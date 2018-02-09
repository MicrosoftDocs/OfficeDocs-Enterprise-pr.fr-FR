---
title: "Diagramme accessible : Intégration réseau de produits Microsoft Office Server"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Cet article est une version texte accessible du diagramme intégration réseau des produits Microsoft Office Server."
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagramme accessible : Intégration réseau de produits Microsoft Office Server

**Résumé :** Cet article est une version texte accessible du diagramme nommé réseau des produits serveur de Microsoft Office Integration.
  
Cette affiche donne une illustration générale d’un environnement réseau qui inclut Exchange Server 2013, SharePoint 2013 et Lync Server 2013. Il illustre également les éléments de mise en réseau suivantes qui sont communes à ces produits : accès interne et distant, l’authentification, le trafic client et le trafic de routage par le biais de périphériques partagés. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Concepts de haut niveau relatifs à Lync, Exchange, SharePoint Server et Office Web Apps

### <a name="about-the-design"></a>À propos de la conception

#### <a name="streamlined-network-design"></a>Conception réseau simplifiée

Cette topologie illustre un déploiement du réseau local de SharePoint 2013, Exchange Server 2013 et Lync Server 2013. Il montre également l’utilisation de la service de nuage de Microsoft, Exchange Online Protection, ce qui assure une protection de spam et les logiciels malveillants pour le trafic SMTP Simple Mail Transfer Protocol () à partir d’Internet. 
  
Cette conception réseau se résume à un ensemble minimal de fonctionnalités réseau. La conception ne prend pas en compte les fonctionnalités de sécurité et d’infrastructure supplémentaires dont certaines organisations peuvent avoir besoin.   
  
Ce schéma :  
  
- Fournit un exemple de topologie réseau illustrant le trafic entrant et le trafic sortant via un routeur passerelle, ainsi que l'équilibrage de charge du trafic (interne et externe) de la session aux différents niveaux des serveurs SharePoint, Exchange et Lync.   
    
- Illustre l'utilisation facultative de serveurs d’accès distants, comme une passerelle VPN tierce ou un serveur DirectAccess, afin de fournir une communication sécurisée aux employés itinérants ou distants.  
    
- Décrit en détail le flux du trafic SharePoint, Exchange et Lync à partir du client pour chaque niveau de serveur de plateforme.  
    
- Identifie le type de connexion d'accès distant ou interne basé sur le client (par exemple, le partenaire ou l'employé) et la méthode d'authentification utilisée.  
    
- Décompose les plates-formes SharePoint, Exchange et Lync par les rôles de serveur requis, qui identifie le serveur frontal, application, base de données et autres niveaux. 
    
L'architecture utilisée ici pour SharePoint, Lync, et Exchange ne privilégie pas une implémentation de ces plateformes. Elle ne fait que proposer un exemple, car les topologies varient selon les exigences réseau et de sécurité propres à chaque situation.  
  
#### <a name="gateway-router"></a>Routeur passerelle

Dans cette topologie, le routeur passerelle se trouve à la périphérie du réseau et achemine le trafic entrant et sortant vers et depuis l'intranet. Par ailleurs, d’autres composants, tels que plusieurs couches de pare-feu, peuvent combler l'écart entre le routeur et l'équilibrage de charge affiché. Cette topologie représente une façon parmi d’autres de déployer votre réseau. Dans cette configuration, la passerelle est configurée avec des listes de contrôle d’accès (LCA) destinées à filtrer le trafic IP entrant et sortant au niveau des interfaces du routeur. Il est possible d’utiliser les LCA, l’inspection avancée ou la traduction d'adresses réseau (NAT) sur d’autres périphériques, tels que les pare-feu, dans l'ensemble de votre réseau.  
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Périphériques d’équilibrage de charge et de proxy inverse

