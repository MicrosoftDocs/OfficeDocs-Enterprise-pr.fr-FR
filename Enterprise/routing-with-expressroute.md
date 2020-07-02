---
title: Routage avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Pour bien comprendre le trafic de routage vers Office 365 à l’aide d’Azure ExpressRoute, vous avez besoin d’une prise ferme des exigences de routage ExpressRoute de base et des circuits ExpressRoute et des domaines de routage. Ces éléments présentent les bases de l’utilisation de ExpressRoute par les clients Office 365.
ms.openlocfilehash: c9d81e0823b63750a456f559855bb130a2e87b07
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998193"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routage avec ExpressRoute pour Office 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Pour bien comprendre le trafic de routage vers Office 365 à l’aide d’Azure ExpressRoute, vous avez besoin d’une prise ferme des [exigences de routage ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) de base et des [circuits ExpressRoute et des domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Ces éléments présentent les bases de l’utilisation de ExpressRoute par les clients Office 365.
  
Voici quelques-uns des éléments clés des articles ci-dessus que vous devrez comprendre :
  
- Les circuits ExpressRoute ne sont pas mappés à une infrastructure physique spécifique, mais constituent une connexion logique établie à un emplacement d’homologation unique par Microsoft et un fournisseur d’homologation en votre nom.

- Il existe un mappage de 1:1 entre un circuit ExpressRoute et une clé s client.

- Chaque circuit peut prendre en charge 2 relations d’homologation indépendantes (homologation privée Azure et homologation Microsoft); Office 365 nécessite Microsoft peering.

- Chaque circuit dispose d’une bande passante fixe qui est partagée entre toutes les relations d’homologation.

- Toutes les adresses IPv4 publiques et publiques sous forme de numéros qui seront utilisés pour le circuit ExpressRoute doivent être validées par vous ou attribuées exclusivement par le propriétaire de la plage d’adresses.

- Les circuits ExpressRoute virtuels sont redondants de façon globale et suivent les pratiques de routage BGP standard. C’est pourquoi nous recommandons deux circuits physiques par sortie à votre fournisseur dans une configuration active/active.

Pour plus d’informations sur les services pris en charge, les coûts et les détails de configuration, voir la [page Forum aux questions](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) . Consultez l' [article des emplacements ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) pour obtenir des informations sur la liste des fournisseurs de connectivité qui offrent une prise en charge de Microsoft peering. Nous avons également enregistré une série de [formations Azure ExpressRoute pour Office 365 pour Office](https://channel9.msdn.com/series/aer) sur Channel 9 afin de mieux comprendre les concepts.
  
## <a name="ensuring-route-symmetry"></a>Garantir la symétrie de l’itinéraire

Les serveurs frontaux Office 365 sont accessibles sur Internet et sur ExpressRoute. Ces serveurs préféreront effectuer un reroutage vers des circuits locaux sur ExpressRoute lorsque les deux sont disponibles. En raison de cette situation, il existe un risque d’acheminer l’asymétrie si le trafic provenant de votre réseau préfère être acheminé sur vos circuits Internet. Les itinéraires asymétriques posent problème car les appareils qui effectuent une inspection des paquets avec état peuvent bloquer le trafic de retour qui suit un chemin d’accès différent des paquets sortants suivis.
  
Que vous établissez une connexion à Office 365 via Internet ou ExpressRoute, la source doit être une adresse routable publiquement. Avec de nombreux clients qui s’homologuent directement avec Microsoft, il n’est pas possible d’utiliser des adresses privées pour faire la duplication entre les clients.
  
Voici les scénarios dans lesquels les communications d’Office 365 vers votre réseau local seront établies. Pour simplifier la conception de votre réseau, nous vous recommandons de les acheminer via le chemin d’accès Internet.
  
- Des services SMTP tels que le courrier provenant d’un client Exchange Online vers un hôte local ou un courrier SharePoint Online envoyé depuis SharePoint Online vers un hôte local. Le protocole SMTP est utilisé plus largement au sein du réseau de Microsoft que les préfixes d’itinéraire partagés sur les circuits ExpressRoute et que les serveurs SMTP sur site publicitaires sur ExpressRoute provoquent des échecs avec ces autres services.

- ADFS lors de la validation du mot de passe pour la connexion.

