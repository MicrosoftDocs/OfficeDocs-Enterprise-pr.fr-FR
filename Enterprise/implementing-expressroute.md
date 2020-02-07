---
title: Implémentation d’ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: ExpressRoute pour Office 365 fournit un autre chemin de routage vers de nombreux services 365 Internet. L’architecture de ExpressRoute pour Office 365 est basée sur des préfixes IP publics publicitaires des services Office 365 déjà accessibles sur Internet dans vos circuits ExpressRoute mis en service pour la redistribution ultérieure de ces préfixes IP dans votre réseau. Avec ExpressRoute, vous activez de manière efficace plusieurs chemins d’accès de routage, via Internet et via ExpressRoute, pour de nombreux services Office 365. Cet état de routage sur votre réseau peut représenter une modification significative de la façon dont la topologie de votre réseau interne est conçue.
ms.openlocfilehash: 63d7c887f9900250a81fe1428d8b5b5cd3df9b81
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840181"
---
# <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

ExpressRoute pour Office 365 fournit un autre chemin de routage vers de nombreux services 365 Internet. L’architecture de ExpressRoute pour Office 365 est basée sur des préfixes IP publics publicitaires des services Office 365 déjà accessibles sur Internet dans vos circuits ExpressRoute mis en service pour la redistribution ultérieure de ces préfixes IP dans votre réseau. Avec ExpressRoute, vous activez de manière efficace plusieurs chemins d’accès de routage, via Internet et via ExpressRoute, pour de nombreux services Office 365. Cet état de routage sur votre réseau peut représenter une modification significative de la façon dont la topologie de votre réseau interne est conçue.
  
 **État :** Guide complet v2
  
Vous devez planifier avec soin votre implémentation de ExpressRoute pour Office 365 afin de prendre en compte les complexités de réseau liées à l’utilisation d’un circuit dédié via un circuit dédié avec des itinéraires injectés dans votre réseau de base et Internet. Si vous et votre équipe n’effectuez pas la planification détaillée et les tests de ce guide, il existe un risque élevé que vous soyez confronté à un risque intermittent ou une perte totale de connectivité aux services Office 365 lorsque le circuit ExpressRoute est activé.
  
Pour réussir l’implémentation, vous devrez analyser vos besoins en matière d’infrastructure, passer par une évaluation et une conception réseau détaillées, planifier soigneusement le déploiement de manière progressive et contrôlée, et créer un plan de validation et de test détaillé. Pour un environnement distribué étendu, il n’est pas rare de voir les implémentations s’étendent sur plusieurs mois. Ce guide est conçu pour vous aider à planifier à l’avance.
  
Les déploiements de grande envergure peuvent durer six mois dans la planification et inclure souvent les membres de l’équipe dans de nombreux domaines de l’organisation, y compris les administrateurs de réseau, de pare-feu et de serveur proxy, les administrateurs Office 365, la sécurité, le support utilisateur final, le projet gestion et parrainage exécutif. Votre investissement dans le processus de planification réduira la probabilité que vous rencontriez des échecs de déploiement résultant d’un temps d’arrêt ou d’un dépannage complexe et onéreux.
  
Les conditions préalables suivantes doivent être remplies avant le démarrage de ce guide de mise en œuvre.
  
1. Vous avez terminé une évaluation réseau pour déterminer si ExpressRoute est recommandé et approuvé.

