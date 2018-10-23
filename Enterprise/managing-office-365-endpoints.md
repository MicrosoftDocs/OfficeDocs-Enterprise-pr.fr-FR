---
title: Gestion des points de terminaison Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Certains réseaux d’entreprise restreindre l’accès à des emplacements internet génériques ou inclure backhaul substantielle ou traitement du trafic réseau. Pour vérifier que les ordinateurs sur des réseaux tels que ceux-ci peuvent accéder à Office 365, les administrateurs réseau et le proxy doivent gérer la liste des noms de domaine complets, URL, et les adresses IP qui constituent la liste des points de terminaison Office 365. Ces doivent figurer dans l’itinéraire direct, contournement de proxy, et/ou les règles de pare-feu et fichiers PAC afin de demandes réseau sont en mesure d’atteindre Office 365.
ms.openlocfilehash: a240e3deea512dacd70b377b3d47a7b6f49a235c
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697970"
---
# <a name="managing-office-365-endpoints"></a>Gestion des points de terminaison Office 365

La plupart des entreprises qui ont plusieurs bureaux et un connexion WAN devra doivent avoir la configuration de la connectivité réseau Office 365. Vous pouvez optimiser votre réseau par l’envoi de que tous les approuvés demandes du réseau Office 365 directement via votre pare-feu, en ignorant inspection de niveau tous les paquets supplémentaires ou traitement. Cela réduit la latence et vos besoins en capacité de périmètre. Identifier le trafic réseau de Office 365 est la première étape dans la fourniture des performances optimales pour vos utilisateurs Office 365. Pour plus d’informations sur la connectivité réseau Office 365, voir [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

Microsoft recommande que vous accéder aux points de terminaison de réseau Office 365 et les modifications apportées à l’aide de l' [adresse Office 365 et les URL des Services Web](office-365-ip-web-service.md)

Quelle que soit la manière de gérer le trafic réseau vital Office 365, Office 365 nécessite une connexion Internet. Autres points de terminaison de réseau où la connectivité est requise sont répertoriés aux [points de terminaison supplémentaires non inclus dans l’adresse Office 365 et d’un service Web de l’URL](additional-office365-ip-addresses-and-urls.md)

Comment vous utilisez les points de terminaison du réseau Office 365 dépend de votre architecture de réseau d’entreprise entreprise. Cet article décrit plusieurs façons architectures réseau d’entreprise peuvent s’intégrer avec des adresses IP de Office 365 et des URL. Pour choisir le réseau qui demande à approuver le plus simple consiste à utiliser des appareils SDWAN qui prennent en charge la configuration automatisée d’Office 365 à chacun de vos bureaux. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN de sortie succursale locale du trafic de réseau vitale Office 365

À chaque emplacement de succursale, vous pouvez fournir un périphérique SDWAN qui est configuré pour acheminer des adresses IP pour Office 365 optimiser une catégorie ou optimiser et autoriser des catégories, directement au réseau de Microsoft. Le trafic réseau, y compris le trafic du centre de données sur site, le trafic des sites web internet générique et Office 365 Default le trafic de catégorie est envoyé à un autre emplacement où vous avez un réseau de périmètre plus importante. 

Microsoft collabore avec les fournisseurs SDWAN pour activer la configuration automatique. Vous trouverez davantage d’informations sur le [Programme de partenariat du réseau d’Office 365](office-365-networking-partner-program.md)

<a name="pacfiles"> </a>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utilisation d’un fichier PAC pour le routage du trafic d’Office 365 vital direct

Fichiers PAC ou WPAD permet de gérer les demandes de réseau qui sont associés à Office 365, mais n’ont pas une adresse IP fournie. Demandes de réseau par défaut qui sont envoyées via un périphérique proxy ou périmètre provoquer latence supplémentaire. Pendant l’arrêt de SSL et inspecter entraîne la plus grande taxe, les autres services tels que la recherche de l’authentification et de la réputation de proxy peuvent entraîner une expérience utilisateur médiocre. En outre, ces appareils de réseau de périmètre besoin une capacité suffisante pour traiter toutes les demandes de connexion réseau. Nous vous recommandons de contournement de votre infrastructure de serveur proxy ou inspection pour les demandes de réseau directs Office 365.
  
[Galerie de PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) est un script PowerShell qui lit les points de terminaison réseau le plus récent à partir des services web et crée un exemple de fichier PAC. 

Une fois que vous avez téléchargé ce script, vous pouvez l’utiliser pour générer un fichier PAC. Vous pouvez également modifier le script afin qu’il s’intègre à votre gestion de fichiers PAC existante. 

![Connexion à Office 365 par le biais de pare-feu et des proxys. ](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) Figure 1 : périmètre de réseau d’entreprise Simple

Le fichier PAC est déployé sur des ordinateurs au point (1) dans la Figure 1. Lorsque vous utilisez un fichier PAC pour sortie directe du trafic de réseau vitale Office 365, vous devez également autoriser la connectivité aux adresses IP derrière ces URL sur votre pare-feu de périmètre de réseau. Cette opération est effectuée par l’extraction des adresses IP pour les catégories de point de terminaison Office 365 spécifié dans le fichier PAC et création de pare-feu ACL en fonction de ces adresses. Le pare-feu est indiqué comme point 3 dans la Figure 1. 

Séparément si vous choisissez d’uniquement routage direct pour le rediriger le trafic réseau pour les systèmes d’extrémité catégorie optimiser, n’importe quel autoriser requis catégorie des points de terminaison que vous envoyez au serveur proxy seront doivent figurer dans le serveur proxy pour contourner le traitement ultérieur. Par exemple, arrêt SSL et inspecter et l’authentification de Proxy sont incompatibles avec les systèmes d’extrémité catégorie l’optimiser et autoriser. Le serveur proxy est indiqué comme point (2) dans la Figure 1.

La configuration courante consiste à autoriser tout le trafic sortant à partir du serveur proxy, tels que les adresses IP de destination pour le trafic réseau Office 365 atteint le serveur proxy n’est pas obligatoire. En savoir plus sur les problèmes avec arrêt de SSL et inspecter [les appareils tiers réseau à l’aide](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)ou des solutions sur le trafic d’Office 365.

Il existe deux types de fichiers PAC génère le script Get-PacFile.

|**Type**|**Description**|
|:-----|:-----|
|**1** <br/> |Envoyer le trafic du point de terminaison optimiser directs et tout autre au serveur proxy. <br/> |
|**2** <br/> |Envoyer optimiser et autoriser le trafic du point de terminaison directs et tout autre au serveur proxy. Peut également être utilisé pour envoyer Qu'expressroute pris en charge pour Office 365 le trafic vers les segments réseau ExpressRoute rien au serveur proxy. <br/> |

Voici un exemple simple de l’appel du script PowerShell :

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Il existe un nombre de paramètres que vous pouvez passer au script :

|**Paramètre**|**Description**|
|:-----|:-----|
|**ClientRequestId** <br/> |Ce paramètre est obligatoire et est un GUID transmis au service web qui représente l’origine de l’appel de l’ordinateur client <br/> |
|**Instance** <br/> |L’instance du service Office 365 par défaut dans le monde entier. Également transmises au service web <br/> |
|**TenantName** <br/> |Nom de votre client Office 365. Transmises au service web et utilisé comme un paramètre remplaçable dans certaines URL de 365 Office <br/> |
|**Type (Type)** <br/> |Le type du fichier que vous souhaitez générer le proxy PAC <br/> |

Voici un autre exemple d’appel du script PowerShell avec des paramètres supplémentaires :

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Traitement du trafic réseau de Office 365 de contournement du serveur proxy 

Où les fichiers PAC ne sont pas utilisées pour diriger le trafic sortant, vous devez toujours contourner le traitement sur votre réseau de périmètre à la configuration de votre serveur proxy. Certains fournisseurs de serveurs proxy ont activé la configuration automatique de ce comme décrit dans le [Programme de partenariat du réseau d’Office 365](office-365-networking-partner-program.md). Si vous effectuez cette opération manuellement, vous devrez obtenir l’optimiser et autoriser des données du point de terminaison de catégorie du point de terminaison à partir de l’adresse Office 365 et l’URL des Services Web et configurer votre serveur proxy pour contourner le traitement de ces. Il est important éviter l’arrêt de SSL et inspecter et l’authentification de Proxy pour l’optimisation et autoriser des points de terminaison de catégorie. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gestion des modifications des URL et des adresses IP Office 365

En plus de la sélection d’une configuration appropriée pour votre réseau de périmètre, il est essentiel d’adopter un processus de gestion des changements de points de terminaison Office 365. Changent régulièrement de ces points de terminaison et si vous ne gérez pas les modifications que vous pouvez vous retrouver avec des utilisateurs bloqués ou avec des performances médiocres après une nouvelle adresse IP adresse ou l’URL est ajoutée. 

Modifications pour les adresses IP de Office 365 et les URL sont généralement publiées vers le dernier jour du mois. Parfois une modification sera publiée en dehors de cette planification en raison de fonctionnement, prise en charge ou en matière de sécurité.

Lorsqu’une modification est publiée qui vous oblige à effectuer une action, car une adresse IP ou l’URL a été ajouté, vous devriez recevoir des avis de 30 jours à partir de la publication de nous la modification jusqu'à ce que le service Office 365 live est sur ce point de terminaison. Bien que Microsoft vise pendant cette notification, il peut être pas toujours possible en raison de fonctionnement, prise en charge ou en matière de sécurité. Les modifications qui ne nécessitent pas d’action immédiate pour maintenir la connectivité, telles que supprimer des URL ou des adresses IP ou moins de changements significatifs, n’incluent pas de notification préalable. Quel type de notification est fourni, indépendamment de la date active service attendue pour chaque modification sont répertoriés.

### <a name="change-notification-using-web-services"></a>Notification des modifications à l’aide des services web

Vous pouvez utiliser l’adresse de IP Office 365 et notification de modification des URL des Services Web à obtenir. Nous vous recommandons de que vous appelez la méthode web/version une fois par heure pour vérifier la version des points de terminaison que vous utilisez pour vous connecter à Office 365. Si cette version est modifiée par rapport à la version que vous avez utilisé, vous devez obtenir les données de point de terminaison le plus récent à partir de la /endpoints méthode web et éventuellement obtenir les différences dans les /changes à la méthode web. Il n’est pas nécessaire d’appeler les méthodes web /endpoints ou /changes s’il y n'a pas été toute modification apportée à la version que vous avez trouvé. 

Pour plus d’informations, voir [Office 365 adresse et le service Web de l’URL](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notification des modifications à l’aide de flux RSS

Les URL des Services Web Office 365 adresse fournissent qu'un flux RSS que vous pouvez vous abonner à dans Outlook. Il existe des liens vers les URL RSS sur chacune des pages spécifiques Office 365 service instance pour les adresses IP et des URL. Le flux RSS est décrit plus loin dans [Office 365 adresse et le service Web de l’URL](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Notification de modification et d’approbation consulter à l’aide de Microsoft Flow

Nous savons que vous pouvez nécessiter toujours le traitement manuel des modifications de point de terminaison de réseau fournis par le biais de chaque mois. Vous pouvez utiliser Microsoft Flow pour créer un flux qui vous avertit par courrier électronique et éventuellement s’exécute un processus d’approbation des modifications lorsque les points de terminaison Office 365 réseau comportent des modifications. Une fois la révision terminée, vous pouvez avoir le flux de messagerie automatiquement les modifications apportées à votre équipe de gestion de serveur proxy et les pare-feu. 

En savoir plus sur l’exemple Microsoft Flow et le modèle à [Utiliser Microsoft flux pour recevoir un message électronique pour les modifications apportées à des adresses IP Office 365 et URL](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Points de terminaison Office 365 réseau FAQ

Questions fréquemment posées un administrateur sur la connectivité Office 365 :
  
### <a name="how-do-i-submit-a-question"></a>Comment soumettre une question ?

Cliquez sur le lien en bas pour indiquer si l’article a été utile ou non et soumettre des questions supplémentaires. Nous surveiller les commentaires et mettre à jour les questions fréquemment posées.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Comment déterminer l’emplacement de mon client ?

 **Emplacement du client** est déterminé mieux à l’aide de notre [mappage du centre de données](http://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Est-ce que je homologue correctement avec Microsoft ?

 **Emplacements Peering** sont décrites plus en détail dans [homologue avec Microsoft](https://www.microsoft.com/peering).
  
Avec plus de 2500 relations homologation de fournisseur de services Internet global et 70 points de présence, prise en main de votre réseau de notre doit être transparente. Il ne peut pas nuire à quelques minutes assurant la que relation d’homologation votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de bonnes et pas homologation livraisons à notre réseau. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Je vois des demandes du réseau pour les adresses IP pas sur la liste publiée, ai-je besoin pour fournir leur accès ?
<a name="bkmk_MissingIP"> </a>

Nous fournissons uniquement des adresses IP pour les serveurs Office 365 vers que vous devez acheminer directement. Ce n’est pas une liste complète de toutes les adresses IP que vous verrez demandes réseau. Vous verrez les demandes réseau Microsoft et de tiers détenus, non publiés, les adresses IP. Ces adresses IP sont dynamiquement générés ou gérés d’une manière qui empêche l’avis de temps lorsqu’ils sont modifiés. Si votre pare-feu ne peut pas autoriser l’accès basé sur les noms de domaines complets pour ces demandes réseau, utilisez un fichier PAC ou WPAD pour gérer les demandes.
  
Voir qu'une adresse IP associée à Office 365 que vous souhaitez plus d’informations ?
  
1. Vérifier si l’adresse IP est incluse dans un plus grand nombre de publié à l’aide d’une [Calculatrice CIDR](http://jodies.de/ipcalc).
2. Voir si un partenaire possède l’adresse IP avec une [requête whois](https://dnsquery.org/). S’il est propriété de Microsoft, il peut être un partenaire interne.
3. Vérifier le certificat, dans un navigateur se connecter à l’adresse IP à l’aide *HTTPS://\<adresse_IP\> * , vérifiez les domaines répertoriés dans le certificat de comprendre quels domaines associés avec l’adresse IP. S’il est Microsoft appartient l’adresse IP et pas dans la liste d’adresses IP de Office 365, il est probable que l’adresse IP associée à un CDN Microsoft tels que *MSOCDN.NET* ou un autre domaine Microsoft sans informations IP publiées. Si vous ne trouvez pas que le domaine sur le certificat est un où nous revendication à l’adresse IP, n’hésitez pas.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Je reçois des noms tels que nsatc.net ou akadns.net dans les noms de domaine Microsoft
<a name="bkmk_akamai"> </a>

Office 365 et autres services Microsoft utilisent plusieurs services de tiers tels que Akamai et MarkMonitor pour améliorer votre expérience avec Office 365. Pour conserver en donnant la meilleure expérience possible, nous pouvons modifier ces services à l’avenir. Ce faisant, nous publier souvent l’enregistrement CNAME qui pointe vers une tierce partie domaine détenu, un enregistrement ou l’adresse IP. Domaines de tiers peuvent héberger le contenu, comme un CDN, ou ils peuvent héberger un service, comme un service de gestion du trafic géographique. Lorsque vous voyez les connexions à des tiers, il se trouve sous la forme d’une redirection ou référence, pas une demande initiale à partir du client. Certains clients doivent s’assurer de cette forme de redirection et la redirection est autorisée à passer sans ajouter explicitement que la longue liste des services de tiers de noms de domaine complets potentiels peut utiliser.
  
La liste des services sujette à modification à tout moment. Les services en cours d’utilisation sont les suivantes :
  
[MarkMonitor](https://www.markmonitor.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent * \*. nsatc.net* . Ce service fournit la protection des noms de domaine et de surveillance pour vous protéger contre les comportements malveillants.
  
[ExactTarget](https://www.marketingcloud.com/) est en cours d’utilisation lorsque vous voyez les demandes à * \*. exacttarget.com* . Ce service fournit la gestion de liens de messagerie et de surveillance par rapport à un comportement malveillant.
  
[Akamai](https://www.akamai.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent un des noms de domaines complets suivants. Ce service offre géo-DNS et les services de réseau de distribution de contenu.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Disposer la connectivité minimale possible pour Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 est un ensemble de services intégrés à la fonction via internet, les fiabilité et disponibilité promesses basés sur de nombreux services internet standard disponibles. Par exemple, les services internet standard tels que DNS, révocation de certificats et CDN doivent être accessibles à utiliser Office 365 comme ils ne doivent être accessibles à utiliser les services internet plus modernes.

La suite Office 365 est divisée en zones principales de service. Ces peuvent être activés de manière sélective pour la connectivité et une zone commune qui est une dépendance pour tous les et est toujours requis.

|**Zone de service**|**Description**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online et Exchange Online Protection <br/> |
|**SharePoint** <br/> |Sharepoint Online et OneDrive Entreprise <br/> |
|**Skype** <br/> |Skype pour les professionnels et les équipes Microsoft <br/> |
|**Courantes** <br/> |Office 365 Pro Plus, Office Online, Azure AD et autres points de terminaison réseau courantes <br/> |

En plus des services de base internet, il existe des services tiers qui ne sont utilisées pour intégrer les fonctionnalités. Alors que ceux-ci sont nécessaires pour l’intégration, ils sont marqués comme étant facultatifs dans l’article de points de terminaison Office 365 qui signifie que les fonctionnalités principales du service continuera de fonctionner, si le point de terminaison n’est pas accessible. Un point de terminaison de réseau qui est requis aura obligatoire attribut défini sur true. Un point de terminaison réseau facultatif auront l’attribut required est définie sur false et l’attribut notes décrit en détail la fonctionnalité manquante, que vous pouvez être confronté si la connectivité est bloquée.
  
Si vous tentez d’utiliser Office 365 et estiment services tiers ne sont pas accessibles, vous souhaiterez afin de [tous les noms de domaine complets marqués obligatoire ou facultatif dans cet article sont autorisées via le pare-feu et de proxy](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Comment bloquer les accès aux services de consommateur de Microsoft ?
<a name="bkmk_consumer"> </a>

Restriction de l’accès à nos services consommateur doit être effectuée à vos propres risques, l’uniquement fiable pour bloquer consommateur services consiste à restreindre l’accès à la *login.live.com* le nom de domaine complet. Ce nom de domaine complet est utilisé par un large éventail de services, notamment les services non consommateur comme MSDN, TechNet et d’autres personnes. Restriction de l’accès à ce nom de domaine complet peut entraîner le besoin d’inclure également des exceptions à la règle pour les demandes réseau associés à ces services.
  
N’oubliez pas de blocage de l’accès aux services Microsoft consommateur uniquement ne sont pas empêcher la possibilité d’une personne de votre réseau aux informations exfiltrate à l’aide d’un client Office 365 ou un autre service.
  
## <a name="related-topics"></a>Rubriques connexes

[Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md)

[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Exigences relatives à l’infrastructure réseau pour Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute et power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)