Vous pouvez utiliser des solutions d’équilibrage de charge matérielle ou logicielle pour rediriger le trafic pour des segments, y compris les serveurs web frontaux de SharePoint et les serveurs d’accès Client (cas) Exchange. Dans certains cas, il est souhaitable d’utiliser un équilibreur de charge matérielle de couche 7 pour les besoins de persistance, comme il peut être plus performant dans la demande, telles que les cookies et en-têtes à l’aide des informations. Toutefois, les facteurs comme le coût et l’utilisation accrue et la charge de travail à partir d’une telle solution n’est peut-être pas souhaitable pour vos besoins spécifiques. Tenez compte des points suivants pour l’équilibrage de charge sur SharePoint, Exchange et Lync : 
  
- SharePoint - pour SharePoint 2013, vous n’avez pas besoin à activer l’affinité pour les serveurs web frontaux. Normalement, ce serait utilisé pour la création de sessions persistantes et éviter plusieurs demandes d’authentification des clients sur chaque serveur web frontal. Le nouveau service de Cache distribué dans SharePoint 2013 stocke et distribue les jetons d’ouverture de session sur les serveurs web de la batterie de serveurs SharePoint. 
    
- Exchange - dans Exchange 2013, le rôle des autorités de certification est conçu pour utiliser l’équilibrage de charge de couche 4, en distribuant les requêtes au niveau de la couche de transport. Cela peut sensiblement diminuer l’utilisation de l’équilibrage de la charge et la charge de travail. 
    
- Lync - équilibrage de la charge de système de nom de domaine (DNS) est recommandée pour le trafic du protocole SIP (Session Initiation) pour les pools de Lync. (HUMIDIFICATION à HLB) d’équilibrage de charge est nécessaire pour le trafic de Lync Web (protocole HTTPS). 
    
### <a name="remote-access-options"></a>Options d'accès distant

Plusieurs options permettent de publier des ressources intranet pour les partenaires sur Internet ou de fournir un accès distant sécurisé aux employés distants ou itinérants. Il s’agit notamment des proxys inverses, de DirectAccess et des passerelles VPN tierces. Les solutions d'accès à distance décrites plus loin dans cette section sont adaptées à SharePoint, Lync et Exchange, ou à toute combinaison de ces serveurs dans un déploiement local. Toutefois, certaines options distantes peuvent ne pas fonctionner avec une solution particulière.   
  
Reverse Proxy - proxy inverse prend en charge le cryptage du trafic, telles que Secure Sockets Layer (SSL) et il que vous pouvez publier des applications intranet et ressources web authentifié utilisateurs et partenaires sur Internet. Par exemple, Microsoft Forefront Unified Access Gateway (UAG). De nombreux équilibreurs de charge matériels prennent également en charge la fonctionnalité de proxy inversé. Toutefois, il existe des scénarios toujours valides pour l’utilisation d’une solution autonome en fonction de vos besoins et exigences, telles que l’isolation du trafic cloisonnement de la sécurité et l’optimisation des performances. 
  
Atouts et avantages du proxy inverse :  
  
- Fournit un accès authentifié et sécurisé aux partenaires et utilisateurs accédant aux ressources intranet (utilisation du port TCP 443 avec le protocole SSL entre le client et le serveur proxy inverse).  
    
- Concernant Exchange, un proxy inverse, tel que Forefront UAG, fournit un mécanisme de pré-authentification avant le serveur d’accès au client Exchange. Les utilisateurs distants faisant usage d’applications publiées telles qu'Outlook Web Access (OWA) peuvent s’authentifier à l’aide des méthodes de base, NTLM ou Kerberos avant d'atteindre le réseau interne.  
    
- Concernant Exchange et SharePoint, des solutions, telles que Forefront UAG, peuvent mettre fin aux connexions SSL et diminuer la charge du serveur de ressources intranet tout en offrant un point unique de gestion des certificats.  
    
- Pour Lync, le trafic Web (HTTPS) passe par le proxy inverse (TCP 443) pour la communication client. Les serveurs proxy de proxy inverse l’HTTPS connexion à Lync Web Services, les autorités de certification Exchange et Office Web Apps. Lync Server 2013 ne prend pas en charge les UAG. 
    
