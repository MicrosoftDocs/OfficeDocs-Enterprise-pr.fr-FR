---
title: Principes de connectivité réseau Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Avant de commencer la planification de votre réseau Office 365 la connectivité réseau, il est important de comprendre les principes de connectivité de gérer en toute sécurité le trafic d’Office 365 et d’obtenir les meilleures performances possibles. Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau.
ms.openlocfilehash: d319d99cdd413fe1df9e8f88d18742ad464bbb3b
ms.sourcegitcommit: f0ba0d8c62f802447bc9d07f5d877067156fbed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "28021805"
---
# <a name="office-365-network-connectivity-principles"></a>Principes de connectivité réseau Office 365

Avant de commencer la planification de votre réseau Office 365 la connectivité réseau, il est important de comprendre les principes de connectivité de gérer en toute sécurité le trafic d’Office 365 et d’obtenir les meilleures performances possibles. Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau.
  
Réseaux d’entreprise traditionnel sont conçus principalement pour fournir aux utilisateurs l’accès aux applications et aux données hébergées dans les centres de données société fonctionne avec la sécurité de périmètre fort. Le modèle traditionnel suppose que les utilisateurs auront accès applications et des données à partir de l’intérieur du périmètre de réseau d’entreprise, sur des liaisons WAN des succursales, ou à distance via des connexions VPN. 
  
L’adoption des applications SaaS tels qu’Office 365 déplace une combinaison de services et données en dehors du périmètre de réseau. Sans optimisation, le trafic entre les utilisateurs et les applications SaaS est soumis à latence introduite par l’inspection des paquets, épingles à cheveux du réseau, les connexions aux points de terminaison distants géographiquement par inadvertance et d’autres facteurs. Vous pouvez vérifier le Office 365 optimiser les performances et la fiabilité par la compréhension et l’implémentation des recommandations d’optimisation clés.
  
Dans cet article, vous apprendrez à :
  
