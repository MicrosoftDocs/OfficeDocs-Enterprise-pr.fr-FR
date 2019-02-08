---
title: Planification de réseau avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute pour Office 365 offre une connectivité de couche 3 entre le réseau et les centres de données de Microsoft. Les circuits utilisent les annonces de routage protocole BGP (Border Gateway) de serveurs frontaux d’Office 365. Du point de vue de vos périphériques locales, lorsqu’ils souhaitent sélectionnez le chemin d’accès correct du TCP/IP vers Office 365, ExpressRoute Azure est considérée comme une alternative à Internet.
ms.openlocfilehash: 7a2c9cb8ee562c0527416aa83184de90cd204476
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897227"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planification de réseau avec ExpressRoute pour Office 365

ExpressRoute pour Office 365 offre une connectivité de couche 3 entre le réseau et les centres de données de Microsoft. Les circuits utilisent les annonces de routage protocole BGP (Border Gateway) de serveurs frontaux d’Office 365. Du point de vue de vos périphériques locales, lorsqu’ils souhaitent sélectionnez le chemin d’accès correct du TCP/IP vers Office 365, ExpressRoute Azure est considérée comme une alternative à Internet.
  
Azure ExpressRoute ajoute un chemin d’accès direct à un ensemble spécifique de fonctionnalités prises en charge et services qui sont offerts par les serveurs au sein de centres de données de Microsoft Office 365. ExpressRoute Azure ne remplace pas la connectivité Internet pour les centres de données Microsoft ou base services Internet tels que de la résolution de nom de domaine. ExpressRoute Azure et vos circuits Internet doivent être sécurisée et redondantes.
  
Le tableau suivant présente quelques différences entre internet et les connexions ExpressRoute Azure dans le cadre d’Office 365.