2. Vous avez sélectionné un fournisseur de services réseau ExpressRoute. Recherchez des détails sur les [partenaires ExpressRoute et les emplacements d’homologation](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Vous avez déjà lu et assimilé la [documentation de ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) et votre réseau interne est capable de répondre aux conditions préalables de ExpressRoute.

4. Votre équipe a lu toutes les instructions et documents publics à l' [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)adresse [https://aka.ms/ert](https://aka.ms/ert), et a surveillé la série de [formation Azure ExpressRoute pour Office 365](https://channel9.msdn.com/series/aer) sur Channel 9 afin de mieux comprendre les détails techniques critiques, notamment :

      - Les dépendances Internet des services SaaS.

      - Comment éviter les itinéraires asymétriques et gérer le routage complexe.

      - Comment incorporer les contrôles de sécurité de périmètre, de disponibilité et de niveau application.

## <a name="begin-by-gathering-requirements"></a>Commencer par collecter les conditions requises
<a name="requirements"> </a>

Commencez par déterminer les fonctionnalités et services que vous prévoyez d’adopter au sein de votre organisation. Vous devez déterminer les fonctionnalités des différents services Office 365 qui seront utilisés et les emplacements de votre réseau qui hébergeront des personnes qui utilisent ces fonctionnalités. Avec le catalogue de scénarios, vous devez ajouter les attributs réseau dont chacun de ces scénarios a besoin ; telles que les flux de trafic réseau entrants et sortants et si les points de terminaison Office 365 sont disponibles sur ExpressRoute ou non.
  
Pour recueillir les exigences de votre organisation :
  
- Cataloguez le trafic réseau entrant et sortant pour les services Office 365 que votre organisation utilise. Consultez les URL et les plages d’adresses IP Office 365 pour obtenir la description des flux requis par différents scénarios Office 365.

- Regroupez la documentation de la topologie réseau existante en affichant les détails de votre topologie et de votre topologie WAN internes, la connectivité des sites satellites, la connectivité des utilisateurs du dernier kilomètre, le routage vers les points de sortie du périmètre réseau et les services proxy.

  - Identifiez les points de terminaison de service entrants dans les diagrammes de réseaux auxquels Office 365 et les autres services Microsoft se connecteront, en affichant à la fois Internet et les chemins de connexion ExpressRoute proposés.

  - Identifiez tous les emplacements d’utilisateur géographique et la connectivité WAN entre les emplacements, ainsi que les emplacements où se trouvent actuellement une sortie sur Internet et quels emplacements sont proposés pour avoir une sortie vers un emplacement d’homologation ExpressRoute.

  - Identifiez tous les périphériques de périmètre, tels que les proxies, les pare-feu, etc., et Cataloguez leurs relations avec les flux de transit sur Internet et ExpressRoute.

  - Indiquez si les utilisateurs finaux peuvent accéder aux services Office 365 via le routage direct ou le proxy d’application indirect pour les flux Internet et ExpressRoute.

- Ajoutez l’emplacement de vos emplacements de client et de réunion à votre diagramme réseau.

- Estimez les caractéristiques de latence et de performances réseau attendues et observées des principaux emplacements utilisateur vers Office 365. N’oubliez pas qu’Office 365 est un ensemble de services globaux et distribués, et que les utilisateurs se connectent à des emplacements qui peuvent être différents de l’emplacement de leur client. Pour cette raison, il est recommandé de mesurer et d’optimiser la latence entre l’utilisateur et le côté le plus proche du réseau global Microsoft sur ExpressRoute et les connexions Internet. Vous pouvez utiliser vos résultats de l’évaluation du réseau pour faciliter cette tâche.

- Répertoriez les exigences en matière de sécurité et de haute disponibilité du réseau d’entreprise qui doivent être remplies avec la nouvelle connexion ExpressRoute. Par exemple, comment les utilisateurs continuent d’accéder à Office 365 en cas de défaillance d’un circuit ExpressRoute ou d’une sortie Internet.

- Documentez les flux réseau Office 365 entrants et sortants qui utiliseront le chemin Internet et qui utilisera ExpressRoute. Les caractéristiques des emplacements géographiques de vos utilisateurs et les détails de votre topologie réseau locale peuvent nécessiter un plan différent d’un emplacement utilisateur à un autre.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Cataloguer votre trafic réseau sortant et entrant
<a name="trafficCatalog"> </a>

Pour minimiser le routage et d’autres complexités de réseau, nous vous recommandons d’utiliser uniquement ExpressRoute pour Office 365 pour les flux de trafic réseau qui sont requis pour passer à une connexion dédiée en raison des exigences réglementaires ou de l’évaluation du réseau. De plus, nous vous recommandons de déployer l’étendue du routage ExpressRoute et d’approcher les flux de trafic réseau entrant et sortant en tant que phases différentes et distinctes du projet d’implémentation. Déployer ExpressRoute pour Office 365 pour les flux de trafic réseau sortants uniquement initiés par l’utilisateur et laisser des flux de trafic réseau entrant sur Internet peut aider à contrôler l’augmentation de la complexité topologique et des risques liés à l’introduction de la fonction asymétrique supplémentaire possibilités de routage.
  
Votre catalogue de trafic réseau doit contenir des listes de toutes les connexions réseau entrantes et sortantes que vous aurez entre votre réseau local et Microsoft.
  
- Les flux de trafic réseau sortants sont des scénarios dans lesquels une connexion est initiée à partir de votre environnement local, par exemple à partir de clients ou de serveurs internes, avec une destination des services Microsoft. Ces connexions peuvent être directement vers Office 365 ou indirect, par exemple lorsque la connexion passe par des serveurs proxy, des pare-feu ou d’autres périphériques réseau sur le chemin d’accès à Office 365.

- Les flux de trafic réseau entrants sont des scénarios dans lesquels une connexion est initiée à partir du Cloud Microsoft vers un hôte local. Ces connexions doivent généralement passer par le pare-feu et d’autres infrastructures de sécurité dont la stratégie de sécurité des clients a besoin pour les flux externes.

Lisez la section « **assurer la symétrie de route** » de l’article [Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) pour déterminer les services qui enverra le trafic entrant et rechercher la colonne marquée **ExpressRoute pour Office 365** dans l’article de référence des [points de terminaison Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) pour déterminer le reste des informations de connectivité.
  
Pour chaque service qui nécessite une connexion sortante, vous devez décrire la connectivité planifiée pour le service, notamment le routage réseau, la configuration du proxy, l’inspection des paquets et les besoins en bande passante.
  
Pour chaque service qui nécessite une connexion entrante, vous aurez besoin d’autres informations. Les serveurs du Cloud Microsoft établiront des connexions à votre réseau local. pour vous assurer que les connexions sont correctement effectuées, vous devez décrire tous les aspects de cette connectivité, y compris ; les entrées DNS publiques pour les services qui accepteront ces connexions entrantes, les adresses IP IPv4 mises en forme CIDR, les équipements de fournisseur de services Internet impliqués et la façon dont le NAT entrant ou le NAT source est géré pour ces connexions.
  
Les connexions entrantes doivent être vérifiées, qu’elles soient connectées via Internet ou ExpressRoute afin de garantir que le routage asymétrique n’a pas été introduit. Dans certains cas, les points de terminaison locaux pour lesquels les services Office 365 initient des connexions entrantes doivent également être accessibles par d’autres services Microsoft et non-Microsoft. Il est primordial que l’activation du routage ExpressRoute vers ces services pour Office 365 ne rompe pas les autres scénarios. Dans de nombreux cas, les clients peuvent avoir besoin d’implémenter des modifications spécifiques sur leur réseau interne, comme une interface NAT source, afin de s’assurer que les flux entrants de Microsoft restent symétriques une fois que ExpressRoute est activé.
  
Voici un exemple du niveau de détail requis. Dans ce cas, Exchange hybride est acheminé vers le système local via ExpressRoute.

|**Connection, propriété**|**Valeur**|
|:-----|:-----|
|**Direction du trafic réseau** <br/> |Entrant  <br/> |
|**Service** <br/> |Environnement Exchange hybride  <br/> |
|**Point de terminaison public Office 365 (source)** <br/> |Exchange Online (adresses IP)  <br/> |
|**Point de terminaison local public (destination)** <br/> |5.5.5.5  <br/> |
|**Entrée DNS publique (Internet)** <br/> |Autodiscover.contoso.com  <br/> |
|**Est-ce que le point de terminaison local sera utilisé par d’autres services Microsoft (autres que Office 365)** <br/> |Non  <br/> |
|**Ce point de terminaison local sera-il utilisé par les utilisateurs/systèmes sur Internet ?** <br/> |Oui  <br/> |
|**Systèmes internes publiés via des points de terminaison publics** <br/> |Rôle d’accès au client Exchange Server (en local) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Publication IP du point de terminaison public** <br/> |**Vers Internet**: 5.5.0.0/16  <br/> **Vers ExpressRoute**: 5.5.5.0/24  <br/> |
|**Contrôles de sécurité/périmètre** <br/> |**Chemin Internet**: DeviceID_002  <br/> **Chemin d’accès ExpressRoute**: DeviceID_003  <br/> |
|**Haute disponibilité** <br/> |Actif/actif sur 2 redondante géographique  <br/> Circuits ExpressRoute-Chicago et Dallas  <br/> |
|**Contrôle de symétrie de chemin** <br/> |**Méthode**: interface NAT source  <br/> **Chemin Internet**: connexions entrantes de l’interface NAT source vers 192.168.5.5  <br/> |**Chemin d’accès ExpressRoute**: connexions NAT source vers 192.168.1.0 (Chicago) et 192.168.2.0 (Dallas)  <br/> |

Voici un exemple de service sortant uniquement :

|**Connection, propriété**|**Valeur**|
|:-----|:-----|
|**Direction du trafic réseau** <br/> |Sortant  <br/> |
|**Service** <br/> |SharePoint Online  <br/> |
|**Point de terminaison local (source)** <br/> |Station de travail utilisateur  <br/> |
|**Point de terminaison public Office 365 (destination)** <br/> |SharePoint Online (adresses IP)  <br/> |
|**Entrée DNS publique (Internet)** <br/> |\*. sharepoint.com (et noms de domaine complets supplémentaires)  <br/> |
|**Références CDN** <br/> |cdn.sharepointonline.com (et noms de domaine complets supplémentaires)-adresses IP gérées par les fournisseurs de CDN)  <br/> |
|**Publicité IP et NAT en cours d’utilisation** <br/> |**Chemin d’accès Internet/NAT source**: 1.1.1.0/24  <br/> **Chemin d’accès ExpressRoute/NAT source**: 1.1.2.0/24 (Chicago) et 1.1.3.0/24 (Dallas)  <br/> |
|**Connectivity, méthode** <br/> |**Internet**: proxy via couche 7 (fichier. PAC)  <br/> **ExpressRoute**: routage direct (sans proxy)  <br/> |
|**Contrôles de sécurité/périmètre** <br/> |**Chemin Internet**: DeviceID_002  <br/> **Chemin d’accès ExpressRoute**: DeviceID_003  <br/> |
|**Haute disponibilité** <br/> |**Chemin Internet**: sortie Internet redondante  <br/> **Chemin d’accès ExpressRoute**: routage de la pomme de terre active/active sur 2 circuits ExpressRoute redondants-Chicago et Dallas  <br/> |
|**Contrôle de symétrie de chemin** <br/> |**Méthode**: interface NAT source pour toutes les connexions  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Conception de la topologie réseau avec connectivité régionale
<a name="topology"> </a>

