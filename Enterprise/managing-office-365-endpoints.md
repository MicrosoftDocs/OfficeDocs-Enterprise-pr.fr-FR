---
title: Gestion des points de terminaison Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Certains réseaux d’entreprise restreignent l’accès aux emplacements Internet génériques ou incluent une déformation ou un traitement substantiel du trafic réseau. Pour s’assurer que les ordinateurs sur des réseaux comme ceux-ci peuvent accéder à Office 365, les administrateurs réseau et proxy doivent gérer la liste des noms de domaine complets, des URL et des adresses IP qui composent la liste des points de terminaison Office 365. Ceux-ci doivent être ajoutés à l’itinéraire direct, à la déviation du proxy et/ou aux règles de pare-feu et/ou aux fichiers PAC pour s’assurer que les demandes réseau sont en mesure d’atteindre Office 365.
ms.openlocfilehash: 1a694d516a81fec7d6c619c17414e2245dd6b0ef
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030608"
---
# <a name="managing-office-365-endpoints"></a>Gestion des points de terminaison Office 365

La plupart des organisations d’entreprise disposant de plusieurs emplacements de bureau et d’un réseau étendu de connexion doivent avoir besoin d’une configuration pour la connectivité réseau Office 365. Vous pouvez optimiser votre réseau en envoyant toutes les demandes réseau Office 365 approuvées directement via votre pare-feu, en contournant toute inspection ou traitement supplémentaire au niveau des paquets. Cela réduit la latence et les besoins en matière de capacité de périmètre. L’identification du trafic réseau Office 365 est la première étape pour fournir des performances optimales pour vos utilisateurs. Pour plus d’informations sur la connectivité réseau Office 365, consultez la rubrique [office 365 Network Connectivity principes](office-365-network-connectivity-principles.md).

Microsoft vous recommande d’accéder aux points de terminaison réseau Office 365 et de les modifier à l’aide de l' [adresse IP office 365 et du service Web d’URL](office-365-ip-web-service.md).

Quelle que soit la façon dont vous gérez le trafic réseau Office 365 vital, Office 365 nécessite une connectivité Internet. Les autres points de terminaison réseau pour lesquels la connectivité est requise sont répertoriés aux [points de terminaison supplémentaires non inclus dans le service Web d’URL et d’adresse IP Office 365](additional-office365-ip-addresses-and-urls.md).

La manière dont vous utilisez les points de terminaison réseau Office 365 dépendra de l’architecture réseau de votre organisation d’entreprise. Cet article décrit plusieurs méthodes d’intégration des architectures réseau d’entreprise aux adresses IP et aux URL Office 365. Le moyen le plus simple de choisir les demandes réseau à approuver est d’utiliser des appareils SDWAN qui prennent en charge la configuration automatisée d’Office 365 à chaque emplacement de votre bureau.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN pour la sortie de succursale locale du trafic réseau vital d’Office 365

À chaque emplacement de succursale, vous pouvez fournir un appareil SDWAN configuré pour acheminer le trafic pour Office 365 optimiser la catégorie de points de terminaison, ou pour optimiser et autoriser les catégories, directement vers le réseau Microsoft. Tout autre trafic réseau, y compris le trafic de centre de contenu local, le trafic de sites Web Internet généraux et le trafic vers les points de terminaison de catégorie par défaut d’Office 365, est envoyé à un autre emplacement où vous disposez d’un périmètre réseau plus substantiel.

Microsoft travaille avec des fournisseurs SDWAN pour activer la configuration automatisée. Pour plus d’informations, consultez la rubrique [Office 365 Networking Partner Program](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utiliser un fichier PAC pour le routage direct du trafic Office 365 vital

Utilisez des fichiers PAC ou WPAD pour gérer les demandes réseau qui sont associées à Office 365, mais qui n’ont pas d’adresse IP. Les requêtes réseau classiques envoyées via un proxy ou un périphérique de périmètre augmentent la latence. Tandis que l’interruption et l’inspection SSL créent la plus grande latence, d’autres services, tels que l’authentification proxy et la recherche de réputation, peuvent entraîner une baisse des performances et une expérience utilisateur incorrecte. En outre, ces périphériques de réseau de périmètre ont besoin d’une capacité suffisante pour traiter toutes les demandes de connexion réseau. Nous vous recommandons de contourner votre proxy ou vos appareils d’inspection pour les demandes réseau directes Office 365.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) est un script PowerShell qui lit les derniers points de terminaison réseau à partir de l’adresse IP et du service Web d’URL Office 365 et crée un exemple de fichier PAC. Vous pouvez modifier le script de sorte qu’il s’intègre à votre gestion de fichiers PAC existante.

