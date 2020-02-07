---
title: Planification du réseau avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute pour Office 365 fournit la connectivité de couche 3 entre votre réseau et les centres de donnes de Microsoft. Les circuits utilisent des publicités d’itinéraires BGP (Border Gateway Protocol) de serveurs frontaux d’Office 365. Du point de vue de vos appareils sur site, lorsqu’ils doivent sélectionner le chemin d’accès TCP/IP correct vers Office 365, Azure ExpressRoute est considéré comme une alternative à Internet.
ms.openlocfilehash: 2f38b88b5d940d1a8aa171c777e82a4a308be0cf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844555"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planification du réseau avec ExpressRoute pour Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

ExpressRoute pour Office 365 fournit la connectivité de couche 3 entre votre réseau et les centres de donnes de Microsoft. Les circuits utilisent des publicités d’itinéraires BGP (Border Gateway Protocol) de serveurs frontaux d’Office 365. Du point de vue de vos appareils sur site, lorsqu’ils doivent sélectionner le chemin d’accès TCP/IP correct vers Office 365, Azure ExpressRoute est considéré comme une alternative à Internet.
  
Azure ExpressRoute ajoute un chemin d’accès direct à un ensemble spécifique de fonctionnalités et de services pris en charge et proposés par les serveurs Office 365 dans les centres de connaissances de Microsoft. Azure ExpressRoute ne remplace pas la connectivité Internet aux centres de noms Microsoft ou aux services Internet de base, tels que la résolution de noms de domaine. Azure ExpressRoute et vos circuits Internet doivent être sécurisés et redondants.
  
Le tableau suivant présente quelques différences entre les connexions Internet et Azure ExpressRoute dans le contexte d’Office 365.