- [Déploiements hybrides Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- [Recherche hybride fédérée SharePoint](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS SharePoint hybride](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype entreprise hybride](https://technet.microsoft.com/library/jj205403.aspx) et/ou [Fédération Skype entreprise](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype entreprise, Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Pour que Microsoft redirige vers votre réseau les flux de trafic bidirectionnel, les itinéraires BGP vers vos appareils locaux doivent être partagés avec Microsoft. Lorsque vous publiez des préfixes de routage vers Microsoft via ExpressRoute, vous devez suivre les meilleures pratiques suivantes :

1) Ne publiez pas le même préfixe d’itinéraire d’adresse IP publique sur l’Internet public et sur ExpressRoute. Il est vivement recommandé que les publications du préfixe d’itinéraire IP BGP vers Microsoft via ExpressRoute proviennent d’une plage qui n’est pas publiée sur Internet. Si cela n’est pas possible en raison de l’espace d’adressage IP disponible, il est essentiel de vous assurer que vous publiez une plage plus spécifique sur ExpressRoute que n’importe quel circuit Internet.

2) Utilisez des pools IP NAT distincts par circuit ExpressRoute et séparez-les de vos circuits Internet.

3) N’oubliez pas que tout itinéraire annoncé à Microsoft attirera le trafic réseau à partir de n’importe quel serveur du réseau de Microsoft, pas seulement ceux pour lesquels des itinéraires sont annoncés sur votre réseau via ExpressRoute. Publiez uniquement les itinéraires vers les serveurs où les scénarios de routage sont définis et bien compris par votre équipe. Publiez des préfixes d’adresse IP distincts sur chacun des différents circuits ExpressRoute de votre réseau.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Choix de l’itinéraire des applications et des fonctionnalités sur ExpressRoute