Une fois que vous comprenez les services et leurs flux de trafic réseau associés, vous pouvez créer un diagramme réseau qui intègre ces nouvelles exigences de connectivité et illustre les modifications que vous allez effectuer pour utiliser ExpressRoute pour Office 365. Votre diagramme doit inclure les éléments suivants :
  
1. Tous les utilisateurs pour lesquels Office 365 et d’autres services seront accessibles à partir de.

2. Tous les points de sortie Internet et ExpressRoute.

3. Tous les périphériques sortants et entrants qui gèrent la connectivité à l’intérieur et à l’extérieur du réseau, y compris les routeurs, les pare-feu, les serveurs de proxy d’application et la détection/prévention des intrusions.

4. Destinations internes pour tout le trafic entrant, telles que les serveurs ADFS internes qui acceptent les connexions à partir des serveurs proxy d’application Web ADFS.

5. Catalogue de tous les sous-réseaux IP qui seront publiés

6. Identifiez chaque emplacement où les personnes accéderont à Office 365 à partir de et répertorient les emplacements de réunion qui seront utilisés pour ExpressRoute.

7. Emplacements et parties de votre topologie de réseau interne, où les préfixes IP Microsoft apprisus depuis ExpressRoute seront acceptés, filtrés et propagés à.

8. La topologie réseau doit illustrer l’emplacement géographique de chaque segment réseau et la façon dont il se connecte au réseau Microsoft via ExpressRoute et/ou Internet.

Le diagramme ci-dessous montre chaque emplacement où des personnes utiliseront Office 365, ainsi que les annonces de routage entrant et sortant vers Office 365.
  