- [Architecture d’office 365](office-365-network-connectivity-principles.md#BKMK_Architecture) telle qu’elle s’applique à la connectivité client vers le nuage
- Mise à jour [principes de connectivité Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) et stratégies d’optimisation du trafic réseau et l’expérience utilisateur final
- Le [service web de points de terminaison Office 365](office-365-network-connectivity-principles.md#BKMK_WebSvc), qui permet aux administrateurs réseau utiliser une liste structurée des points de terminaison pour une utilisation dans l’optimisation du réseau
- [Catégories de point de terminaison nouvel Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) et l’optimisation des instructions
- [Comparaison de la sécurité de périmètre de réseau avec la sécurité du point de terminaison](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Options [d’optimisation incrémentielle](office-365-network-connectivity-principles.md#BKMK_IncOpt) pour le trafic d’Office 365

## <a name="office-365-architecture"></a>Architecture d’Office 365
<a name="BKMK_Architecture"> </a>

Office 365 est un nuage Software-as-a-Service (SaaS) distribué qui fournit des scénarios de collaboration et de productivité via un ensemble divers de micro-services et applications, tels que Exchange Online, SharePoint Online, Skype pour Business Online, Microsoft Les équipes, Exchange Online Protection, Office Online et bien d’autres. Si des applications Office 365 spécifiques peuvent avoir leurs fonctionnalités uniques telle qu’il s’applique au réseau de client et de connectivité vers le nuage, ils partagent tous les entités principales, des objectifs et des modèles d’architecture. Ces entités de sécurité et les modèles d’architecture pour la connectivité sont typiques de nombreux autres nuages SaaS et en même temps en cours différents à partir des modèles de déploiement classique de plateforme en tant que Service et nuages Infrastructure en tant que Service, tels que Microsoft Azure.
  
L’une des fonctionnalités plus importantes architecturales d’Office 365 (qui est souvent manquées ou mal interprétée par les planificateurs réseau) est qu’il est un service distribué véritablement global, dans le contexte de la façon dont les utilisateurs se connectent à elle. L’emplacement du client cible Office 365 est important de comprendre la localité où les données du client sont stockées dans le nuage, mais l’expérience utilisateur avec Office 365 n’implique pas une connexion directe au disques contenant les données. L’expérience utilisateur avec Office 365 (y compris les performances, la fiabilité et autres caractéristiques de qualité important) implique la connectivité via un capots avant service fortement distribué qui sont réparties sur des centaines de sites Microsoft dans le monde entier. Dans la plupart des cas, la meilleure expérience utilisateur est obtenue en autorisant le réseau du client pour router les demandes utilisateur vers le point d’entrée de service Office 365 le plus proche, au lieu de se connecter à Office 365 via un point de sortie dans un emplacement central ou une région.
  
La plupart des clients, les utilisateurs d’Office 365 sont répartis sur plusieurs emplacements. Pour obtenir les meilleurs résultats, les principes présentés dans ce document doivent être considérés à partir de la montée en puissance parallèle (pas une montée en puissance) point de vue, en mettant l’accent sur l’optimisation de connectivité jusqu’au point le plus proche de présence dans le réseau Global Microsoft, pas pour les informations géographiques emplacement du client Office 365. En résumé, cela signifie que même si les données du client Office 365 peuvent être stockées dans un emplacement géographique spécifique, l’expérience Office 365 pour ce client reste distribué peut être présent dans presque proximité (réseau) pour chaque emplacement de l’utilisateur final que le client a .
  
## <a name="office-365-connectivity-principles"></a>Principes de connectivité Office 365
<a name="BKMK_Principles"> </a>

Microsoft recommande les principes suivants pour obtenir des performances et connectivité Office 365 optimale. Utilisez ces principes de connectivité Office 365 pour gérer le trafic et optimiser les performances lors de la connexion à Office 365.
  
Le principal objectif de la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (durée aller-retour) à partir de votre réseau dans le réseau Global Microsoft, public dorsale principale de Microsoft qui relie tous les centres de données de Microsoft avec une faible latence et en nuage de points d’entrée application répartis dans le monde entier. Pour plus d’informations sur le réseau Global Microsoft [comment Microsoft crée son réseau global rapides et fiables](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>Identifier et distinguer le trafic d’Office 365

![Identifier le trafic d’Office 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identifier le trafic réseau de Office 365 est la première étape de la possibilité de différencier ce trafic générique trafic lié aux Internet. Connectivité Office 365 peut être optimisée en implémentant une combinaison des méthodes telles que l’optimisation d’itinéraire réseau, les règles de pare-feu, paramètres du navigateur et contournement de périphériques de contrôle de réseau pour certains points de terminaison.
  
Directives d’optimisation Office 365 antérieures divisés points de terminaison Office 365 en deux catégories, **requis** et **facultatif**. Comme les points de terminaison ont été ajoutées pour prendre en charge les fonctionnalités et nouveaux services Office 365, nous avons réorganisation des points de terminaison Office 365 en trois catégories : **optimiser**, **Autoriser** et **par défaut**. Instructions pour chaque catégorie s’applique à tous les points de terminaison dans la catégorie, effectuer des optimisations plus facile à comprendre et à implémenter. 
  
Pour plus d’informations sur les catégories de point de terminaison Office 365 et les méthodes d’optimisation, consultez la section [catégories de point de terminaison nouvel Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Maintenant, Microsoft publie tous les points de terminaison Office 365 comme un service web et fournit des conseils sur la meilleure méthode pour utiliser ces données. Pour plus d’informations sur la façon de récupérer et travailler avec des points de terminaison Office 365, voir l’article [Office 365 URL et plages d’adresses IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Sortir les connexions réseau localement

![Sortir les connexions réseau localement](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Sortie DNS local et Internet est très important pour réduire la latence de connexion et vous assurer que les connexions utilisateur sont effectuées au point le plus proche de l’entrée aux services Office 365. Dans une topologie de réseau complexe, il est important de mettre en œuvre des DNS local local sortant Internet ensemble. Pour plus d’informations sur la façon dont Office 365 achemine les connexions client au point le plus proche de l’entrée, voir l’article de la [Connectivité des clients](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Avant l’apparition de services en nuage, tels qu’Office 365, l’utilisateur final comme un facteur de conception de l’architecture de réseau la connectivité Internet était relativement simple. Lorsque les services Internet et les sites web sont distribuées dans le monde entier, la latence entre les points de sortie d’entreprise et un point de terminaison donné de destination est en grande partie d’une fonction de la distance géographique.
  
Dans une architecture réseau traditionnel, toutes les connexions Internet sortantes traversent le réseau d’entreprise et sortie à partir d’un emplacement central. Comme les offres de cloud de Microsoft se développent, architecture distribuée réseau accessible sur Internet est devenue critique pour la prise en charge des services de cloud computing sensibles à la latence. Le réseau Global Microsoft ont été conçu pour répondre aux exigences de latence avec l’infrastructure porte sur Service distribué, un fabric dynamique des points d’entrée globale qui achemine les connexions entrantes du service nuage vers le point d’entrée le plus proche. Cela est destiné pour réduire la longueur de la « dernière nautique » clients du nuage Microsoft en simplifiant efficacement l’itinéraire entre le client et le nuage.
  
WAN d’entreprise sont souvent conçus pour le trafic réseau de backhaul à un société centrale siège social pour inspection avant sortant vers Internet, généralement par le biais d’un ou plusieurs serveurs proxy. Le diagramme ci-dessous illustre une topologie réseau.
  
![Modèle de réseau d’entreprise traditionnel](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Office 365 s’exécute sur le réseau Microsoft Global, qui inclut les serveurs frontaux dans le monde entier, il sera souvent un serveur frontal proche de l’utilisateur. En fournissant une sortie Internet locale et en configurant les serveurs DNS internes pour fournir la résolution de nom local pour les systèmes d’extrémité Office 365, le trafic réseau destiné à Office 365 peut se connecter à Office 365 les serveurs frontaux aussi proche que possible à l’utilisateur. Le diagramme ci-dessous illustre un exemple de topologie de réseau qui permet aux utilisateurs qui se connectent depuis le siège social, les sites distants et les sites distants à suivre l’itinéraire le plus court pour le point d’entrée le plus proche Office 365.
  
![Modèle de réseau étendu avec des points de sortie régionales](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Raccourcir le chemin d’accès réseau vers Office 365 points d’entrée de cette manière peuvent améliorer les performances de la connectivité et l’utilisateur final l’expérience dans Office 365 et peut également permettent de réduire l’impact des futures modifications apportées à l’architecture du réseau sur les performances d’Office 365 et fiabilité.
  
En outre, les requêtes DNS peuvent introduire une latence si le serveur DNS qui répond est distant ou occupé (e). Vous pouvez réduire la latence de résolution de nom à la mise en service des serveurs DNS locaux dans les succursales et à s’assurer qu’ils sont correctement configurés pour les enregistrements DNS de cache.
  
Alors que la sortie régionale permettre fonctionnent correctement pour Office 365, le modèle de connectivité optimale serait toujours fournir la sortie de réseau à l’emplacement de l’utilisateur, que ce soit sur le réseau d’entreprise ou les sites distants tels qu’accueil, hôtels, cafés et aéroports. Ce modèle local sortant directement est représenté dans le diagramme ci-dessous.
  
![Architecture de réseau local sortant](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Les entreprises ayant adoptent Office 365 peuvent tirer parti de l’architecture de porte sur Service distribué du réseau Global Microsoft en s’assurant que les connexions utilisateur vers Office 365 prendront l’itinéraire le plus court possible à l’entrée de réseau Global Microsoft le plus proche point. Pour cela, l’architecture de réseau local sortant autorisant le trafic d’Office 365 via la sortie le plus proche, quel que soit l’emplacement de l’utilisateur.
  
L’architecture de sortie local présente les avantages suivants sur le modèle traditionnel :
  
- Fournit des performances optimales Office 365 en optimisant la longueur de l’itinéraire. Connexions utilisateur final sont dynamiquement acheminées vers le point d’entrée le plus proche Office 365 à l’infrastructure distribué porte Service.
- Réduit la charge sur l’infrastructure du réseau d’entreprise en autorisant sortant local.
- Sécurise les connexions aux deux extrémités en tirant parti de la sécurité du point de terminaison client et les fonctionnalités de sécurité dans le nuage.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Éviter les épingles de réseau

![Éviter les épingles à cheveux](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
En règle générale, l’itinéraire le plus court et le plus direct entre l’utilisateur et le point de terminaison le plus proche Office 365 offre les meilleures performances. Un « hairpin » du réseau qui se produit lorsque le trafic WAN ou VPN lié pour une destination particulière est d’abord dirigée vers un autre emplacement intermédiaire (par exemple, la pile de sécurité, broker d’accès dans le cloud, de passerelle web de nuage basé), présentation de la latence et potentielle redirection vers un point de terminaison distant géographiquement. Épingles à cheveux du réseau peuvent également être provoquées par insuffisances routage/peering ou non optimaux recherches DNS (distants).
  
Pour vous assurer que connectivité Office 365 n’est pas soumis à des épingles à cheveux réseau même dans le cas de sortie local, vérifiez si le fournisseur de services qui est utilisé pour fournir la sortie Internet pour l’emplacement de l’utilisateur a une relation d’homologation directe avec le réseau Global Microsoft dans fermer proximité à cet emplacement. Vous pouvez également configurer le routage pour envoyer le trafic Office 365 approuvé directement de sortie, au lieu de proxy ou tunnel via un nuage tiers ou un fournisseur de sécurité réseau en nuage qui traite le trafic lié aux Internet. Résolution de noms DNS des points de terminaison Office 365 contribue à garantir qu’en plus de routage direct, les points d’entrée le plus proche Office 365 sont utilisés pour les connexions utilisateur.
  
Si vous utilisez le réseau en nuage ou les services de sécurité pour le trafic d’Office 365, assurez-vous que l’effet hairpinning est évaluée et leur impact sur les performances d’Office 365 est compris. Cela en examinant le nombre et les emplacements des emplacements de fournisseur de service par le biais duquel le trafic est transféré en relation avec le nombre de vos succursales et les points homologation Microsoft Global Network, qualité de la relation homologation réseau de le fournisseur de services avec votre fournisseur de services Internet et Microsoft et l’impact sur les performances de backhauling dans l’infrastructure de fournisseur de service.
  
En raison du grand nombre d’emplacements distribués avec Office 365 les points d’entrée et leur proximité avec les utilisateurs finaux, routage Office 365 le trafic vers n’importe quel fournisseur de réseau ou de sécurité tiers peut avoir un impact négatif sur les connexions Office 365 si le réseau du fournisseur n’est pas optimiser Office 365 peering configuré.
  
<a name="BKMK_P4"> </a>
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Ignorer les serveurs proxy, les appareils de contrôle du trafic et des technologies de sécurité en double

![Ignorer les serveurs proxy, les appareils de contrôle du trafic et des technologies de sécurité en double](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Les clients en entreprise doivent vérifier leur sécurité réseau et les méthodes de réduction des risques spécifiquement pour Office 365 lié le trafic et utilisent les fonctionnalités de sécurité d’Office 365 afin de réduire leur dépendance envers intrusive, de performances ayant un impact sur et sécurité réseau coûteux technologies pour le trafic réseau Office 365.
  
La plupart des réseaux d’entreprise appliquent la sécurité de réseau pour le trafic Internet à l’aide de technologies telles que les serveurs proxy, inspection SSL, inspection de paquets et systèmes de protection contre la perte de données. Ces technologies fournissent de réduire les risques importants pour les demandes Internet génériques mais peuvent réduire considérablement les performances, l’évolutivité et la qualité de l’expérience utilisateur final lorsqu’elle est appliquée aux points de terminaison Office 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Service web de points de terminaison Office 365

Les administrateurs Office 365 peuvent utiliser un script ou appel REST à consommer une liste structurée des points de terminaison à partir de points de terminaison Office 365 service web et mettre à jour les configurations de pare-feu de périmètre et autres périphériques réseau. Cela permet de garantir que le trafic lié à Office 365 est identifié, traité de manière appropriée et géré différemment de trafic réseau pour les sites web Internet générique et souvent inconnu. Pour plus d’informations sur l’utilisation d’Office 365 points de terminaison de service web, voir l’article [Office 365 URL et plages d’adresses IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Scripts PAC (Proxy la Configuration automatique)
<a name="BKMK_WebSvc"> </a>

Les administrateurs Office 365 peuvent créer des scripts PAC (Configuration automatique du Proxy) peuvent être remis aux ordinateurs des utilisateurs via le WPAD ou la stratégie de groupe. Scripts PAC peuvent servir à contourner les serveurs proxy pour les demandes des utilisateurs WAN ou VPN, Office 365 autorisant le trafic d’Office 365 utiliser des connexions Internet directes plutôt que de parcourir le réseau d’entreprise.
  
#### <a name="office-365-security-features"></a>Fonctionnalités de sécurité d’Office 365
<a name="BKMK_WebSvc"> </a>

Microsoft est transparent sur la sécurité du centre de données, sécurité opérationnelle et réduction des risques autour des serveurs Office 365 et les points de terminaison de réseau qu’ils représentent. Fonctionnalités de sécurité intégrée à 365 Office sont disponibles pour réduire les risques de sécurité réseau, tels que Data Loss Prevention, antivirus, l’authentification multifacteur, zone de verrouillage du client, protection contre les menaces avancées, menaces Office 365, Office 365 sécurisé Score, Exchange Online Protection et la sécurité réseau par déni.
  
Pour plus d’informations sur le centre de données Microsoft et la sécurité réseau globale, voir le [Centre de gestion de la confidentialité de Microsoft](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nouvelles catégories de point de terminaison Office 365
<a name="BKMK_Categories"> </a>

Points de terminaison Office 365 représentent un ensemble d’adresses réseau et sous-réseaux varié. Points de terminaison peuvent être des URL, plages d’adresses IP ou l’adresse IP et certains points de terminaison sont répertoriés avec des ports TCP/UDP spécifiques. URL peuvent être un nom de domaine complet comme *account.office.net* , ou une URL générique comme * \*. office365.com*.
  
> [!NOTE]
> Les emplacements des points de terminaison Office 365 au sein du réseau ne sont pas directement liées à l’emplacement des données client Office 365. Pour cette raison, les clients doivent ressembler à Office 365 comme un service global et distribué et ne doivent pas essayer de bloquer les connexions réseau aux points de terminaison Office 365 en fonction des critères géographiques.
  
Dans notre guide précédente pour gérer le trafic d’Office 365, les points de terminaison ont été organisés en deux catégories, **requis** et **facultatif**. Points de terminaison dans chaque catégorie requises optimisations différentes en fonction de l’importance du service et de nombreux clients rencontrés défis en matière de justifier l’application des même optimisations de réseau à la liste complète des adresses IP et les URL d’Office 365. 
  
Dans le nouveau modèle, points de terminaison sont répartis sur trois catégories, **optimiser**, **Autoriser** et **par défaut**, fournissant un tableau croisé dynamique basé sur des priorités où efforts d’optimisation réseau activé pour réaliser l’amélioration des performances meilleures et renvoyer sur investissement. Les points de terminaison sont consolidés dans les catégories ci-dessus en fonction de la sensibilité de l’expérience utilisateur efficace à l’enveloppe de volume, la qualité et les performances réseau des scénarios et faciliter la mise en œuvre. Optimisations recommandées peuvent être appliquées à la même manière pour tous les points de terminaison dans une catégorie donnée.
  
- **Optimisation** de points de terminaison sont requis pour la connectivité à tous les services Office 365 et représentent plus de 75 % de la bande passante, les connexions et les volumes de données Office 365. Ces points de terminaison représentent des scénarios Office 365 qui sont les plus sensibles aux performances et la disponibilité, la latence du réseau. Tous les points de terminaison sont hébergées dans des centres de données Microsoft. Le taux de modifications effectuées sur les points de terminaison de cette catégorie est censé être très inférieur à celui pour les points de terminaison dans les deux autres catégories. Cette catégorie inclut un ensemble très petit (l’ordre de 10) d’URL et un ensemble défini de sous-réseaux IP dédiées à des charges de travail principaux Office 365 tels que Exchange Online, SharePoint Online, Skype pour Business Online et Microsoft Teams la clé.

    Une liste condensée de points de terminaison critique bien définie doit vous aider à planifier et à implémenter les optimisations de réseau de valeur haute pour ces destinations plus rapides et plus faciles.

    Exemples de points de terminaison *optimiser* *https://outlook.office365.com* , *https://\<client\>. sharepoint.com* et *https://\<client\>-my.sharepoint.com* .

    Méthodes d’optimisation sont les suivantes :

  - Contournement de média ou d’autorisation *optimiser* points de terminaison sur les périphériques réseau et les services qui exécutent le trafic interception, SSL déchiffrement, approfondie des paquets et le filtrage du contenu.
  - Ignorer les périphériques de proxy sur site et services en nuage de proxy couramment utilisées pour la navigation Internet générique.
  - Classer par priorité l’évaluation de ces points de terminaison comme étant entièrement approuvé par vos systèmes d’infrastructure et de périmètre de réseau.
  - Classer par priorité réduction ou élimination des backhauling WAN et faciliter directe sortie Internet en distribué pour ces systèmes d’extrémité comme près utilisateurs/succursales que possible.
  - Faciliter la connexion directe à ces points de terminaison dans le nuage pour les utilisateurs VPN en implémentant tunnel fractionné.
  - Assurez-vous que les adresses IP renvoyées par la résolution de noms DNS correspondent à l’itinéraire de routage sortant pour ces systèmes d’extrémité.
  - Classer par priorité les points de terminaison pour l’intégration de réseau étendu SD pour le routage de latence minimale directe en point homologation Internet le plus proche du réseau global Microsoft.

- Points de terminaison **Autoriser** sont requis pour la connectivité à des fonctionnalités et des services Office 365 spécifiques, mais ne sont pas soumis à des performances du réseau et la latence en tant que ceux de la catégorie *d’optimisation* . L’encombrement réseau de ces points de terminaison du point de vue de la bande passante et de connexion est également beaucoup plus petite. Ces points de terminaison sont dédiés à Office 365 et sont hébergées dans des centres de données Microsoft. Ils représentent un large éventail de micro-services Office 365 et leurs dépendances (l’ordre des URL ~ 100) et sont changer à une vitesse supérieure à celles de la catégorie *d’optimisation* . Pas tous les points de terminaison de cette catégorie sont associés à des sous-réseaux IP dédiés définis.

    Optimisations du réseau pour les systèmes d’extrémité *Autoriser* peut améliorer l’expérience utilisateur Office 365, mais certains clients peuvent choisir de ces optimisations plus étroitement pour réduire les modifications apportées à leur réseau d’étendue.

    Exemples de points de terminaison *Autoriser* *https://\*. protection.outlook.com* et *https://accounts.accesscontrol.windows.net*.

    Méthodes d’optimisation sont les suivantes :

  - Contournement de média ou d’autorisation *Autoriser* points de terminaison sur les périphériques réseau et les services qui exécutent le trafic interception, SSL déchiffrement, approfondie des paquets et le filtrage du contenu.
  - Classer par priorité l’évaluation de ces points de terminaison comme étant entièrement approuvé par vos systèmes d’infrastructure et de périmètre de réseau.
  - Classer par priorité réduction ou élimination des backhauling WAN et faciliter directe sortie Internet en distribué pour ces systèmes d’extrémité comme près utilisateurs/succursales que possible.
  - Assurez-vous que les adresses IP renvoyées par la résolution de noms DNS correspondent à l’itinéraire de routage sortant pour ces systèmes d’extrémité.
  - Classer par priorité les points de terminaison pour l’intégration de réseau étendu SD pour le routage de latence minimale directe en point homologation Internet le plus proche du réseau global Microsoft.

- Points de terminaison **par défaut** représentent des services Office 365 et les dépendances qui ne nécessitent pas de n’importe quel optimisation et peuvent être traités par les réseaux client comme Internet normal lié le trafic. Notez que certains points de terminaison de cette catégorie ne peuvent pas être hébergés dans les centres de données Microsoft. Voici des exemples *https://odc.officeapps.live.com* et *https://appexsin.stb.s-msn.com*.

Pour plus d’informations sur les techniques d’optimisation réseau Office 365, voir l’article [points de terminaison de gestion Office 365](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparaison de la sécurité de périmètre de réseau avec la sécurité du point de terminaison
<a name="BKMK_SecurityComparison"> </a>

L’objectif de la sécurité réseau traditionnelle consiste à renforcer la sécurité du périmètre du réseau d’entreprise contre les intrusions et les attaques malveillantes. Comme les organisations adoptent Office 365, certains services réseau et les données sont partiellement ou entièrement migrées vers le nuage. Comme tout changement fondamental à l’architecture de réseau, ce processus nécessite une réévaluation de la sécurité réseau qui tient compte des facteurs émergents :
  
- Comme l’adoptent de services de cloud computing, les services réseau et les données sont réparties entre des centres de données sur site et le nuage et périmètre de sécurité n’est plus appropriée sur son propre.
- Les utilisateurs distants se connectent aux ressources d’entreprise dans les centres de données sur site et dans le nuage à partir d’emplacements ne soit pas contrôlés tel que le domicile, hôtels et les cafés.
- Fonctionnalités de sécurité spécialisé sont intégrées plus en plus des services de cloud computing et peuvent compléter ou remplacer les systèmes de sécurité existants.

Microsoft offre un large plage d’Office 365 fonctionnalités de sécurité et fournit des conseils d’utilisation des meilleures pratiques de sécurité qui peuvent vous aider à garantir la sécurité des données et de réseau pour Office 365. Les meilleures pratiques recommandées sont les suivantes :
  
- **Utiliser l’authentification multifacteur (MFA)** MFA ajoute une couche de protection supplémentaire à une stratégie de mot de passe fort en demandant aux utilisateurs à remercier un appel téléphonique, message texte ou une notification de l’application sur leur téléphone active après avoir entré correctement leur mot de passe.

- **Utiliser Office 365 Cloud application la sécurité** Définir des stratégies pour suivre l’activité anormale et d’agir. Configurer les alertes de sécurité pour application Cloud Microsoft Office 365 afin que les administrateurs peuvent vérifier activité utilisateur inhabituelle ou risqué, telles que le téléchargement de grandes quantités de données, plusieurs échecs de connexion, ou adresses de connexions à partir d’une adresse IP inconnue ou dangereuse.

- **Configurer la protection contre la perte de données (DLP)** DLP permet d’identifier les données sensibles et créer des stratégies qui permettent d’empêcher les utilisateurs d’accidentellement ou intentionnellement partage des données. DLP fonctionne sur Office 365, notamment Exchange Online, SharePoint Online et OneDrive afin que vos utilisateurs de rester conformes sans interrompre leur travail.

- **Zone de sécurité utilisez client** En tant qu’un administrateur Office 365, vous pouvez utiliser la zone de sécurité client pour contrôler la façon dont un ingénieur du support technique Microsoft accède à vos données pendant une session de l’aide. Dans les cas où l’ingénieur requiert l’accès à vos données à résoudre les problèmes et à résoudre un problème, zone de sécurité client vous permet d’approuver ou refuser la demande d’accès.

- **Utilisez le Score sécurisé Office 365** Score sécurisé est un outil analytique sécurité recommande ce que vous pouvez faire pour réduire encore le risque. Score sécurisé examine vos paramètres Office 365 et les activités et les compare à une base établie par Microsoft. Vous obtiendrez un score dépendent de comment aligné avec les meilleures pratiques de sécurité.

Une approche holistique pour une sécurité renforcée obligatoirement tenant compte des éléments suivants :
  
- Décale accentuation à partir de la sécurité de périmètre vers la sécurité du point de terminaison en appliquant en nuage et les fonctionnalités de sécurité du client Office.
  - Réduire le périmètre de sécurité pour le centre de données
  - Activer l’approbation équivalente pour les périphériques d’utilisateur à l’intérieur du bureau ou sur des sites distants
  - Se concentrer sur la sécurisation de l’emplacement des données et l’emplacement de l’utilisateur
  - Machines utilisateur managé ont de confiance plus élevé avec la sécurité du point de terminaison
- Gérer la sécurité, toutes les informations holistique ne pas entièrement axée sur le périmètre
  - Redéfinition des liaisons réseau étendu et création de sécurité de réseau de périmètre en autorisant le trafic approuvé d’ignorer les périphériques de sécurité et en séparant les périphériques non gérés à des réseaux Wi-Fi invité.
  - Réduit les exigences de sécurité réseau du périmètre de réseau étendu d’entreprise
  - Certains périphériques de sécurité de périmètre de réseau telles que les pare-feu sont nécessaires, mais la chargent est réduite
  - Garantit sortant local pour le trafic d’Office 365
- Améliorations peuvent être résolues par incrément, comme décrit dans la section [optimisation incrémentielle](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Certaines techniques d’optimisation peuvent offrir une meilleure taux de coûts-avantages en fonction de votre architecture de réseau, et vous devez choisir les optimisations qui le plus pertinent pour votre organisation.

Pour plus d’informations sur la sécurité Office 365 et de conformité, voir l’article [vue d’ensemble de la sécurité et conformité dans Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Optimisation incrémentielle
<a name="BKMK_IncOpt"> </a>

Nous avons représenté le modèle de connectivité de réseau idéale pour SaaS plus haut dans cet article, mais de nombreuses grandes entreprises avec des architectures de réseau complexe historiquement, ne sera pas pratique d’effectuer directement toutes ces modifications. Dans cette section, nous présentent un certain nombre de modifications incrémentielles qui peuvent aider à améliorer la fiabilité et les performances d’Office 365.
  
Les méthodes que vous utiliserez pour optimiser le trafic d’Office 365 varie en fonction de votre topologie du réseau et les périphériques réseau que vous avez implémenté. Grandes entreprises avec de nombreux emplacements et pratiques de sécurité complexes réseau requises pour le développement d’une stratégie qui inclut tout ou partie des principes répertoriés dans la section [principes de connectivité Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) , tandis que les organisations de petite taille peuvent uniquement Il faut prendre en compte une ou deux.
  
Vous pouvez aborder optimisation comme un processus incrémentiels, l’application de chaque méthode successivement. Le tableau suivant répertorie les méthodes d’optimisation clés dans l’ordre de leur impact sur la latence et la fiabilité pour le plus grand nombre d’utilisateurs.
  
|**Méthode d’optimisation**|**Description**|**Impact**|
|:-----|:-----|:-----|
|Résolution DNS locale entrant et sortant d’Internet  <br/> |Mettre en service des serveurs DNS locaux dans chaque emplacement et vérifiez que sortant de connexions d’Office 365 à Internet aussi proche que possible à emplacement son.  <br/> | Réduire la latence  <br/>  Améliorer la connectivité fiable au point d’entrée le plus proche Office 365  <br/> |
|Ajouter des points de sortie régionales  <br/> |Si votre réseau d’entreprise a plusieurs emplacements, mais du point de seule sortie, ajouter des points de sortie régionaux pour permettre aux utilisateurs de se connecter au point d’entrée le plus proche Office 365.  <br/> | Réduire la latence  <br/>  Améliorer la connectivité fiable au point d’entrée le plus proche Office 365  <br/> |
|Proxys de contournement de média et les périphériques de l’inspection  <br/> |Configurer les navigateurs avec les fichiers PAC qui envoient des demandes d’Office 365 directement aux points de sortie.  <br/> Configurer les routeurs et les pare-feu pour autoriser le trafic d’Office 365 sans inspection.  <br/> | Réduire la latence  <br/>  Réduire la charge sur les périphériques réseau  <br/> |
|Activer la connexion directe pour les utilisateurs VPN  <br/> |Pour les utilisateurs VPN, activer les connexions d’Office 365 pour vous connecter directement à partir du réseau de l’utilisateur plutôt que sur le tunnel VPN en implémentant tunnel fractionné.  <br/> | Réduire la latence  <br/>  Améliorer la connectivité fiable au point d’entrée le plus proche Office 365  <br/> |
|Migration de WAN traditionnel vers SD-WAN  <br/> |SD-WAN (logiciel défini les réseaux WAN) simplifie la gestion de réseau étendue et améliorer les performances en remplaçant traditionnels WAN avec authentification multifacteur, similaire à la virtualisation des ressources de calcul à l’aide de machines virtuelles (VM).  <br/> | Améliorer les performances et la facilité de gestion du trafic réseau étendu  <br/>  Réduire la charge sur les périphériques réseau  <br/> |