Lorsque vous configurez une relation d’homologation à l’aide du domaine de routage d’homologation Microsoft et que vous êtes approuvé pour l’accès approprié, vous pouvez voir tous les services PaaS et SaaS disponibles sur ExpressRoute. Les services Office 365 conçus pour ExpressRoute peuvent être gérés avec des [communautés BGP](https://aka.ms/bgpexpressroute365) ou des [filtres d’itinéraires](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
D’autres applications, telles que la vidéo Office 365, est une application Office 365 ; Toutefois, la vidéo Office 365 est composée de trois composants différents : le portail, le service de diffusion en continu et le réseau de distribution de contenu. Le portail réside dans SharePoint Online, le service de diffusion en continu dans Azure Media Services et le réseau de distribution de contenu dans le CDN Azure. Le tableau suivant présente ces composants.

|**Composant**|**Application sous-jacente**|**Inclus dans la communauté BGP SharePoint Online ?**|**Utiliser**|
|:-----|:-----|:-----|:-----|
|Portail vidéo Office 365  <br/> |SharePoint Online  <br/> |Oui  <br/> |Configuration, chargement  <br/> |
|Service de diffusion vidéo en continu Office 365  <br/> |Azure Media Services  <br/> |Non  <br/> |Service de diffusion en continu, utilisé en cas d’indisponibilité de la vidéo à partir du CDN  <br/> |
|Réseau de distribution de contenu vidéo Office 365  <br/> |CDN Azure  <br/> |Non  <br/> |Source principale de téléchargement/transmission vidéo en continu. [En savoir plus sur la mise en réseau vidéo Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).  <br/> |

Chacune des fonctionnalités Office 365 disponibles à l’aide de l’homologation Microsoft est répertoriée dans l' [article points de terminaison 365 Office](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) par type d’application et nom de domaine complet. La raison d’utiliser le nom de domaine complet dans les tables est de permettre aux clients de gérer le trafic à l’aide de fichiers PAC ou d’autres configurations de proxy, consultez notre guide de [gestion des points de terminaison Office 365](https://aka.ms/manageo365endpoints) pour obtenir des exemples de fichiers PAC.
  
Dans certains cas, nous avons utilisé un domaine générique où un ou plusieurs noms de domaine complets sont annoncés différemment du domaine générique de niveau supérieur. Cela se produit généralement lorsque le caractère générique représente une longue liste de serveurs qui sont tous annoncés sur ExpressRoute et Internet, tandis qu’un petit sous-ensemble de destinations n’est publié que sur Internet ou inversement. Reportez-vous aux tableaux ci-dessous pour comprendre où se trouvent les différences.
  
Ce tableau affiche les noms de domaine complets génériques annoncés à la fois sur Internet et sur Azure ExpressRoute, parallèlement aux sous-noms de domaine complets publiés uniquement sur Internet.

|**Domaine générique annoncé sur les circuits ExpressRoute et Internet**|**Sous-nom de domaine complet annoncé sur les circuits Internet uniquement**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

En règle générale, les fichiers PAC sont destinés à envoyer des demandes réseau aux points de terminaison publiés ExpressRoute directement vers le circuit et toutes les autres requêtes réseau vers votre proxy. Si vous configurez un fichier PAC comme ceci, composez votre fichier PAC dans l’ordre suivant :
  
1. Incluez les sous-noms de domaine complets de la colonne deux dans le tableau ci-dessus en haut de votre fichier PAC, en envoyant le trafic vers votre proxy. Nous avons créé un exemple de fichier PAC que vous pouvez utiliser dans notre article sur la [gestion des points de terminaison Office 365](https://aka.ms/manageexpressroute365).

2. Incluez tous les noms de domaine complets marqués comme publiés dans [cet article](https://aka.ms/o365endpoints) sous la première section, en envoyant le trafic directement à votre circuit ExpressRoute.

3. Incluez tous les autres points de terminaison réseau ou règles en dessous de ces deux entrées, en envoyant le trafic vers votre proxy.

Ce tableau affiche les domaines génériques publiés sur les circuits Internet uniquement avec les sous-noms de domaine complets publiés sur les circuits ExpressRoute et Internet Azure. Pour votre fichier PAC ci-dessus, les noms de domaine complets (FQDN) de la colonne 2 du tableau ci-dessous sont répertoriés comme étant annoncés dans ExpressRoute dans le lien référencé, ce qui signifie qu’ils seront inclus dans le deuxième groupe d’entrées du fichier.

|**Domaine générique annoncé sur les circuits Internet uniquement**|**Sous-nom de domaine complet publié sur ExpressRoute et sur les circuits Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> <div style="display: inline">www.office.com</div>  <br/> |
|\*. office.net  <br/> |agent.office.net  <br/> |
|\*. office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> découverte automatique- \<tenant\> . Outlook.com  <br/> |
|\*. windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routage du trafic Office 365 sur Internet et ExpressRoute

Pour acheminer vers l’application Office 365 de votre choix, vous devez déterminer un certain nombre de facteurs clés.
  
1. La largeur de bande passante requise par l’application. L’échantillonnage de l’utilisation existante est la seule méthode fiable permettant de déterminer cela dans votre organisation.

2. Le ou les emplacements de sortie dont vous souhaitez que le trafic réseau laisse votre réseau. Nous vous recommandons de réduire la latence réseau pour la connectivité à Office 365, car cela aura un impact sur les performances. Étant donné que Skype entreprise utilise la voix et la vidéo en temps réel, la latence réseau est particulièrement médiocre.

3. Si vous souhaitez que tous ou un sous-ensemble de vos emplacements réseau exploite ExpressRoute.

4. Les emplacements auprès desquels votre fournisseur de réseau choisi offre ExpressRoute.

Une fois que vous avez déterminé les réponses à ces questions, vous pouvez mettre en service un circuit ExpressRoute qui répond aux besoins de bande passante et d’emplacement. Pour plus d’informations sur la planification réseau, reportez-vous au [Guide de réglage réseau Office 365](https://aka.ms/tune) et à l' [étude de cas sur la façon dont Microsoft gère la planification des performances réseau](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Exemple 1 : emplacement géographique unique
  
Cet exemple est un scénario pour une société fictive appelée Trey Research qui a un seul emplacement géographique.
  
Les employés de Trey Research ne sont autorisés à se connecter qu’aux services et sites Web sur Internet que le service de sécurité autorise explicitement sur les serveurs proxy sortants qui se trouvent entre le réseau d’entreprise et leur fournisseur de services Internet.
  
Trey Research prévoit d’utiliser Azure ExpressRoute pour Office 365 et reconnaît que le trafic destiné aux réseaux de distribution de contenu ne peut pas être acheminé via la connexion ExpressRoute pour Office 365. Étant donné que tout le trafic est déjà acheminé vers les périphériques proxy par défaut, ces demandes continueront à fonctionner comme auparavant. Une fois que Trey Research a déterminé qu’il peut répondre aux exigences de routage d’Azure ExpressRoute, il procède à la création d’un circuit, à la configuration du routage et à la liaison du nouveau circuit ExpressRoute à un réseau virtuel. Une fois la configuration Azure ExpressRoute fondamentale mise en place, Trey Research utilise le [fichier PAC #2 que nous publions](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) pour acheminer le trafic avec des données spécifiques du client sur les connexions ExpressRoute pour Office 365.
  
Comme indiqué dans le diagramme suivant, Trey Research est en mesure de satisfaire la nécessité d’acheminer le trafic Office 365 sur Internet et un sous-ensemble de trafic sur ExpressRoute à l’aide d’une combinaison de modifications de configuration de proxy sortant et de routage.
  
1. À l’aide du [fichier PAC #2, nous publions](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) sur le trafic de routage via un point de sortie Internet distinct pour Azure ExpressRoute pour Office 365.

2. Les clients sont configurés avec un itinéraire par défaut vers les proxies de Trey Research.

Dans cet exemple de scénario, Trey Research utilise un périphérique de proxy sortant. De même, les clients qui n’utilisent pas Azure ExpressRoute pour Office 365 peuvent souhaiter utiliser cette technique pour acheminer le trafic en fonction du coût d’inspection du trafic destiné à des points de terminaison de volume élevé connus.
  
Les noms de domaine complets de volume les plus élevés pour Exchange Online, SharePoint Online et Skype entreprise Online sont les suivants :
  
![Réseau Edge client ExpressRoute](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>. SharePoint.com, \<tenant-name\> -My.SharePoint.com, \<tenant-name\> - \<app\> . SharePoint.com

- \*. Lync.com avec les plages d’adresses IP pour le trafic non TCP

- \*broadcast.officeapps.live.com, \* Excel.officeapps.live.com, \* onenote.officeapps.live.com, \* PowerPoint.officeapps.live.com, \* view.officeapps.live.com, \* Visio.officeapps.live.com, \* Word-Edit.officeapps.live.com, \* Word-View.officeapps.live.com, Office.live.com

En savoir plus sur le [déploiement et la gestion des paramètres de proxy dans Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) et [la garantie qu’Office 365 n’est pas limité par votre proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Avec un seul circuit ExpressRoute, il n’existe pas de haute disponibilité pour Trey Research. Dans l’éventualité où la paire redondante d’appareils de périmètre de Trey qui traite la connectivité ExpressRoute échoue, il n’existe pas de circuit ExpressRoute supplémentaire vers lequel basculer. Trey Research reste dans un Predicament, car le basculement vers Internet nécessite une reconfiguration manuelle et, dans certains cas, de nouvelles adresses IP. Si Trey souhaite ajouter une haute disponibilité, la solution la plus simple consiste à ajouter des circuits ExpressRoute supplémentaires pour chaque emplacement et à configurer les circuits de manière active/active.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routage de ExpressRoute pour Office 365 avec plusieurs emplacements

Le dernier scénario, Routing Office 365 le trafic sur ExpressRoute est la base de l’architecture de routage encore plus complexe. Quel que soit le nombre d’emplacements, le nombre de continents où ces emplacements existent, le nombre de circuits ExpressRoute, et ainsi de suite, peuvent acheminer le trafic vers Internet et du trafic sur ExpressRoute sera requis.
  
Les questions supplémentaires auxquelles doivent répondre les clients disposant de plusieurs emplacements dans plusieurs régions géographiques sont les suivantes :
  
1. Avez-vous besoin d’un circuit ExpressRoute à chaque emplacement ? Si vous utilisez Skype entreprise Online ou que vous avez besoin d’une sensibilité de latence pour SharePoint Online ou Exchange Online, une paire redondante de circuits ExpressRoute actifs/actifs est recommandée à chaque emplacement. Pour plus d’informations, reportez-vous au Guide de la qualité des médias Skype entreprise et de la connectivité réseau.

2. Si un circuit ExpressRoute n’est pas disponible dans une région particulière, comment le trafic Office 365 ciblé doit-il être acheminé ?

3. Quelle est la méthode préférée pour consolider le trafic dans le cas de réseaux avec de nombreux petits emplacements ?

Chacun de ces éléments présente un défi unique qui nécessite l’évaluation de votre propre réseau, ainsi que les options disponibles auprès de Microsoft.

|**Mûre**|**Composants réseau à évaluer**|
|:-----|:-----|
|Circuits dans plusieurs emplacements  <br/> |Nous recommandons un minimum de deux circuits configurés de manière active/active.  <br/> Les besoins en termes de coûts, de latence et de bande passante doivent être comparés.  <br/> Utilisez le coût de l’itinéraire BGP, les fichiers PAC et la traduction d’adresses réseau pour gérer le routage avec plusieurs circuits.  <br/> |
|Routage à partir d’emplacements sans circuit ExpressRoute  <br/> |Nous vous recommandons de sortir de la résolution DNS et de la résolution DNS près de la personne à l’origine de la demande pour Office 365.  <br/> Le transfert DNS peut être utilisé pour permettre aux bureaux distants de découvrir le point de terminaison approprié.  <br/> Les clients du bureau distant doivent disposer d’un itinéraire permettant d’accéder au circuit ExpressRoute.  <br/> |
|Consolidation de petite entreprise  <br/> |La bande passante et l’utilisation des données disponibles doivent être soigneusement comparées.  <br/> |

> [!NOTE]
> Microsoft préfèrera ExpressRoute sur Internet si l’itinéraire est disponible quel que soit l’emplacement physique.
  
Chacune de ces considérations doit être prise en compte pour chaque réseau unique. Voici un exemple.
  
### <a name="example-2-multi-geographic-locations"></a>Exemple 2 : emplacements multigéographiques
  
Cet exemple est un scénario pour une société fictive appelée Humongous Insurance, qui comporte plusieurs emplacements géographiques.
  
Humongous Insurance est dispersé géographiquement avec des bureaux dans le monde entier. Ils souhaitent implémenter Azure ExpressRoute pour Office 365 afin de conserver la plupart de leur trafic Office 365 sur des connexions réseau directes. Humongous Insurance comporte également des bureaux sur deux continents supplémentaires. Les employés du bureau distant où ExpressRoute n’est pas réalisable doivent effectuer un routage vers l’une ou l’autre des installations principales ou les deux pour utiliser une connexion ExpressRoute.
  
Le principe de la prise en main est d’obtenir le trafic Office 365 destiné à un centre de contenu Microsoft aussi rapidement que possible. Dans cet exemple, Humongous Insurance doit décider si ses bureaux distants doivent Router sur Internet pour accéder à un centre de centre de mise en route sur n’importe quelle connexion aussi rapidement que possible ou si leurs bureaux distants doivent Router sur un réseau interne pour accéder à un centre de centre de mise en route sur une connexion ExpressRoute aussi rapidement que possible.
  
Les centres de services, les réseaux et l’architecture des applications de Microsoft sont conçus pour prendre des communications globalement disparates et les traiter de manière la plus efficace possible. Il s’agit de l’un des plus grands réseaux du monde. Les demandes destinées à Office 365 qui restent sur les réseaux clients plus long que nécessaire ne peuvent pas tirer parti de cette architecture.
  
Dans la situation de Humongous Insurance, elles doivent continuer en fonction des applications qu’elles envisagent d’utiliser sur ExpressRoute. Par exemple, s’il s’agit d’un client Skype entreprise Online ou si vous envisagez d’utiliser la connectivité ExpressRoute lors de la connexion à des réunions Skype entreprise Online externes, la conception recommandée dans le Guide de connectivité réseau et de la qualité des médias Skype entreprise Online est de mettre en service un circuit ExpressRoute supplémentaire pour le troisième emplacement. Cela peut être plus onéreux du point de vue de la mise en réseau ; Toutefois, le routage des demandes d’un continent vers un autre avant la remise à un centre de distribution Microsoft peut entraîner une expérience médiocre ou inutilisable pendant les réunions et les communications dans Skype entreprise online.
  
Si Humongous Insurance n’utilise pas ou ne prévoit pas d’utiliser Skype entreprise Online de quelque façon que ce soit, le routage du trafic réseau Office 365 vers un continent avec une connexion ExpressRoute peut être possible, mais peut entraîner une latence TCP ou non. Dans les deux cas, il est recommandé de router le trafic Internet destiné à Internet sur le site local afin de tirer parti des réseaux de distribution de contenu sur lesquels Office 365 s’appuie.
  
![ExpressRoute multi-Geography](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Lorsque Humongous Insurance prévoit sa stratégie mutualisée, il existe plusieurs éléments à prendre en compte concernant la taille du circuit, le nombre de circuits, le basculement, etc.
  
Avec ExpressRoute dans un seul emplacement avec plusieurs régions qui tentent d’utiliser le circuit, Humongous Insurance veut s’assurer que les connexions à Office 365 à partir du bureau distant sont envoyées au centre de centre de mise à niveau Office 365 le siège social le plus proche et reçus par l’emplacement du siège. Pour ce faire, Humongous Insurance met en œuvre le transfert DNS afin de réduire le nombre d’allers-retours et de recherches DNS nécessaires pour établir la connexion appropriée avec l’environnement Office 365 le plus proche du point de sortie Internet du siège. Cela empêche le client de résoudre un serveur frontal local et s’assure que le serveur frontal auquel la personne se connecte est proche du siège social où Humongous Insurance s’associe à Microsoft. Vous pouvez également apprendre à [affecter un redirecteur conditionnel à un nom de domaine](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
Dans ce scénario, le trafic provenant du bureau distant permet de résoudre l’infrastructure frontale Office 365 en Amérique du Nord et d’utiliser Office 365 pour se connecter aux serveurs principaux en fonction de l’architecture de l’application Office 365. Par exemple, Exchange Online met fin à la connexion en Amérique du Nord et les serveurs frontaux se connectent au serveur de boîtes aux lettres principal, quel que soit le client. Tous les services disposent d’un service de compartiment frontal largement réparti composé de destinations monodiffusion et anycast.
  
Si Humongous a des bureaux importants dans plusieurs continents, il est recommandé de disposer d’un minimum de deux circuits actifs/actifs par région afin de réduire la latence pour les applications sensibles telles que Skype entreprise online. Si tous les bureaux se trouvent sur un seul continent ou n’utilisent pas la collaboration en temps réel, le fait de disposer d’un point de sortie consolidé ou distribué est une décision spécifique du client. Lorsque plusieurs circuits sont disponibles, le routage BGP garantit un basculement si un seul circuit ne devient pas disponible.
  
Pour en savoir plus, consultez la rubrique Exemples de [configurations de routage](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) et [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/) .
  
## <a name="selective-routing-with-expressroute"></a>Routage sélectif avec ExpressRoute

Le routage sélectif avec ExpressRoute peut être nécessaire pour diverses raisons, telles que le test, le déploiement d’ExpressRoute vers un sous-ensemble d’utilisateurs. Il existe différents outils que les clients peuvent utiliser pour acheminer de manière sélective le trafic réseau Office 365 sur ExpressRoute :
  
1. **Routing Filtering/segreging** -autorisant les itinéraires BGP vers Office 365 via ExpressRoute vers un sous-ensemble de vos sous-réseaux ou routeurs. Cela achemine de manière sélective le segment réseau du client ou l’emplacement du Bureau physique. Cela est courant pour échelonner le déploiement de ExpressRoute pour Office 365 et est configuré sur vos périphériques BGP.

2. **Fichiers PAC/URL** : la direction du trafic réseau de l’Office 365 pour des noms de domaine complets spécifiques à acheminer sur un chemin d’accès spécifique. Cela achemine de manière sélective par ordinateur client comme identifié par le [déploiement de fichiers PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Filtrage**  -  des itinéraires Les [filtres d’itinéraires](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) permettent de consommer un sous-ensemble de services pris en charge via l’homologation Microsoft.

4. **Communautés BGP** -le filtrage basé sur les [balises communautaires BGP](https://aka.ms/bgpexpressroute365) permet à un client de déterminer les applications Office 365 qui traverseront ExpressRoute et qui transiteront sur Internet.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365](bgp-communities-in-expressroute.md)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