DirectAccess - il s’agit d’une technologie d’accès à distance qui s’appuie sur la sécurité du protocole Internet (IPsec) pour l’authentification et le cryptage du trafic entre le client DirectAccess et le serveur. DirectAccess fournit un accès simultané aux ressources intranet et Internet pour les employés itinérants et distants sans avoir à établir une connexion. 
  
Points à prendre en compte lors de l’utilisation de DirectAccess :  
  
- DirectAccess utilise le trafic protégé IPsec (protocole 50 et 51 et UDP 500) entre le client DirectAccess et le serveur.  
    
- DirectAccess pour Windows Server 2012 et Windows 8 n’a pas besoin de déploiement PKI (infrastructure de clé publique) pour l’authentification du serveur et du client.  
    
- Nous déconseillons l’utilisation de DirectAccess avec Lync Server 2013 en raison de problèmes de latence audio et vidéo liés à IPsec et le décryptage. 
    
    Passerelle VPN - passerelles VPN standard fournissent une connexion d’accès distant dans lequel un ordinateur client d’accès distant est logiquement projeté sur l’intranet via une connexion par tunnel et initiée par l’utilisateur. Vous pouvez utiliser unifiée d’accès à distance dans Windows Server 2012 ou plusieurs solutions de tiers pour fournir un accès sécurisé à l’intranet pour les employés itinérants ou distants. VPN n’est pas recommandée pour Lync. Le trafic de Lync distant doit utiliser les serveurs Edge et tunneling fractionné. 
    
### <a name="domain-name-system-dns-considerations"></a>Considérations relatives au système DNS (Domain Name System)

Vous devez préparer le jeu d'enregistrements DNS qui permettra aux utilisateurs Internet et intranet de résoudre les noms DNS en adresses IP.  
  
- Pour les partenaires Internet et les employés itinérants ou distants, les enregistrements DNS inscrits auprès des serveurs DNS Internet fournissent une résolution à l'ensemble des adresses IP publiques correspondant au routeur passerelle, au serveur Edge de Lync, à l'ensemble des adresses IP virtuelles (VIP) sur l'équilibreur de charge et à la passerelle DirectAccess ou VPN selon vos besoins.  
    
- Pour les utilisateurs intranet, les enregistrements DNS inscrits auprès des serveurs DNS de l’intranet fournissent une résolution à l'ensemble des adresses IP virtuelles (VIP) de l'équilibreur de charge pour permettre d’accéder aux ressources Exchange, SharePoint et Lync.  
    
- Les clients DirectAccess utilisent les serveurs DNS de l’intranet pour les noms appartenant à l'espace de noms DNS de l’intranet et ils utilisent les serveurs DNS Internet pour les autres noms. Pour une utilisation plus simple de DirectAccess, vous pouvez envisager de recourir à une implémentation de DNS fractionné utilisant des espaces de noms DNS différents pour les noms intranet et les noms Internet. Par exemple, utilisez contoso.com pour les noms Internet et corp.contoso.com pour l'espace de noms intranet.  
    
- Exchange s’appuie sur un modèle DNS fractionné dans lequel la résolution de l’hôte vers l’adresse IP diffère selon que le trafic est routé dans l’espace public ou sur le réseau d’entreprise. Au minimum, vous devez disposer des enregistrements DNS pour OWA, de la découverte automatique, des URL ActiveSync pour le trafic du client et d’un enregistrement MX pour le courrier entrant.  
    
- Si vous utilisez Exchange Online Protection (EOP), votre enregistrement MX pointe vers ce service et non pas vers votre batterie de serveurs Exchange.  
    
- Pour Exchange, vous avez besoin d'une preuve de propriété de l’enregistrement TXT dans votre DNS public et d’un ID d'organisation de fédération afin de configurer le partage fédéré.  
    
- Il est possible de configurer les clients VPN d'accès à distance de sorte qu’ils utilisent uniquement des serveurs DNS intranet lorsque la connexion VPN d'accès à distance est active.  
    
