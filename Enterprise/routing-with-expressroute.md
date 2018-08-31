---
title: Routage avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Pour bien comprendre le routage du trafic vers Office 365 à l’aide d’Azure ExpressRoute, vous devez connaître des exigences de gamme ExpressRoute principaux circuits ExpressRoute et de domaines de routage. Ces présenter les concepts fondamentaux pour l’utilisation ExpressRoute se base sur les clients Office 365.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540372"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routage avec ExpressRoute pour Office 365

Pour bien comprendre le routage du trafic vers Office 365 à l’aide d’Azure ExpressRoute, vous devez connaître de la base [des exigences de gamme ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) et [circuits ExpressRoute et les domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Ces présenter les concepts fondamentaux pour l’utilisation ExpressRoute se base sur les clients Office 365.
  
Les éléments clés dans les articles ci-dessus que vous aurez besoin de comprendre sont les suivantes :
  
- Circuits ExpressRoute ne sont pas associés à l’infrastructure physique spécifique, mais une connexion logique apportées à un seul emplacement homologation par Microsoft et un fournisseur homologation en votre nom.

- Il existe un mappage de 1:1 entre un circuit ExpressRoute et une clé s client.

- Chaque circuit peut prendre en charge jusqu'à 3 relations homologation indépendantes (peering Public Azure, peering Azure privé et Microsoft peering) ; Office 365 nécessite Microsoft peering.

- Chaque circuit a une bande passante fixe qui est partagée par tous les relations homologation.

- Adresses de n’importe quel public IPv4 et public sous forme de nombres qui sera utilisé pour la ExpressRoute circuit doit être validée comme étant la propriété par vous ou affectée exclusivement par le propriétaire de la plage d’adresses.

- Les circuits ExpressRoute virtuels sont redondants global et suivent les pratiques de routage BGP standard. C’est pourquoi nous vous recommandons de deux circuits physiques par sortie à votre fournisseur dans une configuration actif/actif.

Voir la [page du Forum aux questions](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) pour plus d’informations sur les services pris en charge, les coûts et les détails de configuration. Consultez l' [article d’emplacements ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) pour plus d’informations sur la liste des fournisseurs de connectivité offrant homologation prise en charge de Microsoft. Nous avons également enregistré une série [ExpressRoute Azure pour Office 365 formation](https://channel9.msdn.com/series/aer) 10 sur Channel 9 pour vous aider à comprendre les concepts plus en détail.
  
## <a name="ensuring-route-symmetry"></a>Assurer la symétrie de l’itinéraire

Les serveurs frontaux Office 365 sont accessibles sur Internet et ExpressRoute. Ces serveurs préfèrent acheminer sur circuits ExpressRoute lorsque les deux sont disponibles. Pour cette raison il est possible d’asymétrie itinéraire si le trafic entre votre réseau préfère Router via votre circuits Internet. Itinéraires asymétriques sont un problème car les périphériques qui effectuent une inspection des paquets peuvent bloquer le trafic de retour qui suit un chemin d’accès autre que les paquets sortants suivi.
  
Si vous démarrez une connexion à Office 365 sur Internet ou ExpressRoute, indépendamment de la source doit être une adresse publiquement routable. Avec de nombreux clients homologue directement avec Microsoft, ayant des adresses privées où la duplication est possible entre des clients n’est pas possible.
  
Voici les scénarios où sera effectuées communications à partir d’Office 365 à votre réseau local. Pour simplifier la conception de votre réseau, nous vous recommandons de routage ces sur le chemin d’accès Internet.
  
- ADFS lors de la validation de mot de passe pour la connexion.

- [Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- À partir d’un client Exchange Online le courrier vers un hôte local...

- SharePoint Online messagerie envoyer à partir de SharePoint Online à un hôte local.

- [SharePoint fédéré de recherche hybride](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint hybride BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype pour un environnement hybride Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) et/ou [Skype pour la fédération de l’entreprise](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype pour Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Pour Microsoft acheminer sur votre réseau pour les flux de trafic bidirectionnel, les itinéraires BGP à vos appareils local doivent être partagées avec Microsoft.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Déterminer les applications et les fonctionnalités de router via ExpressRoute

Lorsque vous configurez une relation d’homologation le domaine de routage homologation Microsoft sont approuvés pour l’accès approprié, vous serez en mesure de voir tous les services PaaS et SaaS services disponibles sur ExpressRoute. Les services Office 365 destinés aux ExpressRoute peuvent être gérés avec [des Communautés BGP](https://aka.ms/bgpexpressroute365) ou des [filtres d’itinéraires](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
Autres applications telles que Office 365 vidéo, est une application Office 365 ; Toutefois, Office 365 vidéo est constituée de trois composants différents, le portail, le service de diffusion en continu et le réseau de distribution de contenu. Le portail se trouve dans SharePoint Online, les durées de vie de diffusion en continu dans les Services de support Azure, et par l’intermédiaire du réseau de distribution de contenu au sein du CDN Azure. Le tableau suivant décrit ces composants.
  
| |
|**Composant**|**Application sous-jacente**|**Inclus dans SharePoint Online BGP Communauté ?**|**Utiliser**|
|:-----|:-----|:-----|:-----|
|Portail de vidéo Office 365  <br/> |SharePoint Online  <br/> |Oui  <br/> |Configuration, de téléchargement  <br/> |
|Service de diffusion en continu vidéo Office 365  <br/> |Azure Media Services  <br/> |Non  <br/> |Service de diffusion en continu, utilisé dans les événements la vidéo n’est pas disponible à partir du CDN  <br/> |
|Réseau de distribution de contenu vidéo Office 365  <br/> |Azure CDN  <br/> |Non  <br/> |Source principale de téléchargement/vidéo. [En savoir plus sur les réseaux vidéo Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

Chacune des fonctionnalités d’Office 365 qui sont disponibles à l’aide de Microsoft peering sont répertoriés dans l' [article de points de terminaison Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) par type d’application et le nom de domaine complet. La raison d’utiliser le nom de domaine complet dans les tableaux consiste à permettre aux clients de gérer le trafic à l’aide de fichiers PAC ou autres configurations de proxy, consultez notre guide de [la gestion des points de terminaison Office 365](https://aka.ms/manageo365endpoints) PAC par exemple des fichiers.
  
Dans certaines situations, nous avons utilisé un domaine générique où un ou plusieurs sub-noms de domaine complets sont publiés différemment le domaine générique de niveau supérieur. Cela se produit généralement lorsque le caractère générique représente une longue liste de serveurs qui sont tous publiés sur ExpressRoute et Internet, pendant un petit ensemble de sous-sites de destinations sont uniquement publiés sur Internet, ou inversement. Reportez-vous aux tableaux ci-dessous pour savoir où sont les différences.
  
Ce tableau affiche le caractère générique de noms de domaine complets sont publiés à internet et Azure ExpressRoute parallèlement à sub-noms de domaines complets qui sont publiés uniquement vers internet.

|**Domaine générique publiés vers des circuits ExpressRoute et Internet**|**Sub-nom de domaine complet publié à circuits Internet uniquement**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.email.microsoftonline.com  <br/> Portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> odc.officeapps.Live.com  <br/> odc.officeapps.Live.com  <br/> CDN.odc.officeapps.Live.com  <br/> OLS.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> ocws.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

Généralement les fichiers PAC sont destinés à envoyer des demandes de réseau à ExpressRoute publié des points de terminaison directement le circuit et toutes les autres demandes de réseau à votre serveur proxy. Si vous configurez un fichier PAC similaire à celle-ci, composez votre fichier PAC dans l’ordre suivant :
  
1. Inclure sub-noms de domaines complets à partir de la seconde colonne dans le tableau ci-dessus en haut de votre fichier PAC, envoyer le trafic vers votre serveur proxy. Nous avons créé un exemple de fichier PAC pour pouvoir utiliser dans notre article sur [la gestion des points de terminaison Office 365](https://aka.ms/manageexpressroute365).

2. Inclure tous les noms de domaine complets marqués publiés à ExpressRoute dans [cet article](https://aka.ms/o365endpoints) sous la première section, envoyer le trafic directement à votre circuit ExpressRoute.

3. Inclure d’autres points de terminaison de réseau ou règles sous ces deux entrées, envoyer le trafic vers votre serveur proxy.

Ce tableau affiche les domaines génériques qui sont publiés à circuits Internet uniquement avec sub-noms de domaines complets qui sont publiés sur Azure ExpressRoute et circuits Internet. Pour votre fichier PAC ci-dessus, les noms de domaines complets dans la seconde colonne dans le tableau ci-dessous sont répertoriées sous publiés dans ExpressRoute dans le lien référencé, ce qui signifie qu’ils doivent figurer dans le deuxième groupe d’entrées dans le fichier.

|**Domaine générique publié vers des circuits Internet uniquement**|**Sub-nom de domaine complet publié à circuits ExpressRoute et Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. office.net  <br/> |agent.Office.NET  <br/> |
|\*. office365.com  <br/> |Outlook.Office365.com  <br/> SMTP.Office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> découverte automatique -\<client\>. outlook.com  <br/> |
|\*. Windows.NET  <br/> |Login.Windows.NET  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routage Office 365 le trafic sur Internet et ExpressRoute

Pour acheminer vers Office 365 application de votre choix vous devez déterminer un certain nombre de facteurs clés.
  
1. La quantité de bande passante nécessite l’application. Échantillonnage utilisation existante est la seule méthode fiable pour cette détermination de votre organisation.

2. Les emplacements de sortie souhaité pour le trafic réseau à laisser votre réseau. Vous devez prévoir afin de réduire la latence du réseau pour la connectivité vers Office 365, comme cela influe sur les performances. Skype pour les entreprises en temps réel vocale et vidéo est particulièrement sensible à la latence du réseau médiocre.

3. Si vous souhaitez que tout ou partie de vos emplacements réseau pour tirer parti de ExpressRoute.

4. Les emplacements de votre fournisseur de réseau que vous avez choisie offre ExpressRoute à partir de.

Une fois que vous avez déterminé les réponses à ces questions, vous pouvez configurer un circuit ExpressRoute répondant aux besoins de bande passante et l’emplacement. Pour plus d’aide à la planification du réseau, reportez-vous à l' [étude de cas sur la façon dont Microsoft gère les réseau la planification des performances](https://aka.ms/tunemsit)et du [réseau Office 365 guide d’optimisation](https://aka.ms/tune) .
  
### <a name="example-1-single-geographic-location"></a>L’exemple 1 : Seul emplacement géographique
  
Cet exemple est un scénario d’une société fictive appelée Trey Research ayant un seul emplacement géographique.
  
Employés de Trey Research sont uniquement autorisées à se connecter aux services et des sites Web sur internet que le service de sécurité autorise explicitement sur la paire de proxy sortant qui se trouvent entre le réseau d’entreprise et de leur fournisseur de services Internet.
  
Trey Research prévoit d’utiliser ExpressRoute Azure pour Office 365 et reconnaît que certains types de trafic telles que le trafic destiné aux réseaux de distribution de contenu ne pourra pas router via la ExpressRoute pour la connexion Office 365. Dans la mesure où toutes les voies de circulation déjà sur les périphériques de proxy par défaut, ces demandes continuera à fonctionner comme auparavant. Une fois que Trey Research détermine qu’ils peuvent répondre aux exigences routage ExpressRoute Azure, ils passez pour créer un circuit, configurez le routage et la liaison du nouveau circuit ExpressRoute à un réseau virtuel. Une fois la configuration ExpressRoute Azure fondamentale, Trey Research utilise le [fichier de PAC #2 que nous publier](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) pour acheminer le trafic avec des données spécifiques du client sur le ExpressRoute directe pour les connexions Office 365.
  
Comme indiqué dans le diagramme suivant, Trey Research est en mesure de satisfaire la condition requise pour acheminer le trafic d’Office 365 sur internet et d’un sous-ensemble de trafic sur ExpressRoute à l’aide d’une combinaison de modifications de configuration proxy sortant et de routage.
  
1. Utilisation du [fichier de PAC #2 que nous publier](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) pour acheminer le trafic via un point de sortie internet distinct pour Azure ExpressRoute pour Office 365.

2. Les clients sont configurés avec un itinéraire par défaut vers les serveurs proxy de Trey Research.

Dans cet exemple de scénario, Trey Research utilise un périphérique proxy sortant. De même, les clients qui ne sont pas à l’aide de ExpressRoute Azure pour Office 365 souhaitent utiliser cette technique pour acheminer le trafic basé sur le coût d’inspecter le trafic destiné aux points de terminaison connu volume élevé.
  
Le plus grand volume de noms de domaine complets pour Exchange Online, SharePoint Online et Skype pour Business Online sont les suivantes :
  
![Réseau de périmètre du client ExpressRoute](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.Office365.com, outlook.office.com

- \<nom de client\>. sharepoint.com, \<nom de client\>-my.sharepoint.com, \<nom de client\>-\<application\>. sharepoint.com

- \*. Lync.com ainsi que les plages IP pour le trafic non TCP

- \*broadcast.officeapps.Live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* Word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

En savoir plus sur le [déploiement et la gestion des paramètres de proxy dans Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) et [en vous assurant d’Office 365 n’est pas limitée par votre serveur proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Avec un seul circuit ExpressRoute, il n’existe pas de haute disponibilité pour Trey Research. Dans l’éventualité paire redondante de Trey d’appareils edge qui traitent la connectivité ExpressRoute, il n’est pas un circuit ExpressRoute supplémentaire pour le basculement vers. Cela laisse Trey Research dans une situation comme basculement vers internet nécessite une nouvelle configuration manuelle et dans certains cas, les adresses IP de nouveau. Si Trey souhaite ajouter une haute disponibilité, la solution la plus simple consiste à ajouter des circuits ExpressRoute supplémentaires pour chaque emplacement et configurer les circuits d’une manière actif/actif.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routage ExpressRoute pour Office 365 avec plusieurs emplacements

Le dernier scénario, le routage du trafic Office 365 sur ExpressRoute est la base de l’architecture de routage encore plus complexe. Quel que soit le nombre d’emplacements, nombre de continents où ces emplacements existent, nombre de circuits ExpressRoute et ainsi de suite, en cours en mesure d’acheminer le trafic vers Internet, ainsi que certains types de trafic sur ExpressRoute seront requis.
  
Les questions supplémentaires qui doivent recevoir une réponse pour les clients disposant de plusieurs emplacements dans plusieurs zones géographiques sont les suivantes :
  
1. Avez-vous besoin d’un circuit ExpressRoute à chaque emplacement ? Si vous utilisez Skype pour Business Online ou souhaitez concernés par la sensibilité de latence de SharePoint Online ou Exchange Online, une paire de circuits de ExpressRoute actif/actif redondants sont recommandés dans chaque emplacement. Voir la Skype pour Business qualité et réseau connectivity guide multimédia pour plus d’informations.

2. Si un circuit ExpressRoute n’est pas disponible dans une région donnée, comment doit le trafic d’Office 365 destinés à être acheminé ?

3. Quelle est la méthode par défaut pour le trafic de consolidation dans le cas des réseaux avec plusieurs emplacements de petite taille ?

Chacun de ces présente un défi unique qui vous oblige à évaluer votre propre réseau, ainsi que les options disponibles auprès de Microsoft.

|**Considération**|**Composants réseau à évaluer**|
|:-----|:-----|
|Circuits dans plusieurs emplacements  <br/> |Nous vous recommandons un minimum de deux circuits configurés de manière actif/actif.  <br/> Besoins en matière de coût, la latence et bande passante doivent être comparées.  <br/> Utilisez BGP itinéraire coût, fichiers PAC et NAT pour gérer le routage avec plusieurs circuits.  <br/> |
|Routage à partir d’emplacements sans un circuit ExpressRoute  <br/> |Nous vous recommandons de sortie et la résolution DNS en tant que près de la personne à l’origine de la demande pour Office 365.  <br/> Redirection DNS peut servir à autoriser les bureaux à distance pour découvrir le point de terminaison approprié.  <br/> Dans le Bureau à distance, les clients doivent posséder un itinéraire disponible qui fournit l’accès au circuit ExpressRoute.  <br/> |
|Consolidation de serveurs de petite entreprise  <br/> |Utilisation de la bande passante et des données disponibles doit être comparée avec soin.  <br/> |

> [!NOTE]
> Microsoft préfère ExpressRoute via internet si l’itinéraire est disponible quel que soit l’emplacement physique.
  
Chacune de ces considérations doit prendre en considération pour chaque réseau unique. Voici un exemple.
  
### <a name="example-2-multi-geographic-locations"></a>L’exemple 2 : Différents emplacements géographiques multiples
  
Cet exemple est un scénario d’une société fictive appelée Humongous Insurance ayant plusieurs emplacements géographiques.
  
Assurance Humongous est dispersé géographiquement avec des bureaux dans le monde entier. Qu’ils souhaitent implémenter ExpressRoute Azure pour Office 365 conserver la majorité de leur trafic d’Office 365 pour les connexions réseau direct. Humongous Insurance possède également des bureaux sur deux continents supplémentaires. Les employés du Bureau à distance lorsque ExpressRoute n’est pas possible devez transmettre au moins l’une des installations principales pour utiliser une connexion ExpressRoute.
  
Le principe consiste à obtenir le trafic vers un centre de données Microsoft Office 365 destiné aussi rapidement que possible. Dans cet exemple, Humongous Insurance doit déterminer si leurs bureaux distants doit router via Internet pour accéder à un centre de données Microsoft sur n’importe quelle connexion aussi rapidement que possible ou si leurs bureaux distants doit router via un réseau interne pour accéder à Microsoft Centre de données via une connexion ExpressRoute aussi rapidement que possible.
  
Centres de données de Microsoft, les réseaux et architecture d’application sont conçus pour prendre des communications globalement disparates et les services de la manière la plus efficace possible. Il s’agit d’un des plus grands réseaux dans le monde. Demandes destinés à Office 365 qui restent sur des réseaux plus longtemps que nécessaire ne puissent pas tirer parti de cette architecture.
  
Situation Humongous Insurance, ils doivent procéder selon les applications qu'ils souhaitent sur ExpressRoute. Par exemple, si ils sont un Skype pour les entreprises en ligne client, ou que vous envisagez de tirer parti de connectivité ExpressRoute lors de la connexion à Skype externe pour les réunions en ligne d’entreprise, la conception recommandée dans le Skype pour la qualité des médias Business en ligne et de réseau guide de connectivité consiste à mettre en service un circuit ExpressRoute supplémentaire pour l’emplacement tiers. Cela peut être plus coûteux du point de vue de la mise en réseau ; Toutefois, le routage demandes à partir d’un continent à l’autre avant de proposer à un centre de données Microsoft peut entraîner une expérience médiocre ou inutilisable pendant Skype pour les communications et réunions en ligne Business.
  
Si Humongous Insurance n’utilise pas ou n’envisagiez d’exploiter Skype pour Business Online en aucune façon, routage du trafic réseau de Office 365 destiné à un continent avec une ExpressRoute connexion peut être possible mais peut provoquer latence inutile ou TCP congestion. Dans les deux cas, routage Internet trafic de destination à Internet sur le site local est recommandé pour tirer parti des réseaux de livraison de contenu que Office 365 s’appuie sur.
  
![Géographie multiples ExpressRoute](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Lorsque vous planifiez leur stratégie de géographie multiples Humongous Insurance, il existe un nombre d’éléments à prendre en compte autour de la taille de circuit, nombre de circuits, le basculement et ainsi de suite.
  
Avec ExpressRoute dans un seul emplacement avec plusieurs régions, essayez d’utiliser le circuit, Humongous Insurance veut s’assurer que les connexions vers Office 365 à partir du Bureau à distance sont envoyées au centre de données Office 365 le plus proche du siège social et reçues par le emplacement du siège social. Pour ce faire, Humongous Insurance implémente redirection DNS pour réduire le nombre d’allers-retours et recherches DNS requis pour établir la connexion avec l’environnement Office 365 plus proche du point de sortie internet sièges sociaux appropriée. Cela empêche le client de résolution d’un serveur frontal local et garantit le serveur frontal d’à que la personne qui se connecte est proche du siège social où Humongous Insurance est homologue avec Microsoft. Vous pouvez également apprendre à [affecter un redirecteur conditionnel pour un nom de domaine](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
Dans ce scénario, le trafic du Bureau à distance doit résoudre l’infrastructure de serveur frontal Office 365 en Amérique du Nord et tirer parti d’Office 365 pour se connecter aux serveurs principaux en fonction de l’architecture de l’application Office 365. Par exemple, Exchange Online se terminerait la connexion en Amérique du Nord et les serveurs frontaux connecte au serveur de boîtes aux lettres principal où résident les clients. Tous les services ont un service de porte répandu constitué de destinations de monodiffusion et de diffusion aléatoire.
  
Si Humongous a des bureaux principaux dans plusieurs continents, un minimum de deux circuits actif/actif par région sont recommandées afin de réduire la latence pour les applications sensibles telles que Skype pour Business Online. Si tous les bureaux se trouvent dans un seul continent ou n’utilisant pas de collaboration en temps réel, ayant une sortie consolidée ou distribuée point est une décision spécifique du client. Lorsque plusieurs circuits sont disponibles, routage BGP permet de garantir le basculement des circuits unique est indisponible.
  
Pour plus d’informations sur les exemples de [configuration de routage](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) et [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Sélective routage avec ExpressRoute

Routage sélective avec ExpressRoute peut-être être nécessaires pour différentes raisons, telles que le test, présentant ExpressRoute à un sous-ensemble d’utilisateurs. Il existe différents outils clients permet de manière sélective router le trafic réseau de Office 365 sur ExpressRoute :
  
1. **Itinéraire filtrage/répartition** - en autorisant les itinéraires BGP vers Office 365 sur ExpressRoute à un sous-ensemble de vos sous-réseaux ou les routeurs. Cela achemine sélectivement par segment de réseau client ou un emplacement physique office. Il est courant pour le déploiement échelonnée de ExpressRoute pour Office 365 et est configuré sur vos périphériques BGP.

2. **Fichiers/URL PAC** - dirigeant Office 365 destiné le trafic réseau pour complets spécifiques acheminer sur un chemin spécifique. Cela achemine sélectivement par ordinateur client tels qu’identifiés par le [déploiement du fichier PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Le filtrage des itinéraires** - [filtres d’itinéraires](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) sont un moyen d’utiliser un sous-ensemble des services pris en charge par le biais de Microsoft peering.

4. **Communautés BGP** - filtrage basé sur les [balises de la Communauté BGP](https://aka.ms/bgpexpressroute365) permet à un client déterminer les applications Office 365 parcourt ExpressRoute et qui sera parcourir internet.

Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Voir aussi

[Connectivité réseau à Office 365](network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[La qualité des médias et des performances pour la connectivité réseau dans Skype pour les entreprises en ligne](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype pour Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype pour les entreprises en ligne](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flux des appels à l’aide de ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Utilisation de communautés BGP dans ExpressRoute pour les scénarios d’Office 365](bgp-communities-in-expressroute.md)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Réseau Office 365 et réglage des performances](network-planning-and-performance.md)