![Connexion à Office 365 via des pare-feu et des proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figure 1 : périmètre de réseau d’entreprise simple**

Le fichier PAC est déployé sur les navigateurs Web au point 1 de la figure 1. Lors de l’utilisation d’un fichier PAC pour la sortie directe du trafic réseau Office 365 vital, vous devez également autoriser la connectivité aux adresses IP situées derrière ces URL sur votre pare-feu de périmètre réseau. Cette opération est effectuée en extrayant les adresses IP pour les mêmes catégories de points de terminaison Office 365 que celles spécifiées dans le fichier PAC et en créant des listes de Contrã’le d’accès de pare-feu basées sur ces adresses. Le pare-feu est le point 3 de la figure 1.

Séparément si vous choisissez uniquement le routage direct pour les points de terminaison de catégorie Optimize, tous les points de terminaison de catégorie requis que vous envoyez au serveur proxy doivent être affichés sur le serveur proxy pour éviter tout traitement supplémentaire. Par exemple, l’interruption et l’inspection de SSL et l’authentification proxy sont incompatibles avec les points de terminaison Optimize et allow Category. Le serveur proxy est le point 2 de la figure 1.

La configuration courante consiste à autoriser sans traiter tout le trafic sortant à partir du serveur proxy pour les adresses IP de destination pour le trafic réseau Office 365 qui accède au serveur proxy. Pour plus d’informations sur les problèmes liés au protocole SSL Break and Inspect, consultez la rubrique [utilisation de périphériques ou de solutions réseau tiers sur le trafic Office 365](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Il existe deux types de fichiers PAC que le script Get-PacFile générera.

|**Type**|**Description**|
|:-----|:-----|
|**0,1** <br/> |Envoyez l’optimisation du trafic du point de terminaison direct et de tous les autres éléments au serveur proxy. <br/> |
|**n°2** <br/> |Envoyez l’optimisation et autorisez le trafic du point de terminaison direct et tout le reste sur le serveur proxy. Ce type peut également être utilisé pour envoyer toutes les ExpressRoute prises en charge pour le trafic Office 365 vers des segments réseau ExpressRoute et tout le reste vers le serveur proxy. <br/> |

Voici un exemple simple d’appel du script PowerShell :

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Vous pouvez transmettre un certain nombre de paramètres au script :

|**Paramètre**|**Description**|
|:-----|:-----|
|**ClientRequestId** <br/> |Ceci est obligatoire et est un GUID transmis au service Web qui représente l’ordinateur client effectuant l’appel. <br/> |
|**Instance** <br/> |L’instance de service Office 365 qui est par défaut dans le monde entier. Également transmis au service Web. <br/> |
|**TenantName** <br/> |Votre nom de client Office 365. Transmis au service Web et utilisé comme paramètre remplaçable dans certaines URL d’Office 365. <br/> |
|**Type** <br/> |Type du fichier PAC de proxy à générer. <br/> |

Voici un autre exemple d’appel du script PowerShell avec des paramètres supplémentaires :

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Traitement de proxy de serveur proxy du trafic réseau Office 365

Lorsque les fichiers PAC ne sont pas utilisés pour le trafic sortant direct, vous voulez tout de même contourner le traitement sur votre périmètre réseau en configurant votre serveur proxy. Certains fournisseurs de serveurs proxy ont activé la configuration automatisée de cet exemple, comme décrit dans le [programme de partenariat de mise en réseau Office 365](office-365-networking-partner-program.md).

Si vous effectuez cette opération manuellement, vous devrez obtenir les données de catégorie optimiser et autoriser le point de terminaison à partir de l’adresse IP et du service Web d’URL Office 365 et configurer votre serveur proxy pour qu’il contourne le traitement de ces éléments. Il est important d’éviter l’interruption de SSL et l’authentification par proxy pour les points de terminaison Optimize et allow Category.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gestion des modifications pour les adresses IP et les URL Office 365

En plus de sélectionner la configuration appropriée pour votre périmètre réseau, il est essentiel d’adopter un processus de gestion des modifications pour les points de terminaison Office 365. Ces points de terminaison changent régulièrement et si vous ne gérez pas les modifications, vous pouvez vous terminer avec des utilisateurs bloqués ou avec des performances médiocres après l’ajout d’une nouvelle adresse IP ou d’une nouvelle URL.

Les modifications apportées aux adresses IP et aux URL Office 365 sont généralement publiées vers le dernier jour de chaque mois. Parfois, une modification sera publiée en dehors de cette planification en raison des exigences opérationnelles, de support ou de sécurité.

Lors de la publication d’une modification qui nécessite l’exécution d’une adresse IP ou d’une URL, vous devriez recevoir un préavis de 30 jours à partir du moment où nous publions la modification jusqu’à ce qu’il y ait un service Office 365 sur ce point de terminaison. Bien que nous cherchions à cette période de notification, il se peut que cela ne soit pas toujours possible en raison des exigences opérationnelles, de support ou de sécurité. Les modifications qui ne nécessitent pas d’action immédiate pour maintenir la connectivité, telles que les adresses IP ou les URL supprimées, ou des modifications moins importantes, n’incluent pas de notification préalable. Quelle que soit la notification fournie, nous répertorions la date de service Active attendue pour chaque modification.

### <a name="change-notification-using-the-web-service"></a>Modifier la notification à l’aide du service Web

Vous pouvez utiliser l’adresse IP et le service Web d’URL Office 365 pour obtenir des notifications de modification. Nous vous recommandons d’appeler la méthode Web **/version** une fois par heure pour vérifier la version des points de terminaison que vous utilisez pour vous connecter à Office 365. Si cette version change par rapport à la version que vous utilisez, vous devez obtenir les données de point de terminaison les plus récentes à partir de la méthode Web **/Endpoints** et éventuellement obtenir les différences à partir de la méthode Web **/changes** . Il n’est pas nécessaire d’appeler les méthodes Web **/Endpoints** ou **/changes** si aucune modification n’a été apportée à la version que vous avez trouvée.

Pour plus d’informations, consultez la rubrique [Office 365 IP address and URL Web service](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Modifier la notification à l’aide de flux RSS

Le service Web d’URL et d’adresses IP Office 365 fournit un flux RSS auquel vous pouvez vous abonner dans Outlook. Il existe des liens vers les URL RSS sur chacune des pages spécifiques de l’instance du service Office 365 pour les adresses IP et les URL. Pour plus d’informations, consultez la rubrique [Office 365 IP address and URL Web service](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Modification de la notification et de l’approbation à l’aide de Microsoft Flow

Nous comprenons qu’il est possible que vous deviez toujours traiter manuellement les modifications apportées au point de terminaison réseau par mois. Vous pouvez utiliser Microsoft Flow pour créer un flux qui vous avertit par courrier électronique et exécute éventuellement un processus d’approbation pour les modifications lorsque les points de terminaison réseau Office 365 ont des modifications. Une fois la révision terminée, vous pouvez faire en sorte que les modifications soient automatiquement envoyées par courrier électronique à l’équipe de gestion de votre pare-feu et de votre serveur proxy.

Pour plus d’informations sur un modèle et un exemple de flux Microsoft, voir [utiliser Microsoft Flow pour recevoir un courrier électronique pour les modifications apportées aux adresses IP et aux URL Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>FAQ sur les points de terminaison réseau Office 365

Questions d’administration fréquemment posées sur la connectivité Office 365 :
  
### <a name="how-do-i-submit-a-question"></a>Comment puis-je soumettre une question ?

Cliquez sur le lien situé en bas pour indiquer si l’article a été utile ou non et envoyez des questions supplémentaires. Nous Surveillez les commentaires et mettez à jour les questions ici en suivant les réponses les plus fréquentes.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Comment puis-je déterminer l’emplacement de mon client ?

 L' **emplacement client** est le mieux déterminé à l’aide de notre [carte de centre](https://aka.ms/datamaps)de contenu.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Est-ce que je m’appaire correctement avec Microsoft ?

 Les **emplacements d’homologation** sont décrits de manière plus détaillée dans la rubrique [peering with Microsoft](https://www.microsoft.com/peering).
  
Avec plus de 2500 les relations d’homologation ISP globales et 70 points de présence, l’obtention de votre réseau vers le nôtre doit être transparente. Il n’est pas judicieux de consacrer quelques minutes à la façon de s’assurer que la relation d’homologation de votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) de bons et pas de bonnes relations d’homologation à notre réseau.
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Je vois des demandes réseau à des adresses IP qui ne se trouvent pas dans la liste publiée, dois-je fournir un accès à ces adresses ?
<a name="bkmk_MissingIP"> </a>

Nous fournissons uniquement des adresses IP pour les serveurs Office 365 que vous devez acheminer directement vers. Il ne s’agit pas d’une liste complète de toutes les adresses IP pour lesquelles vous verrez des demandes réseau. Vous verrez des demandes réseau à Microsoft et à des adresses IP tierces, non publiées. Ces adresses IP sont générées dynamiquement ou gérées d’une manière qui empêche la notification en temps opportun. Si votre pare-feu ne peut pas autoriser l’accès basé sur les noms de domaine complets pour ces demandes réseau, utilisez un fichier PAC ou WPAD pour gérer les demandes.
  
Voir une adresse IP associée à Office 365 sur laquelle vous souhaitez plus d’informations.
  
1. Vérifiez si l’adresse IP est incluse dans une plage publiée plus grande à l’aide d’une [calculatrice CIDR](https://jodies.de/ipcalc).
2. Voir si un partenaire possède la IP avec une [requête Whois](https://dnsquery.org/). S’il est détenu par Microsoft, il peut s’agir d’un partenaire interne.
3. Vérifiez le certificat, dans un navigateur Connectez-vous à l’adresse IP à l’aide de *https://\<IP_ADDRESS\> * , vérifiez les domaines répertoriés sur le certificat pour comprendre quels domaines sont associés à l’adresse IP. S’il s’agit d’une adresse IP appartenant à Microsoft et non sur la liste des adresses IP Office 365, l’adresse IP est probablement associée à un CDN Microsoft tel que *MSOCDN.net* ou un autre domaine Microsoft sans informations IP publiées. Si vous trouvez le domaine sur le certificat est un domaine dans lequel nous revendiquons de répertorier l’adresse IP, veuillez nous le faire savoir.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Certaines URL Office 365 pointent vers des enregistrements CNAMe au lieu d’un enregistrement dans le DNS. Que dois-je faire avec les enregistrements CNAMe ?

Les ordinateurs clients ont besoin d’un enregistrement DNS A ou AAAA qui inclut une ou plusieurs adresses IP pour se connecter à un service Cloud. Certaines URL incluses dans Office 365 affichent des enregistrements CNAMe au lieu des enregistrements A ou AAAA. Ces enregistrements CNAMe sont intermédiaires et il peut y en avoir plusieurs dans une chaîne. Elles sont toujours résolues en un enregistrement A ou AAAA pour une adresse IP. Par exemple, considérez la série d’enregistrements DNS suivante, qui est résolue en adresse IP _IP_1_:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Ces redirections CNAMe sont une partie normale du DNS et sont transparentes pour l’ordinateur client et sont transparentes pour les serveurs proxy. Elles sont utilisées pour l’équilibrage de charge, les réseaux de distribution de contenu, la haute disponibilité et la minimisation des incidents de service. Microsoft ne publie pas les enregistrements CNAMe d’intermédiaires, ils sont susceptibles d’être modifiés à tout moment, et vous n’avez pas besoin de les configurer comme autorisés dans votre serveur proxy.

Un serveur proxy valide l’URL initiale qui, dans l’exemple ci-dessus, est serviceA.office.com et cette URL serait incluse dans Office 365 Publishing. Le serveur proxy demande la résolution DNS de cette URL à une adresse IP et reçoit IP_1. Il ne valide pas les enregistrements de redirection CNAMe CNAMe.

Les configurations codées en dur ou la fonctionnalité de liste de domaines autorisées basée sur les noms de domaine complets Office 365 indirects ne sont pas recommandées par Microsoft et sont connues comme entraînant des problèmes de connectivité client. Les solutions DNS qui bloquent sur la redirection CNAMe, ou qui résolvent les entrées DNS Office 365 de manière incorrecte, peuvent être résolues via le transfert conditionnel DNS (étendu aux noms de domaine complets Office 365) avec la récursivité DNS activée. De nombreux produits de périmètre réseau tiers intègrent en mode natif la liste de point de terminaison 365 Office dans leur configuration à l’aide de l' [adresse IP office 365 et du service Web d’URL](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Pourquoi est-ce que je vois des noms tels que nsatc.net ou akadns.net dans les noms de domaine Microsoft ?
<a name="bkmk_akamai"> </a>

Office 365 et d’autres services Microsoft utilisent plusieurs services tiers tels que Akamai et MarkMonitor pour améliorer votre expérience Office 365. Pour vous assurer de la meilleure expérience possible, nous pouvons modifier ces services à l’avenir. Les domaines tiers peuvent héberger du contenu, tel qu’un CDN, ou ils peuvent héberger un service, tel qu’un service de gestion du trafic géographique. Voici quelques-uns des services actuellement utilisés :
  
[MarkMonitor](https://www.markmonitor.com/) est en cours d’utilisation lorsque vous voyez des requêtes qui incluent * \*. nsatc.net* . Ce service assure la protection des noms de domaine et la surveillance contre les comportements malveillants.
  
[ExactTarget](https://www.marketingcloud.com/) est en cours d’utilisation lorsque vous voyez des demandes à * \*. ExactTarget.com* . Ce service fournit la gestion des liens de messagerie et la surveillance contre les comportements malveillants.
  
[Akamai](https://www.akamai.com/) est utilisé lorsque vous voyez des demandes qui incluent l’un des noms de domaine complets suivants. Ce service offre des services réseau de distribution de contenu et DNS.
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Je dois disposer de la connectivité minimale pour Office 365
<a name="bkmk_thirdparty"> </a>

Comme Office 365 est une suite de services conçue pour fonctionner sur Internet, les promesses de fiabilité et de disponibilité sont basées sur de nombreux services Internet standard disponibles. Par exemple, les services Internet standard, tels que DNS, la liste de révocation de certificats et CDN doivent être accessibles pour utiliser Office 365, tout comme ils doivent être accessibles pour utiliser les services Internet modernes les plus récents.

La suite Office 365 est divisée en domaines de service principaux. Ces éléments peuvent être activés de manière sélective pour la connectivité et il existe un domaine commun qui est une dépendance de tous et est toujours obligatoire.

|**Zone de service**|**Description**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online et Exchange Online Protection <br/> |
|**SharePoint** <br/> |Sharepoint Online et OneDrive Entreprise <br/> |
|**Skype Entreprise Online et Microsoft Teams** <br/> |Skype entreprise et Microsoft teams <br/> |
|**Courant** <br/> |Office 365 Pro plus, Office dans un navigateur, Azure AD et d’autres points de terminaison réseau courants <br/> |

En plus des services Internet de base, il existe des services tiers qui sont uniquement utilisés pour intégrer les fonctionnalités. Bien que ces éléments soient nécessaires à l’intégration, ils sont marqués comme étant facultatifs dans l’article relatif aux points de terminaison Office 365, ce qui signifie que les fonctionnalités de base du service continueront à fonctionner si le point de terminaison n’est pas accessible. Tout point de terminaison réseau requis aura l’attribut required défini sur true. Tout point de terminaison réseau facultatif aura l’attribut required défini sur false et l’attribut notes détaillera la fonctionnalité manquante dont vous devez vous attendre si la connectivité est bloquée.
  
Si vous essayez d’utiliser Office 365 et que vous ne pouvez pas accéder aux services tiers, vous devez vous [assurer que tous les noms de domaine complets marqués comme obligatoires ou facultatifs dans cet article sont autorisés via le proxy et le pare-feu](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Comment bloquer l’accès aux services grand public de Microsoft ?
<a name="bkmk_consumer"> </a>

La restriction de l’accès à nos services grand public doit être réalisée à vos propres risques. La seule façon fiable de bloquer les services grand public est de restreindre l’accès au nom de domaine complet *login.live.com* . Ce nom de domaine complet est utilisé par un large éventail de services, y compris des services non consommateurs tels que MSDN, TechNet, etc. Ce nom de domaine complet est également utilisé par le programme d’échange de fichiers sécurisé de Microsoft et est nécessaire pour transférer des fichiers afin de faciliter la résolution des problèmes pour les produits Microsoft.  La limitation de l’accès à ce nom de domaine complet peut entraîner l’ajout d’exceptions à la règle pour les demandes réseau associées à ces services.
  
N’oubliez pas que le blocage de l’accès aux services de grand public de Microsoft n’empêchera pas la possibilité pour un utilisateur de votre réseau d’exfiltrer les informations à l’aide d’un client Office 365 ou d’un autre service.
  
## <a name="related-topics"></a>Rubriques connexes

[Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md)

[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Configuration requise de l’infrastructure réseau pour Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute et Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)