### <a name="diagram-description"></a>Description du diagramme

Ce diagramme fournit un exemple de topologie réseau illustrant le trafic entrant et sortant via un routeur passerelle et l'équilibrage de charge du trafic (externe et interne) de la session du client vers les niveaux appropriés des serveurs SharePoint, Exchange et Lync. La description de ce diagramme est divisée en deux :  
  
- Description des composants figurant dans le diagramme  
    
- Description de la façon dont le trafic se déplace dans les composants vers les niveaux serveur SharePoint, Exchange, Lync et Office Web Apps.  
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Description des composants figurant dans le diagramme 

#### <a name="user-types"></a>Types d'utilisateur

Il existe quatre types d'utilisateurs, trois types externes aux services réseau et services cloud, et un type interne, qui incluent :  
  
- Sociétés partenaires (B2B), externes  
    
- Partenaires individuels (SharePoint et anonymes (Lync)), externes  
    
- Employés itinérants et distants, externes  
    
- Employés internes 
    
#### <a name="cloud-based-email-traffic"></a>Trafic de messagerie sur le cloud

Il existe un composant cloud pour le trafic de messagerie SMTP : il peut s’agir d’hôtes de messagerie Internet ou d’Exchange Online Protection.  
  
#### <a name="authentication-for-external-access"></a>Authentification pour l'accès externe

Un ensemble de procédures d'authentification régit chacun des types d’utilisateur pour Lync, SharePoint et Exchange. Ces procédures sont décrites en détail plus loin dans le présent document.  
  
#### <a name="gateway-router-with-acls"></a>Routeur passerelle avec LCA

Le routeur passerelle se trouve à la périphérie du réseau et achemine le trafic entrant et sortant vers et depuis l'intranet.  
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Serveurs d'accès distant pour Lync et SharePoint

Cette topologie comprend un serveur Edge Lync et une passerelle VPN SharePoint ou un serveur DirectAccess.  
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Équilibreur de charge et périphérique de proxy inverse

Vous pouvez utiliser des solutions d'équilibrage de charge matérielles ou logicielles afin de rediriger le trafic pour des segments comprenant les serveurs web frontaux SharePoint et les serveurs d'accès Client (CAS) Exchange. Cette topologie présente des composants VIP Lync, VIP SharePoint et VIP Exchange dans l'équilibreur de charge.  
  
#### <a name="servers"></a>Serveurs

Il existe quatre serveurs : Lync, SharePoint, Exchange et serveur de Office Web Apps. Chaque serveur peut avoir trois niveaux : frontal, couche d’accès au client, une couche application et une couche de stockage/base de données.
  
#### <a name="front-end-client-access-tier"></a>Niveau accès client frontal

Ce niveau comporte des éléments sur les quatre serveurs :  
  
- Pool Lync (frontal). Le diagramme représente deux bases de données Lync.  
    
- Serveur frontal SharePoint et cache distribué. Le diagramme représente trois bases de données SharePoint.   
    
- CAS Exchange. Le diagramme représente deux bases de données Exchange.  
    
- Serveur Office Web Apps Le diagramme représente deux bases de données Office Web Apps.  
    
#### <a name="application-tier"></a>Niveau application

Ce niveau comprend les éléments qui résident uniquement sur le serveur SharePoint :  
  
- Recherche (requête, index, administrateur). Le diagramme représente trois bases de données SharePoint.  
    
- Traitement par lots. Le diagramme représente trois bases de données SharePoint.   
    
#### <a name="databasestorage-tier"></a>Niveau stockage/base de données

Ce niveau comporte des éléments résidant sur les serveurs Exchange, SharePoint et Lync :  
  
- Base de données Lync (serveur frontal). Le diagramme représente trois bases de données Lync.  
    
- Base de données SharePoint. Le diagramme représente trois bases de données SharePoint.  
    
- Serveur de boîtes aux lettres Exchange. Le diagramme représente deux serveurs de boîtes aux lettres Exchange.  
    