|**Différences de planification réseau**|**Connexion au réseau Internet**|**Connexion réseau ExpressRoute**|
|:-----|:-----|:-----|
| Accès aux services Internet requis, y compris ;  <br/>  Résolution de noms DNS  <br/>  Vérification de la révocation de certificats  <br/>  Réseaux de distribution de contenu  <br/> |Oui  <br/> |Les demandes d’infrastructure DNS et/ou CDN appartenant à Microsoft peuvent utiliser le réseau ExpressRoute.  <br/> |
| Accès aux services Office 365, y compris ;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Entreprise Online  <br/>  Office dans un navigateur  <br/>  Portail et authentification Office 365  <br/> |Oui, toutes les applications et fonctionnalités  <br/> |Oui, [applications et fonctionnalités spécifiques](https://aka.ms/o365endpoints) <br/> |
|Sécurité locale sur le périmètre.  <br/> |Oui  <br/> |Oui  <br/> |
|Planification de la haute disponibilité.  <br/> |Basculement vers une autre connexion réseau Internet  <br/> |Basculement vers une autre connexion ExpressRoute  <br/> |
|Connexion directe avec un profil réseau prévisible.  <br/> |Non  <br/> |Oui  <br/> |
|Connectivité IPv6.  <br/> |Oui  <br/> |Oui  <br/> |

Développez les titres ci-dessous pour obtenir des instructions de planification réseau supplémentaires. Nous avons également enregistré une série [de formations Azure ExpressRoute pour Office 365](https://channel9.msdn.com/series/aer) qui explore plus en détail.

## <a name="existing-azure-expressroute-customers"></a>Clients Azure ExpressRoute existants

Si vous utilisez un circuit ExpressRoute Azure existant et souhaitez ajouter la connectivité Office 365 sur ce circuit, vérifiez le nombre de circuits, les emplacements de sortie et la taille des circuits afin de vous assurer qu’ils répondent aux besoins de votre utilisation d’Office 365. La plupart des clients nécessitent une bande passante supplémentaire et de nombreux autres nécessitent des circuits supplémentaires.
  
Pour permettre l’accès à Office 365 sur vos circuits ExpressRoute Azure existants, [configurez les filtres d’itinéraires](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) afin de vous assurer que les services Office 365 sont accessibles.
  
L’abonnement Azure ExpressRoute est centré sur le client, ce qui signifie que les abonnements sont liés aux clients. En tant que client, vous pouvez avoir plusieurs circuits ExpressRoute Azure et accéder à de nombreuses ressources Cloud Microsoft sur ces circuits. Par exemple, vous pouvez choisir d’accéder à une machine virtuelle hébergée par Azure, à un client de test Office 365 et à un client de production Office 365 sur une paire de circuits ExpressRoute Azure redondants.
  
Ce tableau décrit les deux types de relations d’homologation que vous pouvez choisir d’implémenter sur vos circuits.

|**Relation d’homologation**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Services** <br/> |IaaS : machines virtuelles Azure  <br/> |PaaS : services publics Azure  <br/> SaaS : Office 365  <br/> SaaS : Dynamics 365  <br/> |
|Initiation de connexion * * * * <br/> |Client-Microsoft  <br/> Microsoft-à-client  <br/> |Client-Microsoft  <br/> Microsoft-à-client  <br/> |
|**Prise en charge de QoS** <br/> |Aucune qualité de service  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS prend en charge Skype entreprise uniquement pour le moment.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planification de la bande passante pour Azure ExpressRoute

Chaque client Office 365 dispose de besoins en bande passante uniques en fonction du nombre de personnes à chaque emplacement, de la façon dont ils sont actifs avec chaque application Office 365, ainsi que d’autres facteurs tels que l’utilisation des équipements locaux ou hybrides et des configurations de sécurité réseau.
  
Si la bande passante est trop faible, des saturations de données, des retransmissions de données et des délais imprévisibles seront survenir. Une bande passante trop importante entraînera un coût inutile. Sur un réseau existant, la bande passante est souvent mentionnée en termes de capacité disponible sur le circuit sous la forme d’un pourcentage. Une marge de 10% entraînera probablement une congestion et une marge de 80% signifie généralement un coût inutile. Les allocations de la cible de hauteur standard représentent entre 20% et 50%.
  
Pour trouver le niveau de bande passante approprié, le meilleur moyen est de tester votre consommation réseau existante. Il s’agit de la seule façon d’obtenir une mesure réelle de l’utilisation et de la nécessité que chaque configuration et application réseau soient différentes d’une certaine manière. Lors de la mesure, vous devez prêter une attention particulière à la consommation totale de bande passante, à la latence et à la congestion TCP pour comprendre vos besoins en matière de réseau.
  
Une fois que vous avez une base estimée qui inclut toutes les applications réseau, pilotez Office 365 avec un petit groupe qui comprend les différents profils des personnes de votre organisation pour déterminer l’utilisation réelle et utilisez les deux mesures pour estimer la quantité de bande passante requise pour chaque emplacement de bureau. S’il existe des problèmes de latence ou de congestion TCP dans le cadre de vos tests, vous devrez peut-être déplacer la sortie plus près des personnes à l’aide d’Office 365 ou supprimer l’analyse de réseau intensive, telle que le déchiffrement/l’inspection SSL.
  
Toutes nos recommandations sur le type de traitement réseau recommandé s’appliquent à la fois aux circuits ExpressRoute et Internet. Il en est de même pour les autres conseils sur notre [site de réglage des performances](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Application des contrôles de sécurité à Azure ExpressRoute pour les scénarios Office 365

La sécurisation de la connectivité Azure ExpressRoute commence par les mêmes principes que la sécurisation de la connectivité Internet. De nombreux clients choisissent de déployer les contrôles réseau et de périmètre le long du chemin ExpressRoute connectant leur réseau local à Office 365 et à d’autres nuages Microsoft. Ces contrôles peuvent inclure des pare-feu, des proxys d’applications, la prévention des fuites de données, la détection d’intrusions, les systèmes de prévention des intrusions, etc. Dans de nombreux cas, les clients appliquent différents niveaux de contrôle au trafic initié à partir de l’accès local à Microsoft, ainsi que le trafic initié par Microsoft vers le réseau client local, et non le trafic initié en local Destination Internet.
  
Voici quelques exemples d’intégration de la sécurité avec le [modèle de connectivité ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-connectivity-models) que vous choisissez de déployer.

|**Option d’intégration ExpressRoute**|**Modèle de périmètre de sécurité réseau**|
|:-----|:-----|
|Même emplacement au niveau d’un échange de cloud  <br/> |Installez de nouvelles ou tirez parti de l’infrastructure de sécurité/périmètre existante dans la zone de localisation où la connexion ExpressRoute est établie.  <br/> Tirez parti de la fonctionnalité de co-location uniquement à des fins de routage/d’interconnexion et de connexions de dépôt arrière à partir de la fonction de co-location dans l’infrastructure de sécurité/périmètre locale.  <br/> |
|Ethernet de point à point  <br/> |Mettre fin à la connexion ExpressRoute point à point dans l’infrastructure de sécurité/périmètre locale existante.  <br/> Installez une nouvelle infrastructure de sécurité/de périmètre propre au chemin d’accès ExpressRoute et arrêtez-y la connexion de point à point.  <br/> |
|Any-to-any IPVPN  <br/> |Tirez parti d’une infrastructure de sécurité/périmètre locale existante à tous les emplacements de sortie dans le IPVPN utilisé pour la connectivité de ExpressRoute pour 365 Office.  <br/> Épinglage IPVPN utilisé pour ExpressRoute pour Office 365 vers des emplacements locaux spécifiques désignés pour servir de sécurité/périmètre.  <br/> |

Certains fournisseurs de services proposent également des fonctionnalités de sécurité/périmètre gérées dans le cadre de leurs solutions d’intégration avec Azure ExpressRoute.
  
Lors de l’examen de la topologie des options de périmètre réseau/sécurité utilisées pour les connexions ExpressRoute pour Office 365, les éléments suivants sont des considérations supplémentaires
  
- La profondeur et les contrôles réseau/sécurité peuvent avoir un impact sur les performances et l’extensibilité de l’expérience utilisateur Office 365.

- Les flux sortants (locaux-\>Microsoft) et entrants (Microsoft\>sur site) [si activé] les flux peuvent avoir des exigences différentes. Celles-ci sont probablement différentes des destinations Internet générales.

- La configuration requise pour Office 365 pour les ports/protocoles et les sous-réseaux IP nécessaires est identique, que le trafic soit acheminé via ExpressRoute pour Office 365 ou via Internet.

- Le positionnement topologique des contrôles réseau/sécurité du client détermine le réseau de bout en bout de bout en bout entre l’utilisateur et le service Office 365 et peut avoir un impact substantiel sur la latence et la congestion du réseau.

- Les clients sont encouragés à concevoir leur topologie de sécurité/périmètre pour une utilisation avec ExpressRoute pour Office 365 conformément aux meilleures pratiques en matière de redondance, de haute disponibilité et de récupération d’urgence.

Voici un exemple de Woodgrove Bank qui compare les différentes options de connectivité Azure ExpressRoute avec les modèles de sécurité de périmètre présentés ci-dessus.
  
### <a name="example-1-securing-azure-expressroute"></a>Exemple 1 : sécurisation d’Azure ExpressRoute
  
Woodgrove Bank envisage d’implémenter Azure ExpressRoute et, après avoir planifié l’architecture optimale pour le [routage avec ExpressRoute pour Office 365](routing-with-expressroute.md) et après avoir utilisé les recommandations ci-dessus pour comprendre les besoins en bande passante, il détermine la meilleure méthode de sécurisation de son périmètre.
  
Pour Woodgrove, une organisation multinationale avec des emplacements sur plusieurs continents, la sécurité doit s’étendre sur tous les périmètres. L’option de connectivité optimale pour Woodgrove Bank est une connexion à plusieurs points avec plusieurs emplacements d’homologation dans le monde entier afin de répondre aux besoins de leurs employés dans chaque continent. Chaque continent inclut des circuits ExpressRoute Azure redondants dans le continent et la sécurité doit s’étendre sur tous ces circuits.
  
L’infrastructure existante de Woodgrove est fiable et peut gérer le travail supplémentaire, par conséquent, la Woodgrove Bank est en mesure d’utiliser l’infrastructure pour son ExpressRoute et la sécurité de périmètre Internet. Si cela n’était pas le cas, Woodgrove pourrait choisir d’acheter un équipement supplémentaire pour compléter son équipement existant ou pour gérer un autre type de connexion.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Haute disponibilité et basculement avec Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Nous vous recommandons de configurer au moins deux circuits actifs à partir de chaque sortie avec ExpressRoute vers votre fournisseur ExpressRoute. Il s’agit de l’emplacement le plus courant pour les clients et vous pouvez facilement les éviter en mettant en service une paire de circuits ExpressRoute actifs/actifs. Nous recommandons également au moins deux circuits Internet actifs/actifs, car de nombreux services Office 365 sont disponibles uniquement sur Internet.
  
Le point de sortie de votre réseau comporte de nombreux autres appareils et circuits qui jouent un rôle essentiel dans la façon dont les personnes perçoivent la disponibilité. Ces parties de vos scénarios de connectivité ne sont pas couvertes par les accords SLA ExpressRoute ou Office 365, mais ils jouent un rôle essentiel dans la disponibilité du service de bout en bout comme perçu par les personnes de votre organisation.
  
Concentrez-vous sur les personnes qui utilisent et fonctionnent Office 365, si une défaillance d’un composant affecte l’expérience des peuples à l’aide du service, recherchez des méthodes permettant de limiter le pourcentage total de personnes affectées. Si le mode de basculement est complexe, tenez compte de l’expérience des peuples pendant la récupération et recherchez les modes de basculement simples et automatisés.
  
À l’extérieur de votre réseau, Office 365, ExpressRoute et votre fournisseur ExpressRoute ont tous des niveaux de disponibilité différents.
  
### <a name="service-availability"></a>Disponibilité du service
  
- Les services Office 365 sont couverts par des [contrats de niveau de service](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)bien définis, qui incluent des mesures de temps et de disponibilité pour des services individuels. Une raison pour laquelle Office 365 peut maintenir ces niveaux de disponibilité de service élevés est la capacité pour des composants individuels de basculer en continu entre les nombreux centres de donnée Microsoft, à l’aide du réseau Microsoft Global. Ce basculement s’étend du centre de ressources et du réseau aux différents points de sortie Internet, et permet un basculement transparent du point de vue des personnes qui utilisent le service.

- ExpressRoute [fournit un contrat SLA de disponibilité de 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) sur des circuits dédiés individuels entre le serveur Edge Microsoft et l’infrastructure partenaire ou fournisseur ExpressRoute. Ces niveaux de service sont appliqués au niveau du circuit ExpressRoute, qui se compose de [deux interconnexions indépendantes](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) entre le matériel Microsoft redondant et le fournisseur réseau dans chaque emplacement d’homologation.

### <a name="provider-availability"></a>Disponibilité des fournisseurs
  
- Les arrangements de niveau de service de Microsoft s’arrêtent auprès de votre fournisseur ou partenaire ExpressRoute. C’est également le premier endroit où vous pouvez créer des choix qui influenceront votre niveau de disponibilité. Vous devez évaluer étroitement l’architecture, la disponibilité et les caractéristiques de résilience que votre fournisseur ExpressRoute propose entre votre périmètre réseau et votre connexion de fournisseurs à chaque emplacement d’homologation Microsoft. Faites attention aux aspects logiques et physiques de la redondance, de l’équipement d’homologation, des circuits WAN fournis par les opérateurs et de toute valeur ajoutée supplémentaire, comme les services NAT ou les pare-feu gérés.

### <a name="designing-your-availability-plan"></a>Conception de votre plan de disponibilité
  
Nous vous recommandons vivement de planifier et de concevoir la haute disponibilité et la résilience dans vos scénarios de connectivité de bout en bout pour Office 365. Une conception doit inclure ;
  
- aucun point de défaillance unique, y compris les circuits Internet et ExpressRoute.

- minimisation du nombre de personnes affectées et de la durée de cet impact pour les modes de défaillance les plus prévisibles.

- optimisation pour le processus de récupération simple, reproductible et automatique à partir des modes d’échec anticipés.

- prise en charge des exigences complètes de votre trafic et de votre fonctionnalité réseau via des chemins redondants, sans dégradation substantielle.

Vos scénarios de connectivité doivent inclure une topologie réseau optimisée pour plusieurs chemins réseau indépendants et actifs vers Office 365. Cette opération offre une meilleure disponibilité de bout en bout qu’une topologie qui est optimisée uniquement pour la redondance au niveau du périphérique ou de l’équipement individuel.
  
> [!TIP]
> Si vos utilisateurs sont répartis sur plusieurs continents ou régions géographiques et que chacun de ces emplacements se connecte sur des circuits WAN redondants à un emplacement local unique où se trouve un seul circuit ExpressRoute, vos utilisateurs auront moins de disponibilité du service de bout en bout par rapport à une conception de topologie réseau qui inclut des circuits ExpressRoute indépendants qui relient les différentes régions à l’emplacement d’homologation le plus proche.
  
Nous vous recommandons de configurer au moins deux circuits ExpressRoute avec chaque circuit se connectant à un autre emplacement géographique. Vous devez mettre en service cette paire de circuits active-active pour chaque région où des personnes utiliseront la connectivité ExpressRoute pour les services Office 365. Cela permet à chaque région de rester connectée pendant une catastrophe qui affecte un emplacement majeur, tel qu’un centre de donneur ou un lieu d’homologation. Leur configuration en tant que actif/actif permet de répartir le trafic des utilisateurs finaux entre plusieurs chemins d’accès réseau. Cela réduit l’étendue des personnes affectées lors des pannes du matériel ou du périphérique réseau.
  
Il n’est pas recommandé d’utiliser un seul circuit ExpressRoute avec Internet comme sauvegarde.
  
### <a name="example-2-failover-and-high-availability"></a>Exemple 2 : basculement et haute disponibilité
  
La conception multi-géographique de la Woodgrove Bank a subi une révision du routage, de la bande passante, de la sécurité et doit à présent passer par un examen de la haute disponibilité. La Woodgrove Bank pense que la haute disponibilité couvre trois catégories ; résistance, fiabilité et redondance.
  
La résilience permet à la Woodgrove Bank de récupérer rapidement après des défaillances. La fiabilité permet à la Woodgrove Bank d’offrir un résultat cohérent dans le système. La redondance permet à Woodgrove Bank de passer d’une ou plusieurs instances d’infrastructure mises en miroir.
  
Dans chaque configuration Edge, Woodgrove a redondant des pare-feu, des proxys et des ID. Pour l’Amérique du Nord, la Woodgrove Bank dispose d’une configuration Edge dans son centre de centre de Dallas et d’une autre configuration Edge dans son centre de centre de serveurs. L’équipement redondant à chaque emplacement offre une résistance à cet emplacement.
  
La configuration réseau de Woodgrove Bank est basée sur quelques principes clés :
  
- Dans chaque région géographique, il existe plusieurs circuits ExpressRoute Azure.

- Chaque circuit dans une région peut prendre en charge tout le trafic réseau au sein de cette région.

- Le routage choisira clairement l’un ou l’autre chemin en fonction de la disponibilité, de l’emplacement, etc.

- Le basculement entre les circuits ExpressRoute Azure se produit automatiquement sans aucune configuration ou action supplémentaire requise par Woodgrove.

- Le basculement entre circuits Internet se produit automatiquement sans aucune configuration ou action supplémentaire requise par Woodgrove.

Dans cette configuration, avec redondance au niveau physique et virtuel, Woodgrove Bank peut offrir une résistance locale, une résistance régionale et une résistance globale de manière fiable. Woodgrove a choisi cette configuration après avoir évalué un seul circuit ExpressRoute Azure par région, ainsi que la possibilité de basculer sur Internet.
  
Si la Woodgrove Bank n’a pas pu avoir plusieurs circuits ExpressRoute Azure par région, le trafic de routage en Amérique du Nord vers le circuit ExpressRoute Azure dans la zone Asie Pacifique ajouterait un niveau de latence et de configuration de redirecteur DNS inacceptables. Ajoute de la complexité.
  
Il n’est pas recommandé d’exploiter Internet comme configuration de sauvegarde. Cela romp le principe de fiabilité de Woodgrove, ce qui entraîne une expérience incohérente à l’aide de la connexion. En outre, la configuration manuelle est requise pour le basculement en tenant compte des annonces BGP qui ont été configurées, de la configuration NAT, de la configuration DNS et de la configuration du proxy. La complexité de basculement ajoutée augmente le temps de récupération et réduit leur capacité à diagnostiquer et à dépanner les étapes impliquées.
  
Vous avez toujours des questions sur la planification et l’implémentation de la gestion du trafic ou d’Azure ExpressRoute ? Lisez le reste de notre [Guide sur les performances et le réseau,](https://aka.ms/tune) ou le [Forum aux questions sur Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Utilisation des fournisseurs ExpressRoute Azure
<a name="BKMK_high-availability"> </a>

Choisissez les emplacements de vos circuits en fonction de votre bande passante, de la latence, de la sécurité et de la planification de la haute disponibilité. Une fois que vous avez déterminé les emplacements optimaux pour placer [les circuits, examinez la liste actuelle des fournisseurs par région](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Collaborez avec votre fournisseur ou vos fournisseurs pour sélectionner les meilleures options de connectivité, point-à-point, multipoint ou hébergé. N’oubliez pas que vous pouvez mélanger et faire correspondre les options de connectivité à condition que la bande passante et les autres composants redondants prennent en charge votre conception et la haute disponibilité.
  
Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Rubriques connexes
<a name="BKMK_high-availability"> </a>

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365 (aperçu)](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flux d’appels à l’aide de ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