![Réunion géographique régionale ExpressRoute](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Pour le trafic sortant, les utilisateurs accèdent à Office 365 de trois façons :
  
1. Par le biais d’un emplacement de réunion en Amérique du Nord pour les personnes en Californie.

2. Par le biais d’un emplacement de réunion de Hong Kong pour les personnes de Hong Kong.

3. Via Internet au Bangladesh où il y a moins de personnes et aucun circuit ExpressRoute configuré.

![Connexions sortantes pour le diagramme régional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
De même, le trafic réseau entrant en provenance d’Office 365 renvoie l’une des trois façons suivantes :
  
1. Par le biais d’un emplacement de réunion en Amérique du Nord pour les personnes en Californie.

2. Par le biais d’un emplacement de réunion de Hong Kong pour les personnes de Hong Kong.

3. Via Internet au Bangladesh où il y a moins de personnes et aucun circuit ExpressRoute configuré.

![Connexions entrantes pour le diagramme régional](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Déterminer l’emplacement de la réunion moi appropriée

La sélection des emplacements de réunion, qui sont l’emplacement physique où votre circuit ExpressRoute connecte votre réseau au réseau Microsoft, est influencée par les emplacements où les utilisateurs accèderont à Office 365 à partir de. À l’instar d’une offre SaaS, Office 365 ne fonctionne pas sous le modèle régional IaaS ou PaaS de la même manière qu’Azure. Au lieu de cela, Office 365 est un ensemble de services de collaboration distribués, où les utilisateurs peuvent avoir besoin de se connecter à des points de terminaison sur plusieurs centres de contenu et régions, qui ne se trouvent pas nécessairement au même emplacement que le client de l’utilisateur.
  
Cela signifie que vous devez prendre en compte les éléments les plus importants lors de la sélection des emplacements de conférence pour ExpressRoute pour Office 365. La recommandation générale pour la connectivité Office 365 optimale consiste à implémenter le routage, de sorte que les demandes de l’utilisateur pour les services Office 365 soient transmises au réseau Microsoft sur le chemin réseau le plus court, il est également souvent appelé routage « de patate chaude ». Par exemple, si la plupart des utilisateurs d’Office 365 se trouvent à un ou deux emplacements, la sélection des emplacements de réunion qui se trouvent à proximité de l’emplacement de ces utilisateurs crée la conception optimale. Si votre entreprise dispose d’un grand nombre d’utilisateurs dans de nombreuses régions différentes, vous pouvez envisager d’avoir plusieurs circuits ExpressRoute et des emplacements de réunion. Pour certains de vos emplacements d’utilisateur, le chemin le plus court/le plus optimal dans le réseau Microsoft et Office 365, peut ne pas être par le biais de vos points de connexion WAN et ExpressRoute, mais via Internet.
  
Il arrive souvent qu’il existe plusieurs emplacements de réunion qui peuvent être sélectionnés dans une région avec une proximité relative pour vos utilisateurs. Renseignez le tableau suivant pour vous aider à prendre vos décisions.

|**Emplacements planifiés pour les réunions ExpressRoute en Californie et New York**||
|:-----|:-----|
|L’emplacement  <br/> |Nombre de personnes  <br/> |Latence attendue pour le réseau Microsoft sur Internet sortie  <br/> |Latence attendue pour le réseau Microsoft over ExpressRoute  <br/> |
|Los Angeles  <br/> |10 000  <br/> |~ 15ms  <br/> |~ 10 ms (via Silicon Valley)  <br/> |
|Washington DC  <br/> |15 000  <br/> |~ 20 ms  <br/> |~ 10 ms (via New York)  <br/> |
|Comptent  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms (via New York)  <br/> |

Une fois que l’architecture réseau globale affichant la région Office 365, le fournisseur de services réseau ExpressRoute et la quantité de personnes par emplacement ont été développées, elle peut être utilisée pour déterminer si des optimisations peuvent être effectuées. Il peut également afficher des connexions réseau épinglage globales où le trafic est acheminé vers un emplacement distant afin d’obtenir l’emplacement de la réunion. Si un épinglage sur le réseau global est découvert, il doit être résolu avant de poursuivre. Recherchez un autre emplacement de la réunion-moi ou utilisez des points de sortie Internet sélectifs pour éviter le épinglage.
  
Le premier diagramme présente un exemple de client avec deux emplacements physiques en Amérique du Nord. Vous pouvez voir les informations sur les emplacements Office, les emplacements client Office 365 et plusieurs options pour les emplacements de conférence ExpressRoute. Dans cet exemple, le client a sélectionné l’emplacement de la réunion-moi en fonction de deux principes, dans l’ordre indiqué :
  
1. Proximité la plus proche des personnes de leur organisation.

2. Le plus proche à proximité d’un centre de Microsoft où Office 365 est hébergé.

![ExpressRoute de réunion géographique américaine](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
En développant ce concept légèrement, le second diagramme présente un exemple de client multinational revêtu d’informations similaires et de la prise de décision. Ce client dispose d’un petit bureau en Bangladesh avec une petite équipe de dix personnes axées sur la croissance de son empreinte dans la région. Il y a un emplacement de réunion dans Chennai et un centre de contenu Microsoft avec Office 365 hébergé dans Chennai, donc un emplacement de réunion serait logique. Toutefois, pour dix personnes, le coût du circuit supplémentaire est fastidieux. Lorsque vous examinez votre réseau, vous devez déterminer si la latence impliquée dans l’envoi du trafic réseau au sein de votre réseau est plus efficace que la dépense du capital pour acquérir un autre circuit ExpressRoute.
  
En guise d’alternative, les dix personnes du Bangladesh peuvent bénéficier de meilleures performances avec le trafic réseau envoyé sur Internet au réseau Microsoft que celui qu’ils acheminent sur le réseau interne, comme indiqué dans les schémas de présentation et reproduit souscrit.
  
![Connexions sortantes pour le diagramme régional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Création de votre plan d’implémentation ExpressRoute pour Office 365
<a name="implementation"> </a>

Votre plan d’implémentation doit inclure les détails techniques de la configuration de ExpressRoute, ainsi que les détails de la configuration de toutes les autres infrastructures de votre réseau, telles que les suivantes.
  
- Planifier les services fractionnés entre ExpressRoute et Internet.

- Planification de la bande passante, de la sécurité, de la haute disponibilité et du basculement.

- Concevoir le routage des messages entrants et sortants, y compris les optimisations du chemin de routage approprié pour différents emplacements

- Déterminez le degré d’annonce des itinéraires ExpressRoute dans votre réseau et quel est le mécanisme pour les clients pour sélectionner Internet ou ExpressRoute chemin d’accès ; par exemple, routage direct ou proxy d’application.

- Planifier les modifications des enregistrements DNS, y compris les entrées de l’infrastructure de la [stratégie d’expéditeurs](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) .

- Planifier la stratégie NAT, y compris les ports NAT entrants et sortants.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planification de votre routage avec des chemins d’accès réseau Internet et ExpressRoute
<a name="paths"> </a>

- Pour votre déploiement initial, tous les services entrants, tels que le courrier électronique entrant ou la connectivité hybride, sont recommandés pour utiliser Internet.

- Planifier le routage LAN du client final, comme [la configuration d’un fichier PAC/WPAD, un](https://aka.ms/manageo365endpoints)Itinéraire par défaut, des serveurs proxy et des annonces d’itinéraires BGP.

- Planifier le routage du périmètre, y compris les serveurs proxy, les pare-feu et les proxys Cloud.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planification de la bande passante, de la sécurité, de la haute disponibilité et du basculement
<a name="availability"> </a>

Créez une planification de la bande passante requise pour chaque charge de travail Office 365 majeure. Estimez séparément les besoins en bande passante Exchange Online, SharePoint Online et Skype entreprise online. Vous pouvez utiliser les calculatrices d’estimation fournies pour Exchange Online et Skype entreprise comme point de départ ; Toutefois, un test pilote avec un échantillon représentatif des profils utilisateur et des emplacements est nécessaire pour comprendre entièrement les besoins en bande passante de votre organisation.
  
Ajoutez la manière dont la sécurité est gérée sur chaque site Internet et ExpressRoute sortie vers votre plan, rappelez-vous que toutes les connexions ExpressRoute à Office 365 utilisent l’homologation publique et qu’elles doivent toujours être sécurisées conformément aux stratégies de sécurité de votre entreprise liées à la connexion à l’extérieur. réseaux.
  
Ajoutez des détails à votre plan sur les personnes qui seront affectées par le type de panne et la façon dont ces personnes seront en mesure d’effectuer leur travail à pleine capacité de la manière la plus simple.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planifier les besoins en bande passante, notamment les exigences de Skype entreprise en matière de gigue, de latence, de congestion et de marge
  
Skype entreprise online comporte également des exigences spécifiques en matière de réseau, qui sont détaillées dans l’article [Media Quality and Network Connectivity performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Lisez la section **planification de la bande passante pour Azure ExpressRoute** dans la [planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Lorsque vous effectuez une évaluation de la bande passante avec vos utilisateurs pilotes, vous pouvez utiliser notre guide ; [Réglage des performances Office 365 à l’aide de la planification et de l’historique des performances](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planifier les besoins en matière de haute disponibilité
  
Créez un plan de haute disponibilité pour répondre à vos besoins et incorporez-le dans le diagramme de topologie réseau mis à jour. Lisez la section **haute disponibilité et basculement avec Azure ExpressRoute** dans la [planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planification des exigences en matière de sécurité réseau
  
Créez un plan pour répondre aux exigences de sécurité de votre réseau et incorporez-le dans votre diagramme de topologie réseau mis à jour. Lisez la section **application des contrôles de sécurité à Azure ExpressRoute pour les scénarios office 365** dans le cadre de la [planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Concevoir la connectivité du service sortant
<a name="outbound"> </a>

La configuration requise pour le *réseau ExpressRoute* pour Office 365 est inhabituelle. Plus précisément, les adresses IP qui représentent vos utilisateurs et réseaux sur Office 365 et agissent comme les points de terminaison sources pour les connexions réseau sortantes à Microsoft doivent respecter des exigences spécifiques décrites ci-dessous.
  
1. Les points de terminaison doivent être des adresses IP publiques, qui sont enregistrées à votre entreprise ou à un opérateur qui vous fournit une connectivité ExpressRoute.

2. Les points de terminaison doivent être publiés auprès de Microsoft et validés/acceptés par ExpressRoute.

3. Les points de terminaison ne doivent pas être publiés sur Internet avec la même mesure de routage préférée ou plus.

4. Les points de terminaison ne doivent pas être utilisés pour la connectivité aux services Microsoft qui ne sont pas configurés sur ExpressRoute.

Si la conception de votre réseau ne répond pas à ces exigences, les utilisateurs risquent de rencontrer des problèmes de connectivité avec Office 365 et d’autres services Microsoft en raison de l’acheminement des holing noirs ou des itinéraires asymétriques. Cela se produit lorsque les demandes envoyées aux services Microsoft sont acheminées via ExpressRoute, mais les réponses sont routées vers l’arrière sur Internet, et inversement, et les réponses sont abandonnées par des périphériques réseau avec état tels que des pare-feu.
  
La méthode la plus courante que vous pouvez utiliser pour répondre aux exigences ci-dessus consiste à utiliser la traduction d’adresses réseau source, soit implémentée dans le cadre de votre réseau, soit fournie par votre opérateur ExpressRoute. Le NAT source vous permet d’abstraire les détails et l’adressage IP privé de votre réseau Internet à partir de ExpressRoute et de ; associés à des publications d’itinéraires IP correctes, fournissent un mécanisme simple pour garantir la symétrie de chemin. Si vous utilisez des périphériques réseau avec état spécifiques aux emplacements d’homologation ExpressRoute, vous devez implémenter des pools NAT distincts pour chaque homologation ExpressRoute afin de garantir une symétrie de chemin d’accès.
  
Pour en savoir plus sur les [exigences du protocole NAT ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Ajoutez les modifications pour la connectivité sortante au diagramme de la topologie réseau.
  
### <a name="design-inbound-service-connectivity"></a>Concevoir la connectivité du service entrant
<a name="inbound"> </a>

La majorité des déploiements d’entreprise d’Office 365 supposent une forme de connectivité entrante à partir d’Office 365 vers des services locaux, tels que les scénarios hybrides Exchange, SharePoint et Skype entreprise, les migrations de boîtes aux lettres et l’authentification à l’aide d’ADFS architecture. Lorsque ExpressRoute vous activez un chemin de routage supplémentaire entre votre réseau local et Microsoft pour la connectivité sortante, ces connexions entrantes peuvent être affectées par inadvertance par le routage asymétrique, même si vous envisagez de faire en sorte que ces flux continuent à utiliser Internet. Quelques précautions décrites ci-dessous sont recommandées pour s’assurer qu’il n’y a aucun impact sur les flux entrants Internet d’Office 365 vers des systèmes locaux.
  
Pour minimiser les risques de routage asymétrique pour les flux de trafic réseau entrant, toutes les connexions entrantes doivent utiliser la traduction d’adresses réseau source avant de les acheminer vers des segments de votre réseau qui ont une visibilité de routage dans ExpressRoute. Si les connexions entrantes sont autorisées sur un segment réseau avec le routage de la visibilité dans ExpressRoute sans NAT source, les demandes provenant d’Office 365 sont entrées à partir d’Internet, mais la réponse renvoyée à Office 365 préfère le ExpressRoute chemin d’accès réseau au réseau Microsoft, provoquant un routage asymétrique.
  
Vous pouvez envisager l’un des modèles d’implémentation suivants pour répondre à cette exigence :
  
1. Exécutez l’interface NAT source avant que les demandes soient acheminées vers votre réseau interne à l’aide d’équipements de mise en réseau tels que des pare-feu ou des programmes d’équilibrage de charge sur le chemin d’accès à vos systèmes locaux à partir d’Internet.

2. Assurez-vous que les itinéraires ExpressRoute ne sont pas propagés aux segments réseau où les services entrants, tels que les serveurs frontaux ou les systèmes de proxys inverses, gèrent les connexions Internet.

La comptabilisation explicite de ces scénarios dans votre réseau et le maintien de tous les flux de trafic réseau entrant sur Internet contribuent à réduire le déploiement et le risque opérationnel du routage asymétrique.
  
Dans certains cas, vous pouvez choisir de diriger certains flux entrants sur des connexions ExpressRoute. Pour ces scénarios, prenez en compte les considérations supplémentaires suivantes.
  
1. Office 365 peut uniquement cibler des points de terminaison locaux qui utilisent des adresses IP publiques. Cela signifie que même si le point de terminaison entrant local est exposé uniquement à Office 365 sur ExpressRoute, il doit quand même être associé à une adresse IP publique.

2. Toute la résolution de noms DNS que les services Office 365 effectuent pour résoudre les points de terminaison sur site à l’aide de DNS public. Cela signifie que vous devez enregistrer le nom de domaine complet (FQDN) des points de terminaison de service entrants sur Internet.

3. Pour recevoir des connexions réseau entrantes via ExpressRoute, les sous-réseaux IP publics de ces points de terminaison doivent être publiés auprès de Microsoft via ExpressRoute.

4. Évaluez soigneusement ces flux de trafic réseau entrant afin de vous assurer que des contrôles de sécurité et de réseau appropriés sont appliqués conformément aux stratégies de votre entreprise en matière de sécurité et de réseau.

5. Une fois que vos points de terminaison entrants locaux sont annoncés à Microsoft via ExpressRoute, ExpressRoute deviendra le chemin de routage préféré vers ces points de terminaison pour tous les services Microsoft, y compris Office 365. Cela signifie que ces sous-réseaux de point de terminaison doivent uniquement être utilisés pour les communications avec les services Office 365 et aucun autre service sur le réseau Microsoft. Dans le cas contraire, votre conception entraînera un routage asymétrique où les connexions entrantes d’autres services Microsoft préfèrent acheminer les messages entrants sur ExpressRoute, tandis que le chemin de retour utilisera Internet.

6. En cas de panne d’un circuit ExpressRoute ou d’un emplacement de réunion, vous devez vous assurer que les points de terminaison entrants locaux sont toujours disponibles pour accepter les demandes sur un chemin d’accès réseau distinct. Cela peut signifier la publication de sous-réseaux pour ces points de terminaison via plusieurs circuits ExpressRoute.

7. Nous vous recommandons d’appliquer une interface NAT source pour tous les flux de trafic réseau entrants entrant sur votre réseau via ExpressRoute, en particulier lorsque ces flux transitent par des périphériques réseau d’État tels que des pare-feu.

8. Certains services locaux, tels que le proxy ADFS ou la découverte automatique d’Exchange, peuvent recevoir des demandes entrantes provenant des services et des utilisateurs Office 365 à partir d’Internet. Pour ces demandes, Office 365 ciblera le même nom de domaine complet que les demandes utilisateur sur Internet. Autoriser les connexions utilisateur entrantes d’Internet à ces points de terminaison locaux, tout en forçant les connexions Office 365 à utiliser ExpressRoute, représente une complexité de routage significative. Pour la plupart des clients qui implémentent ce type de scénario complexe sur ExpressRoute n’est pas recommandé en raison des considérations opérationnelles. Cette charge supplémentaire inclut, la gestion des risques liés au routage asymétrique et vous oblige à gérer soigneusement les annonces et les stratégies de routage sur plusieurs dimensions.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Mettre à jour votre plan de topologie réseau pour montrer comment éviter les itinéraires asymétriques
<a name="asymmetric"> </a>

Vous souhaitez éviter le routage asymétrique afin de vous assurer que les membres de votre organisation peuvent utiliser Office 365 de façon transparente, ainsi que d’autres services importants sur Internet. Il existe deux configurations courantes que les clients provoquent un routage asymétrique. Maintenant, nous vous recommandons de passer en revue la configuration réseau que vous prévoyez d’utiliser et de vérifier si l’un de ces scénarios de routage asymétrique existe.
  
Pour commencer, nous allons examiner quelques situations différentes associées au diagramme réseau suivant. Dans ce diagramme, tous les serveurs qui reçoivent des demandes entrantes, comme ADFS ou les serveurs hybrides locaux, se trouvent dans le nouveau centre de données Jersey et sont publiés sur Internet.
  
1. Alors que le réseau de périmètre est sécurisé, aucune interface NAT source n’est disponible pour les demandes entrantes.

2. Les serveurs du nouveau centre de données Jersey peuvent voir les itinéraires Internet et ExpressRoute.

![Vue d’ensemble de la connectivité ExpressRoute](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Nous avons également des suggestions sur la façon de les résoudre.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problème 1 : Cloud vers une connexion locale sur Internet
  
Le diagramme suivant illustre le chemin d’accès au réseau asymétrique lorsque votre configuration réseau ne fournit pas NAT pour les demandes entrantes de Microsoft Cloud sur Internet.
  
1. La demande entrante d’Office 365 récupère l’adresse IP du point de terminaison local à partir du DNS public et envoie la demande à votre réseau de périmètre.

2. Dans cette configuration défectueuse, aucun NAT source n’est configuré ou disponible sur le réseau de périmètre où le trafic est envoyé, ce qui entraîne l’utilisation de l’adresse IP source réelle comme destination de retour.

  - Le serveur de votre réseau achemine le trafic de retour vers Office 365 par le biais de n’importe quelle connexion réseau ExpressRoute disponible.

  - Le résultat est un chemin d’accès asymétrique pour ce flux à Office 365, ce qui entraîne une connexion rompue.

![ExpressRoute Asymetric problème de routage 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Solution 1a : interface NAT source
  
En ajoutant simplement une interface NAT source à la demande entrante, vous résolvez ce réseau mal configuré. Dans ce schéma :
  
1. La demande entrante continue de pénétrer dans le réseau de périmètre du nouveau vendeur Jersey. Cette fois source NAT est disponible.

2. La réponse du serveur revient vers l’adresse IP associée à la NAT source au lieu de l’adresse IP d’origine, ce qui entraîne le renvoi du même chemin réseau.

![Solution de routage Asymetric ExpressRoute 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Solution 1b : portée de routage
  
Vous pouvez également choisir de ne pas autoriser la publication des préfixes BGP ExpressRoute, en supprimant le chemin d’accès réseau de substitution pour ces ordinateurs. Dans ce schéma :
  
1. La demande entrante continue de pénétrer dans le réseau de périmètre du nouveau vendeur Jersey. Cette fois, les préfixes publiés par Microsoft sur le circuit ExpressRoute ne sont pas disponibles pour le nouveau centre de données Jersey.

2. La réponse du serveur revient vers l’adresse IP associée à l’adresse IP d’origine sur le seul itinéraire disponible, entraînant la réponse renvoyant le même chemin d’accès réseau.

![Solution de routage ExpressRoute Asymetric 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problème 2 : Cloud vers une connexion locale sur ExpressRoute
  
Le diagramme suivant illustre le chemin d’accès au réseau asymétrique lorsque votre configuration réseau ne fournit pas NAT pour les demandes entrantes de Microsoft Cloud over ExpressRoute.
  
1. La demande entrante d’Office 365 récupère l’adresse IP à partir du DNS et envoie la demande à votre réseau de périmètre.

2. Dans cette configuration défectueuse, aucun NAT source n’est configuré ou disponible sur le réseau de périmètre où le trafic est envoyé, ce qui entraîne l’utilisation de l’adresse IP source réelle comme destination de retour.

  - L’ordinateur de votre réseau achemine le trafic de retour vers Office 365 via une connexion réseau ExpressRoute disponible.

  - Le résultat est une connexion asymétrique à Office 365.

![ExpressRoute Asymetric problème de routage 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Solution 2 : NAT source
  
En ajoutant simplement une interface NAT source à la demande entrante, vous résolvez ce réseau mal configuré. Dans ce schéma :
  
1. La demande entrante continue de pénétrer dans le réseau de périmètre du centre de données de New York. Cette fois source NAT est disponible.

2. La réponse du serveur revient vers l’adresse IP associée à la NAT source au lieu de l’adresse IP d’origine, ce qui entraîne le renvoi du même chemin réseau.

![Solution de routage ExpressRoute Asymetric 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Document vérifier que la conception du réseau comporte une symétrie de chemin

À ce stade, vous devez vérifier sur papier que votre plan de mise en œuvre offre une symétrie de route pour les différents scénarios dans lesquels vous utiliserez Office 365. Vous identifierez l’itinéraire réseau spécifique qui doit être exécuté lorsqu’une personne utilise différentes fonctionnalités du service. Depuis le réseau local et le routage WAN, vers les périphériques de périmètre, vers le chemin de connectivité ; ExpressRoute ou Internet, et sur la connexion au point de terminaison en ligne.
  
Vous devez effectuer cette opération pour tous les services réseau Office 365 qui ont été précédemment identifiés comme des services que votre organisation adoptera.
  
Il vous aide à effectuer ce parcours papier via les routes avec une deuxième personne. Expliquez-leur où chaque saut réseau est attendu pour obtenir son itinéraire suivant et assurez-vous que vous êtes familiarisé avec les chemins de routage. N’oubliez pas que ExpressRoute fournira toujours un itinéraire plus étendu aux adresses IP de serveur Microsoft, ce qui lui donne un coût de routage inférieur à celui d’un itinéraire Internet par défaut.
  
### <a name="design-client-connectivity-configuration"></a>Conception de la configuration de la connectivité client
<a name="asymmetric"> </a>

![Utilisation de fichiers PAC avec ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Si vous utilisez un serveur proxy pour le trafic lié à Internet, vous devez ajuster les fichiers de configuration de l’PAC ou du client pour vous assurer que les ordinateurs clients de votre réseau sont correctement configurés pour envoyer le trafic ExpressRoute que vous souhaitez vers Office 365 sans transit votre serveur proxy, ainsi que le reste du trafic, y compris le trafic Office 365, sont envoyés au proxy approprié. Lisez notre guide sur la [gestion des points de terminaison Office 365](https://aka.ms/manageo365endpoints) pour obtenir des exemples de fichiers PAC.
  
> [!NOTE]
> Les points de terminaison changent fréquemment, aussi souvent qu’une fois par semaine. Vous devez uniquement effectuer des modifications en fonction des services et des fonctionnalités adoptés par votre organisation pour réduire le nombre de modifications à effectuer pour rester à jour. Soyez très attentif à la **Date d’effet** dans le flux RSS où les modifications sont annoncées et un enregistrement est conservé de toutes les modifications antérieures, les adresses IP annoncées peuvent ne pas être annoncées ou supprimées de la publication, jusqu’à ce que la date d’effet soit atteinte.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Créer vos procédures de déploiement et de test
<a name="testing"> </a>

Votre plan d’implémentation doit inclure les tests et la planification de la restauration. Si votre implémentation ne fonctionne pas comme prévu, le plan doit être conçu pour affecter le moins de personnes avant la découverte des problèmes. Voici quelques principes de haut niveau que votre plan doit prendre en compte.
  
1. Préparez le segment réseau et l’intégration du service d’utilisateurs pour minimiser les interruptions.

2. Planifiez les tests d’itinéraires avec traceroute et TCP Connect à partir d’un hôte connecté à Internet distinct.

3. De préférence, le test des services entrants et sortants doit être réalisé sur un réseau de test isolé avec un client Office 365 de test.

      - En guise d’alternative, le test peut être effectué sur un réseau de production si le client n’utilise pas encore Office 365 ou s’il est en phase pilote.

      - En guise d’alternative, le test peut être effectué pendant une panne de production qui est réservée uniquement à des fins de test et de surveillance.

      - En guise d’alternative, le test peut être réalisé en vérifiant les itinéraires de chaque service sur chaque nœud de routeur de couche 3. Cette inversion doit être utilisée uniquement si aucun autre test n’est possible, étant donné qu’un manque de tests physiques introduit un risque.

### <a name="build-your-deployment-procedures"></a>Créer vos procédures de déploiement

Vos procédures de déploiement doivent être déployées sur de petits groupes de personnes par étapes pour permettre le test avant le déploiement vers des groupes plus importants de personnes. Vous trouverez ci-dessous plusieurs façons de déployer le déploiement de ExpressRoute.
  
1. Configurer ExpressRoute avec l’homologation Microsoft et faire en sorte que les annonces d’itinéraires soient transmises à un seul hôte uniquement à des fins de test intermédiaire.

2. Publiez les itinéraires vers le réseau ExpressRoute vers un seul segment réseau, puis développez les annonces d’itinéraires par segment réseau ou région.

3. Si vous déployez Office 365 pour la première fois, utilisez le déploiement réseau ExpressRoute en tant que pilote pour un petit nombre de personnes.

4. Si vous utilisez des serveurs proxy, vous pouvez également configurer un fichier PAC de test pour diriger un petit nombre de personnes vers ExpressRoute avec des tests et des commentaires avant d’en ajouter.

Votre plan d’implémentation doit répertorier chacune des procédures de déploiement qui doivent être prises ou des commandes qui doivent être utilisées pour déployer la configuration réseau. Lorsque le temps d’indisponibilité du réseau arrive, toutes les modifications apportées doivent provenir du plan de déploiement écrit qui a été écrit à l’avance et de l’homologue. Consultez nos conseils sur la configuration technique de ExpressRoute.
  
- Mise à jour de vos enregistrements TXT SPF si vous avez modifié des adresses IP pour des serveurs locaux qui continueront à envoyer des courriers électroniques.

- Mise à jour de toutes les entrées DNS pour les serveurs locaux si vous avez modifié les adresses IP afin de prendre en compte une nouvelle configuration NAT.

- Assurez-vous d’avoir souscrit au flux RSS pour les notifications de points de terminaison 365 Office afin de maintenir les configurations de routage ou de proxy.

Une fois votre déploiement ExpressRoute terminé, les procédures du plan de test doivent être exécutées. Les résultats pour chaque procédure doivent être consignés. Vous devez inclure les procédures de restauration de l’environnement de production d’origine dans le cas où les résultats du plan de test indiquent que l’implémentation a échoué.
  
### <a name="build-your-test-procedures"></a>Créer vos procédures de test

Vos procédures de test doivent inclure des tests pour chaque service réseau entrant et sortant pour Office 365 qui utiliseront ExpressRoute et ceux qui ne le seront pas. Les procédures doivent inclure des tests à partir de chaque emplacement réseau unique, y compris les utilisateurs qui ne sont pas en local dans le réseau local d’entreprise.
  
Voici quelques exemples d’activités de test :
  
1. Effectuez un test ping à partir de votre routeur local vers votre routeur d’opérateur réseau.

2. Valider les 500 + annonces d’adresses IP 365 et CRM Online reçues par votre routeur local.

3. Valider votre interface NAT entrante et sortante fonctionne entre ExpressRoute et le réseau interne.

4. Vérifiez que les itinéraires vers votre NAT sont publiés à partir de votre routeur.

5. Vérifiez que ExpressRoute a accepté vos préfixes publiés.

      - Utilisez l’applet de commande suivante pour vérifier les publicités d’homologation :

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. La validation de votre plage IP NAT publique n’est pas annoncée à Microsoft via un autre circuit de réseau Internet public ou ExpressRoute, sauf s’il s’agit d’un sous-ensemble spécifique d’une plage plus importante comme dans l’exemple précédent.

7. Les circuits ExpressRoute sont couplés, vérifiez que les deux sessions BGP sont en cours d’exécution.

8. Configurez un seul hôte à l’intérieur de votre NAT et utilisez les commandes ping, tracert et tcpping pour tester la connectivité entre le nouveau circuit et l’hôte outlook.office365.com. Vous pouvez également utiliser un outil tel que Wireshark ou Microsoft Network Monitor 3,4 sur un port en miroir vers le MSEE pour vous assurer que vous pouvez vous connecter à l’adresse IP associée à outlook.office365.com.

9. Testez la fonctionnalité au niveau de l’application pour Exchange Online.

  - Test Outlook est capable de se connecter à Exchange Online et d’envoyer/recevoir des courriers électroniques.

  - Test Outlook est en mesure d’utiliser le mode en ligne.

  - Fonctionnalité de connectivité smartphone de test et d’envoi/réception.

10. Fonctionnalités d’application de test pour SharePoint Online

  - Testez le client de synchronisation OneDrive entreprise.

  - Testez SharePoint Online Web Access.

11. Testez la fonctionnalité au niveau de l’application pour les scénarios d’appel Skype entreprise :

  - Rejoindre l’appel de téléconférence en tant qu’utilisateur authentifié [invitation initiée par l’utilisateur final].

  - Inviter l’utilisateur à appeler une téléconférence [invite envoyée depuis le MCU].

  - Joignez une conférence en tant qu’utilisateur anonyme à l’aide de l’application Web Skype entreprise.

  - Joindre l’appel à partir de votre connexion à un ordinateur câblé, un téléphone IP et un appareil mobile.

  - Appel à l’utilisateur fédéré o appel à la validation PSTN : l’appel est terminé, la qualité de l’appel est acceptable, le temps de connexion est acceptable.

  - Vérifier l’état de présence des contacts est mis à jour pour les deux membres du client et des utilisateurs fédérés.

### <a name="common-problems"></a>Problèmes courants

Le routage asymétrique est le problème d’implémentation le plus courant. Voici quelques sources courantes à Rechercher :
  
- Utilisation d’une topologie de routage réseau ouverte ou plate sans NAT source.

- N’utilisant pas SNAT pour acheminer les services entrants via Internet et les connexions ExpressRoute.

- Ne pas tester les services entrants sur ExpressRoute sur un réseau de test avant de procéder au déploiement.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Déploiement de la connectivité ExpressRoute via votre réseau
<a name="testing"> </a>

Déployez votre déploiement sur un segment du réseau à la fois, en déployant progressivement la connectivité vers différentes parties du réseau avec un plan de restauration pour chaque nouveau segment réseau. Si votre déploiement est aligné sur un déploiement d’Office 365, déployez d’abord sur vos utilisateurs du pilote Office 365 et étendez-le à partir de là.
  
Tout d’abord pour votre test, puis pour la production :
  
- Exécutez les étapes de déploiement pour activer ExpressRoute.

- Testez l’affichage des itinéraires réseau comme prévu.

- Effectuez des tests sur chaque service entrant et sortant.

- Rollback si vous découvrez des problèmes.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurer une connexion de test à ExpressRoute avec un segment de réseau de test

Maintenant que vous avez terminé le plan sur papier, il est temps de tester à une petite taille. Dans ce test, vous allez établir une connexion ExpressRoute unique avec l’homologation Microsoft à un sous-réseau de test sur votre réseau local. Vous pouvez configurer un [client d’évaluation Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) avec une connectivité vers et depuis le sous-réseau de test et inclure tous les services entrants et sortants que vous utiliserez en production dans le sous-réseau de test. Configurez le DNS pour le segment de réseau de test et établissez tous les services entrants et sortants. Exécutez votre plan de test et assurez-vous que vous êtes familiarisé avec le routage de chaque service et la propagation de l’itinéraire.
  
### <a name="execute-the-deployment-and-test-plans"></a>Exécuter les plans de déploiement et de test

Lorsque vous avez terminé les éléments décrits ci-dessus, cochez les zones que vous avez terminées et assurez-vous et que votre équipe les a révisées avant d’exécuter vos plans de déploiement et de test.
  
- Liste des services entrants et sortants impliqués dans le changement de réseau.

- Diagramme d’architecture de réseau global montrant à la fois des emplacements de réunion et de conférence ExpressRoute Internet.

- Diagramme de routage réseau illustrant les différents chemins d’accès réseau utilisés pour chaque service déployé.

- Un plan de déploiement avec des étapes pour implémenter les modifications et la restauration si nécessaire.

- Un plan de test pour tester chaque Office 365 et service réseau.

- Validation du papier terminée pour les itinéraires de production pour les services entrants et sortants.

- Test terminé sur un segment de réseau de test, y compris des tests de disponibilité.

Choisissez une fenêtre de panne suffisamment longue pour être exécutée dans l’ensemble du plan de déploiement et du plan de test, dont le temps est disponible pour le dépannage et le temps de restauration, si nécessaire.
  
> [!CAUTION]
> En raison de la nature complexe du routage sur Internet et ExpressRoute, il est recommandé d’ajouter du temps de mémoire tampon supplémentaire à cette fenêtre afin de gérer la résolution des problèmes de routage complexe.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configuration de la qualité de service pour Skype entreprise Online

QoS est nécessaire pour obtenir des avantages vocaux et de réunion pour Skype entreprise online. Vous pouvez configurer QoS une fois que vous avez vérifié que la connexion réseau ExpressRoute ne bloque aucun de vos autres accès au service Office 365. La configuration de QoS est décrite dans l’article [ExpressRoute and QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>Dépannage de votre implémentation
<a name="troubleshooting"> </a>

Le premier emplacement à consulter concerne les étapes de ce guide de mise en œuvre qui ont été manquées dans votre plan d’implémentation ? Revenez en arrière et exécutez des tests de réseau de petite taille, si possible pour répliquer l’erreur et la déboguer.
  
Identifier les services entrants ou sortants qui ont échoué pendant le test. Obtenir spécifiquement les adresses IP et les sous-réseaux pour chacun des services qui ont échoué. Parcourez le diagramme de topologie réseau sur papier et validez le routage. Vérifier spécifiquement où le routage ExpressRoute est annoncé, tester ce routage pendant la panne, si possible avec des traces.
  
Exécutez PSPing avec un suivi réseau pour chaque point de terminaison client et évaluez les adresses IP source et de destination afin de vérifier qu’elles sont conformes aux attentes. Exécutez telnet sur un hôte de messagerie que vous exposez sur le port 25 et vérifiez que SNAT masque l’adresse IP source d’origine si cela est attendu.
  
N’oubliez pas que lors du déploiement d’Office 365 avec une connexion ExpressRoute, vous devez vous assurer que la configuration réseau pour ExpressRoute est optimale et que vous avez également optimisé les autres composants de votre réseau, tels que les ordinateurs clients. En plus de l’utilisation de ce guide de planification pour résoudre les étapes que vous avez peut-être manquées, nous avons également écrit un [plan de résolution des problèmes de performances pour Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365 (aperçu)](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flux d’appels à l’aide de ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