|**Différences dans la planification du réseau**|**Connexion réseau à Internet**|**Connexion de réseau ExpressRoute**|
|:-----|:-----|:-----|
| Accès aux services internet requis, y compris ;  <br/>  Résolution de noms DNS  <br/>  Vérification de révocation de certificats  <br/>  Réseaux de distribution de contenu  <br/> |Oui  <br/> |La propriété infrastructure DNS et/ou CDN peut-être utiliser le réseau de ExpressRoute demandes à Microsoft.  <br/> |
| Accès aux services Office 365, y compris ;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Entreprise Online  <br/>  Office Online  <br/>  L’authentification et le portail office 365  <br/> |Oui, toutes les applications et fonctionnalités  <br/> |Oui, [applications et fonctionnalités spécifiques](https://aka.ms/o365endpoints) <br/> |
|Sécurité au niveau du périmètre sur site.  <br/> |Oui  <br/> |Non  <br/> |
|Planification de la haute disponibilité.  <br/> |Basculement vers une autre connexion réseau  <br/> |Basculement vers une autre connexion ExpressRoute  <br/> |
|Connexion directe avec un profil de réseau prévisible.  <br/> |Non  <br/> |Oui  <br/> |
|Connectivité IPv6.  <br/> |Oui  <br/> |Non  <br/> |

Développez les titres ci-dessous pour plus d’instructions de planification du réseau. Que nous avons également enregistrées une série de [ExpressRoute Azure pour Office 365 formation](https://channel9.msdn.com/series/aer) 10 parties qui ouvre plus approfondie.

## <a name="existing-azure-expressroute-customers"></a>Clients existants ExpressRoute Azure

Si vous utilisez un circuit ExpressRoute Azure existant et que vous souhaitez ajouter une connectivité Office 365 sur ce circuit, vous devez examiner le nombre de circuits, les emplacements de sortie et la taille des circuits pour s’assurer qu’ils vous répondre aux besoins de votre utilisation d’Office 365. La plupart des clients requièrent plus de bande passante et la plupart nécessitent des circuits supplémentaires.
  
Pour activer l’accès à Office 365 sur votre circuits ExpressRoute Azure existantes, [Configurez les filtres d’itinéraire](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) pour vérifier les services Office 365 sont accessibles.
  
L’abonnement Azure ExpressRoute est axée sur, abonnements sens sont liés aux clients le client. En tant que client, vous pouvez avoir plusieurs circuits ExpressRoute Azure et pourrez accéder aux nombreuses ressources de cloud Microsoft sur ces circuits. Par exemple, vous pouvez choisir d’accéder un Azure hébergée par un client de test d’Office 365, l’ordinateur virtuel et un client de production Office 365 sur une paire de circuits ExpressRoute Azure redondants.
  
Ce tableau présente les deux types de relations homologation, que vous pouvez choisir d’implémenter sur votre circuits.

|**Relation d’homologation**|**Private Azure**|**Microsoft**|
|:-----|:-----|:-----|
|**Services** <br/> |IaaS : Machines virtuelles Azure  <br/> |PaaS : Les services publics Azure  <br/> SaaS : Office 365  <br/> SaaS : Dynamics 365  <br/> |
|Connexion initiation *** <br/> |Client-Microsoft  <br/> Client Microsoft  <br/> |Client-Microsoft  <br/> Client Microsoft  <br/> |
|**Prise en charge de QoS** <br/> |Aucun QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS prend en charge Skype pour les entreprises uniquement à ce stade.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Bande passante de la planification des ExpressRoute Azure

Chaque client Office 365 a des besoins en bande passante unique en fonction du nombre de personnes à chaque emplacement, ils sont comment active avec chaque application Office 365 et d’autres facteurs, tels que l’utilisation de locaux ou équipement hybride et configurations de sécurité réseau.
  
Avoir trop peu de bande passante entraînera la congestion, de retransmissions de données et les retards imprévisibles. Ayant une bande passante élevée entraînera des coûts inutiles. Sur un réseau existant, la bande passante est souvent qualifiée en termes de la quantité d’espace disponible sur le circuit sous forme de pourcentage. Marge de 10 % est susceptible de provoquer de congestion et ayant une capacité suffisante 80 % généralement signifie que les coûts inutiles. Allocations de cibles de marge standard sont 20 à 50 %.
  
Pour rechercher le niveau de bande passante, la meilleure solution consiste à tester la consommation de votre réseau existant. Il s’agit de la seule façon d’obtenir une mesure de l’utilisation de la valeur true et besoin en tant que toutes les configurations réseau et les applications sont dans une certaine mesure unique. Lorsque vous mesure souhaiterez attentivement la consommation de bande passante totale, la latence et la congestion TCP de comprendre votre réseau a besoin.
  
Une fois vous avez une base estimée qui inclut toutes les applications de réseau, pilote Office 365 avec un petit groupe qui comprend les différents profils de personnes dans votre organisation afin de déterminer l’utilisation réelle, et utilisez les deux mesures pour estimer la quantité de bande passante que vous aurez besoin pour chaque emplacement de bureau. S’il existe des problèmes de congestion de TCP trouvés dans vos tests ou la latence, vous devrez peut-être rapprocher la sortie pour les personnes à l’aide d’Office 365 ou le supprimer monopolisent réseau analyse telles que l’inspection/déchiffrement SSL.
  
Tous nos recommandations sur le type de traitement de réseau est recommandé s’applique aux circuits ExpressRoute et Internet. Cela vaut également pour le reste de l’aide sur notre [site réglage des performances](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Application des contrôles de sécurité à ExpressRoute Azure pour les scénarios d’Office 365

Sécurisation de connectivité Azure ExpressRoute commence par les mêmes principes que la sécurisation de la connectivité Internet. De nombreux clients choisissent de déployer des contrôles de réseau et de périmètre sur le chemin d’accès ExpressRoute connexion leur réseau local vers Office 365 et autres nuages de Microsoft. Ces contrôles peuvent inclure pare-feu, proxys d’application, protection contre la perte de données, la détection d’intrusion, prévention des intrusions et ainsi de suite. Dans de nombreux cas, les clients s’appliquent différents niveaux de contrôles au trafic émanant de locaux accédant à Microsoft, et le trafic émanant de Microsoft sur le point d’un réseau local du client, et le trafic émanant de localement sur le point d’un grand Destination Internet.
  
Voici quelques exemples de l’intégration de sécurité avec le [modèle de connectivité de ExpressRoute](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) vous choisissez de déployer.

|**Option d’intégration ExpressRoute**|**Modèle de périmètre de sécurité réseau**|
|:-----|:-----|
|Colocation sur un échange cloud  <br/> |Installation de nouveaux ou d’exploiter l’infrastructure de sécurité/périmètre existante dans l’installation de l’emplacement partagé où est établie la connexion ExpressRoute.  <br/> Exploitez colocalisation permettant de purement à des fins de routage/interconnect et les connexions de trajet arrière à partir de la solution proposée par un emplacement partagé à l’infrastructure de sécurité/périmètre sur site.  <br/> |
|Ethernet point à point  <br/> |Mettre fin à la connexion point à point ExpressRoute à l’emplacement de l’infrastructure/périmètre de sécurité local existant.  <br/> Installer la nouvelle infrastructure/périmètre de sécurité spécifique pour le chemin d’accès ExpressRoute et mettre fin à la connexion point à point il.  <br/> |
|Pour tout IPVPN  <br/> |Exploiter une infrastructure de sécurité/périmètre sur site existante à tous les emplacements de sortie dans la IPVPN utilisé pour ExpressRoute pour la connectivité d’Office 365.  <br/> « Hairpin » le IPVPN utilisé pour ExpressRoute pour Office 365 pour les emplacements spécifiques sur site désigné comme le périmètre de sécurité /.  <br/> |

Certains fournisseurs de services offrent également des fonctionnalités de sécurité/périmètre gérées dans le cadre de leurs solutions de l’intégration avec Azure ExpressRoute.
  
Lorsque vous envisagez l’emplacement de la topologie des options/sécurité réseau périmètre utilisé pour ExpressRoute pour les connexions d’Office 365, Voici des considérations supplémentaires
  
- Les contrôles de sécurité/réseau profondeur et type peuvent avoir d’impact sur les performances et l’évolutivité de l’expérience utilisateur Office 365.

- Sortante (sur-site -\>Microsoft) et entrant (Microsoft -\>locale) [si activé] flux peuvent avoir des besoins différents. Il s’agit probablement différente de celle sortant vers les destinations Internet générales.

- Exigences relatives à Office 365 pour les ports, protocoles et les sous-réseaux IP nécessaires sont les mêmes si le trafic est routé via ExpressRoute pour Office 365 ou via Internet.

- Topologie placement des contrôles de sécurité/réseau client détermine le réseau de bout en bout intégrale entre l’utilisateur et le service Office 365 et peut avoir un impact important sur la latence du réseau et de congestion.

- Les clients sont invités à leur topologie/périmètre de sécurité pour une utilisation avec ExpressRoute de conception pour Office 365 conformément aux meilleures pratiques pour la redondance, haute disponibilité et la récupération d’urgence.

Voici un exemple de la Woodgrove Bank qui compare les différentes options de connectivité Azure ExpressRoute avec les modèles de sécurité de périmètre décrits ci-dessus.
  
### <a name="example-1-securing-azure-expressroute"></a>L’exemple 1 : Sécurisation ExpressRoute Azure
  
Woodgrove Bank envisage d’implémenter ExpressRoute Azure et après la planification de l’architecture optimale pour le [routage avec ExpressRoute pour Office 365](routing-with-expressroute.md) et en suivant les instructions ci-dessus pour comprendre les besoins en bande passante, ils sont détermination de la meilleure méthode pour sécuriser son périmètre.
  
Pour Woodgrove, une organisation internationale avec des emplacements dans plusieurs continents, sécurité doit couvrir tous les périmètres. L’option de connectivité optimale pour Woodgrove est une connexion multipoint comportant plusieurs emplacements homologation dans le monde pour répondre aux besoins de leurs employés dans chaque continent. Chaque continent inclut redondants circuits ExpressRoute Azure dans le continent et sécurité doit couvrir tous ces éléments.
  
Infrastructure de la Woodgrove Bank est fiable et peut gérer le travail supplémentaire, par conséquent, Woodgrove Bank est en mesure d’utiliser l’infrastructure pour la sécurité de périmètre ExpressRoute Azure et internet. Si ce n’était pas le cas, Woodgrove peut choisir d’acheter un équipement supplémentaire pour compléter leur équipement existant ou pour gérer un autre type de connexion.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Haute disponibilité et basculement avec Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Nous vous recommandons d’au moins deux circuits actif chaque sortant avec ExpressRoute à votre fournisseur de ExpressRoute de mise en service. Il s’agit là que nous voir échecs pour les clients et vous pouvez facilement l’éviter par la mise en service une paire de circuits de ExpressRoute actif/actif. Il est également recommandé d’au moins deux circuits d’Internet actif/actif, car de nombreux services Office 365 sont uniquement disponibles sur Internet.
  
À l’intérieur du point de sortie de votre réseau sont d’autres appareils et circuits qui jouent un rôle essentiel dans la façon dont les personnes perçoivent disponibilité. Ces parties de vos scénarios de connectivité ne sont pas couvertes par ExpressRoute ou Office 365 SLA, mais ils jouent un rôle essentiel dans la disponibilité du service de bout en bout en tant que perçues par des personnes dans votre organisation.
  
Se concentrer sur les personnes qui utilisent et utilisation d’Office 365, si une défaillance d’un un composant risque d’affecter des personnes expérience à l’aide du service, recherchez les moyens de limiter le pourcentage total de personnes affectées. Si un mode de basculement est complexité opérationnelle, prendre en compte l’expérience du soulez de beaucoup de temps de récupération et recherchez les modes de basculement requises simple et automatisée.
  
En dehors de votre réseau, Office 365, ExpressRoute et votre fournisseur ExpressRoute tous ont différents niveaux de disponibilité.
  
### <a name="service-availability"></a>Disponibilité du service
  
- Services Office 365 sont couverts par des [contrats de niveau de service](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)bien définie, qui incluent des mesures de temps de fonctionnement et de disponibilité pour les services individuels. L’une des raisons Qu'office 365 peut maintenir ces niveaux de service haute disponibilité est la capacité des composants individuels en toute transparence le basculement entre les nombreux Microsoft centres de données, en utilisant le réseau Microsoft global. Ce basculement étend à partir du centre de données et le réseau sur les points de sortie Internet plusieurs et permet le basculement en toute transparence à partir du point de vue des personnes à l’aide du service.

- ExpressRoute [fournit un SLA de disponibilité de 99,9 %](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) sur des circuits dédiés individuels entre le bord de réseau Microsoft et de l’infrastructure de fournisseur ou partenaire ExpressRoute. Ces niveaux de service est appliquées au niveau des circuits ExpressRoute, qui se compose [deux indépendant relie](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) entre l’équipement Microsoft redondant et le matériel de fournisseur de réseau dans chaque emplacement homologation.

### <a name="provider-availability"></a>Disponibilité du fournisseur
  
- Les accords de niveau de services de Microsoft s’arrête à votre fournisseur de ExpressRoute ou d’un partenaire. C’est également la première chose que vous pouvez effectuer les choix qui influence votre niveau de disponibilité. Vous devez mieux évaluer l’architecture, la disponibilité et votre fournisseur ExpressRoute offre des caractéristiques de résistance entre votre réseau de périmètre et votre connexion de fournisseurs à chaque emplacement homologation Microsoft. Attentif aux aspects physiques et logiques de redondance, équipement homologation, circuits WAN opérateur fourni, et n’importe quelle valeur supplémentaire ajouter des services tels que les services de traduction d’adresses réseau ou les pare-feu gérés.

### <a name="designing-your-availability-plan"></a>Conception de votre plan de disponibilité
  
Nous recommandons vivement de planifier et concevoir une haute disponibilité et résilience dans vos scénarios de connectivité de bout en bout pour Office 365. Une conception doit inclure ;
  
- Aucun point de défaillance, y compris les circuits Internet et ExpressRoute unique.

- en réduisant le nombre de personnes affectées et la durée de cet impact pour les modes de défaillance plus attendues.

- optimisation des processus de récupération simple, reproductible et automatique à partir des modes de défaillance plus attendues.

- prise en charge les demandes de vos le trafic réseau par le biais des chemins d’accès redondants, sans dégradation substantielle complètes.

Les scénarios de connectivité doivent inclure une topologie de réseau qui est optimisée pour plusieurs chemins d’accès réseau indépendant et active vers Office 365. Cela produira une disponibilité de bout en bout mieux à une topologie optimisé uniquement pour la redondance au niveau de chaque périphérique ou d’équipement.
  
> [!TIP]
> Si vos utilisateurs sont répartis sur plusieurs continents ou des zones géographiques et chacun de ces emplacements se connecte via redondants circuits WAN à un emplacement unique local où se trouve un seul circuit ExpressRoute, vos utilisateurs subiront inférieur disponibilité du service de bout en bout à une conception de topologie réseau qui inclut des circuits ExpressRoute indépendants qui se connectent les différentes régions pour le plus proche peering emplacement.
  
Nous vous recommandons d’au moins deux circuits ExpressRoute avec chaque connexion de circuit à un autre emplacement homologation géographique de mise en service. Mettre en service cette paire active / active de circuits pour chaque région où personnes utiliseront ExpressRoute connectivité pour les services Office 365. Cela permet à chaque région reste connecté lors d’un sinistre qui affecte un emplacement comme un centre de données principal ou homologation. Le trafic des utilisateurs à être réparti dans plusieurs chemins d’accès réseau permet de les configurer dans actif/actif. Cela permet de réduire l’étendue des personnes affectées au cours des pannes de matériel réseau ou de périphérique.
  
N’est pas recommandée à l’aide d’un seul circuit ExpressRoute avec Internet en tant que sauvegarde.
  
### <a name="example-2-failover-and-high-availability"></a>L’exemple 2 : Haute disponibilité et basculement
  
Conception de multiples géographique de Woodgrove Bank a subi un examen de routage, la bande passante, la sécurité et maintenant doit passer par un examen de la haute disponibilité. Woodgrove pense à haute disponibilité comme couvrant trois catégories ; résistance, la fiabilité et la redondance.
  
Résistance permet Woodgrove récupérer rapidement à des défaillances. Fiabilité permet Woodgrove offrir un résultat cohérent au sein du système. La redondance permet de Woodgrove un déplacement entre une ou plusieurs instances de mise en miroir de l’infrastructure.
  
Dans chaque configuration de périphérie, Woodgrove a redondants, proxys et les pare-feu ID. Amérique du Nord, Woodgrove a une configuration de périphérie dans leur centre de données Dallas et une autre configuration du serveur edge dans leur centre de données Virgin. L’équipement redondant à chaque emplacement offre résistance à cet emplacement.
  
La configuration réseau Woodgrove Bank s’appuie sur quelques principes clés suivants :
  
- Dans chaque région géographique, il existe plusieurs circuits ExpressRoute Azure.

- Chaque circuit au sein d’une région peut prendre en charge tout le trafic réseau au sein de cette région.

- Routage sera clairement préfèrent une ou l’autre chemin en fonction de la disponibilité, l’emplacement et ainsi de suite.

- Basculement entre des circuits ExpressRoute Azure se produit automatiquement sans configuration supplémentaire ou action requise par Woodgrove.

- Basculement entre des circuits Internet se produit automatiquement sans configuration supplémentaire ou action requise par Woodgrove.

Dans cette configuration, avec redondance au niveau du physique et virtuel, Woodgrove Bank est en mesure de proposer une résilience local, régional et la permanence globale de manière fiable. Woodgrove choisi cette configuration après l’évaluation d’un seul circuit Azure ExpressRoute par région, ainsi que la possibilité de basculement vers internet.
  
Si Woodgrove n’a pas pu avoir plusieurs circuits Azure ExpressRoute par région, le trafic de routage d’origine en Amérique du Nord pour le circuit ExpressRoute Azure dans Asie-Pacifique pouvait ajouter un niveau inacceptable de latence et la configuration du redirecteur DNS requise Ajoute la complexité.
  
Utilisation d’internet dans une configuration de sauvegarde n’est pas recommandé. Cela rompt principe de la fiabilité de la Woodgrove Bank, entraînant une expérience incohérente à l’aide de la connexion. En outre, une configuration manuelle est requise pour prendre en compte les publications BGP qui ont été configurées de basculement, la configuration de NAT, configuration DNS et la configuration du proxy. Cela Ajout de complexité de basculement augmente le temps de récupération et diminue leur capacité à diagnostiquer et résoudre les étapes.
  
Avez encore des questions sur la façon de planifier et implémenter la gestion du trafic ou ExpressRoute Azure ? Lire le reste de notre [Guide de performances et de réseau](https://aka.ms/tune) ou le [Forum aux questions de ExpressRoute Azure](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Utilisation de fournisseurs ExpressRoute Azure
<a name="BKMK_high-availability"> </a>

Choisissez les emplacements de vos circuits en fonction de votre bande passante, la latence, sécurité et planification de la haute disponibilité. Une fois que vous connaissez les emplacements optimales que vous souhaitez placer des circuits [passez en revue la liste actuelle des fournisseurs par région](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Travailler avec votre ou les fournisseurs pour sélectionner les meilleures options de connectivité, point à point, multipoint ou hébergé. N’oubliez pas, vous pouvez combiner et correspondent aux options de connectivité pour que votre conception de disponibilité élevée et de routage de prise en charge de la bande passante et autres composants redondants.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Voir aussi
<a name="BKMK_high-availability"> </a>

[Connectivité réseau à Office 365](network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Scénarios d’utilisation des communautés BGP dans ExpressRoute pour Office 365 (aperçu)](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