Pour plus d’informations sur les composants installés sur chacun des rôles de serveur SharePoint, consultez [Les Topologies rationalisée pour SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Description du parcours du trafic dans les composants des différents niveaux serveur

Cette section décrit la façon dont les demandes utilisateur circulent dans la topologie réseau.   
  
#### <a name="authentication-and-routing-for-external-access"></a>Authentification et routage pour l'accès externe

Il existe trois types de clients externes aux services cloud et réseau, notamment :  
  
- Sociétés partenaires (B2B), externes  
    
- Partenaires individuels (SharePoint et anonymes (Lync)), externes  
    
- Employés itinérants et distants, externes  
    
Le processus d'authentification et de routage est décrit individuellement pour chaque type d'utilisateur externe.  
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Sociétés partenaires (B2B) (https://partnerweb.contoso.com)

- Lync : approbation de fédération avec d'autres organisations, Skype et connectivité PIC (Public IM Connectivity) avec AOL. Le trafic de fédération Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync.  
    
- SharePoint : Fournisseur d'identité du partenaire approuvé avec authentification SAML. Le trafic du client SharePoint passe par le routeur passerelle pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint.  
    
- Exchange : Authentification mutuelle TLS pour le trafic de messagerie, authentification SAML pour le partage fédéré. Le trafic du client Exchange passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange.  
    
- Le trafic SMTP passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange.  
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Partenaires individuels (SharePoint) et anonymes (Lync) (https://partnerweb.contoso.com et https://meet.contoso.com)

- Lync : les utilisateurs anonymes peuvent participer aux réunions Lync seulement si elles sont organisées par les employés. Le trafic de fédération Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, à l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync.   
    
- SharePoint : fournisseur d’identité du partenaire approuvé avec authentification SAML ou authentification basée sur les formulaires. Le trafic du client SharePoint passe par le routeur passerelle pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint.  
    
- Exchange : sans objet.  
    
- Le trafic web du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync.  
    
#### <a name="roaming-and-remote-employees"></a>Employés itinérants et distants

1. https://intranet.contoso.com 
    
2. https://Teams.contoso.com 
    
3. https://My.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://Mail.contoso.com * 
    
6. https://Dial.contoso.com *
    
7. https://Meet.contoso.com *
    
* L’URL de Exchange contient les répertoires virtuels suivants : service de découverte automatique, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell 
  
- Lync : authentification TLS-DSK ou NTLM. Le trafic du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, à l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), puis le serveur Lync.  
    
- SharePoint : services de domaine Active Directory, authentification basée sur les formulaires ou authentification SAML. Le trafic du client SharePoint passe par la passerelle VPN ou le serveur DirectAccess pour atteindre l’adresse IP virtuelle SharePoint (équilibreur de charge/serveur proxy inverse), puis le serveur SharePoint.  
    
- Exchange : Authentification de base sur SSL (ActiveSync, découverte automatique), authentification basée sur les formulaires (OWA). Le trafic du client Exchange passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange.  
    
- Le trafic du client Lync passe par le routeur passerelle pour atteindre le serveur Edge de Lync, l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync.  
    
#### <a name="authentication-for-internal-access"></a>Authentification pour l'accès interne

#### <a name="internal-employees"></a>Employés internes

> https://intranet.contoso.com 
    
> https://Teams.contoso.com 
    
> https://My.contoso.com
    
> https://partnerweb.contoso.com
    
> https://Mail.contoso.com * 
    
> https://Dial.contoso.com 
    
> https://Meet.contoso.com
    
> https://Admin.contoso.com
    
- Lync : authentification Kerberos, TLS-DSK ou NTLM. Le trafic du client Lync atteint l'adresse IP virtuelle Lync (serveur d’équilibrage de charge/proxy inverse), puis le serveur Lync.  
    
- SharePoint : services de domaine Active Directory, authentification basée sur les formulaires ou authentification SAML. Le trafic du client SharePoint atteint l’adresse IP virtuelle SharePoint (serveur d’équilibrage de charge/proxy inverse), puis le serveur SharePoint.  
    
- Exchange : service de domaine Active Directory, authentification basée sur les formulaires. Le trafic du client Exchange atteint l’adresse IP virtuelle Exchange (serveur d’équilibrage de charge/proxy inverse), puis le serveur Exchange.  
    
- Le trafic du client Lync atteint l'adresse IP virtuelle Lync (équilibreur de charge/serveur proxy inverse), l’équilibreur de charge matériel (requis pour le trafic HTTPS), puis le serveur Lync.  
    
#### <a name="cloud-based-email-traffic"></a>Trafic de messagerie sur le cloud

Le composant de nuage pour le trafic de messagerie SMTP se compose d’hôtes de messagerie Internet ou de Protection en ligne d’Exchange.
  
Ces composants acheminent le trafic de messagerie sur le réseau à l’aide du protocole SMTP. Le trafic passe par le routeur passerelle pour atteindre l’adresse IP virtuelle Exchange (équilibreur de charge/serveur proxy inverse), puis le serveur Exchange.  
  
### <a name="network-traffic-legend"></a>Légende relative au trafic réseau

La zone de légende représente graphiquement les différents types de trafic à l’aide de lignes de couleur comme suit :  
  
- Vert ligne : Lync SIP le trafic 
    
- Ligne bleue : Trafic web Lync  
    
- Ligne violette : Trafic du client SharePoint  
    
- Ligne orange : Trafic du client Exchange  
    
- Ligne grise : Trafic du serveur de messagerie Exchange entre le site Exchange local et Exchange Online Protection.  
    
La zone de légende contient également les descriptions des différents types de trafic et des ports que ceux-ci utilisent.  
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Trafic SIP Lync et trafic web Lync

Le serveur Edge de Lync utilise les ports suivants pour les communications utilisateur externes :   
  
- Trafic de signalisation/messagerie instantanée (SIP/SIMPLE) : Port TCP 443 (ouvert pour le trafic entrant)  
    
- Trafic de conférence web (PSOM) : TCP 443 (ouvert pour le trafic entrant)  
    
- Trafic audio/vidéo (SRTP) : TCP 443, UDP 3478 et TCP 50000-59999 (facultatif) (ouvert pour le trafic entrant et sortant)  
    
Le serveur Edge de Lync utilise les ports suivants pour les communications de fédération :   
  
- Ports TCP 5061 (SIP), 5269 (XMPP), 443 et UDP 3478 (SRTP) (ouverts pour le trafic entrant et le trafic sortant)  
    
#### <a name="sharepoint-client-traffic"></a>Trafic du client SharePoint

SharePoint peut utiliser le port TCP 443 (SSL) pour la communication chiffrée entre le client et l’équilibreur de charge. Concernant l’accès externe à partir d’Internet, ce port doit être ouvert pour le trafic entrant et sortant sur un routeur passerelle (ou un pare-feu externe).  
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Trafic du client Exchange et trafic du serveur de messagerie Exchange

Exchange utilise le port TCP 25 (SMTP) pour les communications de serveur à serveur. La plupart du trafic client (OWA, ActiveSync, Autodiscover, Outlook Anywhere) est traité sur le port 443 (HTTPS). Si vous avez des clients POP ou IMAP, les ports 110 (POP3), 995 (POP3 crypté), 143 (IMAP4), 993 (IMAP4 crypté) et 587 (SMTP) sont également utilisés pour prendre en charge ces clients. 
  
#### <a name="more-on-lync-network-traffic"></a>En savoir plus sur le trafic réseau Lync

Découvrez comment Lync Server peut aider votre entreprise à fournir une messagerie instantanée, les conférences web, partage d’application et la communication vocale. Pour plus d’informations, reportez-vous à la section [Comptabilisation de charges de travail de Microsoft Lync Server 2013 protocole](https://aka.ms/G5jzjo). 
  
Le code QR figurant dans l’affiche permet d’accéder à ces informations.  
  

