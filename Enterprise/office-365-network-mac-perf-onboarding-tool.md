---
title: Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)
ms.openlocfilehash: ae3a818100f8b84f89d502f9e076fc1fcf6559e8
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890397"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a>Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)

L’outil d’intégration réseau Office 365 se trouve à <https://connectivity.office.com>l’adresse. Il s’agit d’un outil complémentaire pour les informations sur le réseau et les informations de score réseau disponibles dans le centre d’administration 365 de Microsoft sous **Health | Menu performances du réseau** .

Le réseau d’informations dans le centre d’administration 365 de Microsoft est basé sur les mesures de produit pour votre client Office 365. En comparaison, le réseau Insights de l’outil d’intégration réseau Office 365 est exécuté localement dans l’outil. Les tests pouvant être effectués dans-le produit sont limités et l’exécution de tests locaux sur l’utilisateur permet de collecter davantage de données, ce qui donne lieu à des analyses plus approfondies. Envisagez ensuite que le réseau Insights dans le centre d’administration 365 de Microsoft indique qu’il existe un problème de réseau pour l’utilisation d’Office 365 à un emplacement de bureau spécifique. L’outil d’intégration réseau Office 365 peut vous aider à identifier la cause première de ce problème à l’aide d’une action d’amélioration des performances réseau recommandée.

Nous vous recommandons de les utiliser ensemble pour évaluer l’état de qualité de la mise en réseau pour chaque emplacement de bureau dans le centre d’administration 365 de Microsoft et des informations supplémentaires sont disponibles après le déploiement de tests basés sur l’outil d’intégration réseau Office 365.

>[!IMPORTANT]
>Les informations relatives au réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="the-advanced-tests-client-application"></a>Application cliente de tests avancés

L’outil d’intégration réseau Office 365 est doté de deux parties. Il existe un site <https://connectivity.office.com> Web et il existe une application cliente téléchargeable Windows. Le client téléchargeable exécute des tests de connectivité réseau avancés et la plupart des tests doivent être exécutés.

Vous pouvez exécuter le test du client avancé à partir du site Web et remplir les résultats dans la page Web au fur et à mesure de son exécution.

![Exemple de résultats de test pour l’outil d’intégration réseau O365](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a>Emplacement du Bureau de l’utilisateur

L’emplacement du Bureau de l’utilisateur est détecté à partir du navigateur Web de l’utilisateur. Il permet d’identifier les distances réseau par des parties spécifiques du périmètre réseau de l’entreprise.

L’emplacement du Bureau de l’utilisateur est indiqué sur la carte.

## <a name="distance-to-the-network-egress-location"></a>Distance vers l’emplacement de sortie réseau

Nous identifions l’adresse IP de sortie réseau côté serveur. Les bases de données d’emplacement sont utilisées pour Rechercher l’emplacement approximatif de la sortie réseau et déterminer la distance à partir de cet emplacement vers l’emplacement du bureau. Il s’agit d’un aperçu réseau si la distance est supérieure à 500 kilomètres (800 kilomètres).

L’emplacement de sortie du réseau est affiché sur la carte et connecté à l’emplacement du Bureau de l’utilisateur indiquant le trajet réseau à l’intérieur du réseau étendu de l’entreprise.

L’emplacement recherché à partir de l’adresse IP de sortie du réseau n’est peut-être pas exact, ce qui entraîne un résultat faux de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser les sites Web d’emplacement d’adresses IP réseau accessibles au public.

L’implémentation d’une sortie réseau locale et directe à partir d’emplacements de bureau d’utilisateurs vers Internet est recommandée pour la connectivité réseau Office 365. Les améliorations apportées à la sortie locale et directe sont la meilleure façon de traiter cette analyse réseau.

## <a name="exchange-online-service-front-door"></a>Volet frontal du service Exchange Online

Le volet Office Online du service Exchange Online est identifié de la même façon qu’Outlook le fait et nous Mesurez la latence TCP réseau à partir de l’emplacement du Bureau de l’utilisateur. Ces deux éléments sont affichés et le porte d’appel frontal Exchange Online Service est comparé à la liste des portes frontales de service optimales recommandées pour l’emplacement actuel. Il s’agit d’un aperçu réseau si une porte d’écran frontale Exchange Online non optimale est utilisée.

L’utilisation d’une trappe frontal non optimale d’un service Exchange Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct. Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

Nous calculons une amélioration potentielle de la latence TCP vers le capot frontal du service Exchange Online. Cette opération est réalisée en examinant la latence du réseau des utilisateurs testés et en soustrayant la latence réseau de l’emplacement actuel vers le capot frontal du service Exchange Online armoires. La différence représente la possibilité d’amélioration potentielle.

## <a name="comparison-of-performance-of-customers-in-the-area"></a>Comparaison des performances des clients dans la zone

La latence TCP réseau de l’emplacement du Bureau de l’utilisateur vers le capot frontal du service Exchange Online est comparée à celle des autres clients Office 365 dans la même région de métro. Un aperçu réseau s’affiche si 10% ou plus de clients dans la même zone de métro offrent de meilleures performances.

Cette vue réseau est générée en fonction du fait que tous les utilisateurs d’une ville ont accès à la même infrastructure de télécommunications et à la même proximité des circuits Internet et du réseau de Microsoft.

## <a name="in-use-default-gateway"></a>Utiliser la passerelle par défaut

La passerelle par défaut en cours d’utilisation est le routeur que le client de test a configuré pour le routage des connexions réseau TCP/IP.

Il est fourni à des fins d’information uniquement et ne contribue pas à une analyse réseau.

## <a name="in-use-dns-servers"></a>Dans utiliser un ou plusieurs serveurs DNS

Cela indique le serveur DNS configuré sur l’ordinateur client qui a exécuté les tests. Il peut s’agir d’un serveur de résolution récursive DNS, mais cela n’est pas courant. Il est plus probable qu’un serveur de redirection DNS met en cache les résultats DNS et transfère les demandes DNS non mises en cache vers un autre serveur DNS.

Il est fourni à des fins d’information uniquement et ne contribue pas à une analyse réseau.

## <a name="identified-dns-recursive-resolver-server"></a>Serveur de résolution récursive DNS identifié

Le programme de résolution de contenu DNS en cours d’utilisation est identifié en effectuant une demande DNS spécifique, puis en demandant au serveur de noms DNS l’adresse IP à partir de laquelle il a reçu la même demande. Cette adresse IP est le résolveur récursif DNS et il est recherché dans les bases de données d’emplacement des adresses IP pour trouver l’emplacement. La distance entre l’emplacement du Bureau de l’utilisateur et l’emplacement du serveur de résolution récursive DNS est ensuite calculée. Il s’agit d’un aperçu réseau si la distance est supérieure à 500 kilomètres (800 kilomètres).

L’emplacement recherché à partir de l’adresse IP de sortie du réseau n’est peut-être pas exact, ce qui entraîne un résultat faux de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser les sites Web d’emplacement d’adresses IP réseau accessibles au public.

Cette analyse réseau a un impact spécifique sur la sélection du capot frontal du service Exchange Online. Pour répondre à cette compréhension, la sortie locale et directe du réseau doit être un prérequis, puis le résolveur DNS récursif doit se trouver près de cette sortie réseau.

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a>Recherche DNS d’un serveur frontal Exchange Online et d’un serveur frontal SharePoint Online

Ces éléments indiquent l’enregistrement DNS pour le service frontal pour ces deux charges de travail Office 365. Elles sont fournies à des fins d’information uniquement et aucune analyse réseau n’est associée.

## <a name="proxy-server-identification"></a>Identification du serveur proxy

Nous allons identifier les serveurs proxy configurés sur l’ordinateur local. Nous allons identifier si l’un de ces éléments est configuré dans le chemin réseau pour optimiser la catégorie du trafic réseau Office 365. Nous identifions la distance entre l’emplacement du Bureau de l’utilisateur et les serveurs proxy. La distance est testée en premier par la commande ping ICMP et, si cela échoue, que nous testons avec le ping TCP et finalement, si cette opération échoue, nous examinons l’adresse IP du serveur proxy dans une base de données d’emplacement d’adresse IP. Nous affichons un Network Insight si le serveur proxy est plus de 500 kilomètres (800 kilomètres) de l’emplacement du Bureau de l’utilisateur.

## <a name="media-quality-checks"></a>Contrôles de la qualité des médias

Ce test installe et exécute l’outil d’évaluation du réseau Skype entreprise et interprète les résultats. L’outil se trouve à l' [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885)adresse.

Il s’agit de tests de protocole UDP utilisés par les fonctionnalités d’appel et de conférence audio et vidéo de Microsoft Teams. Nous testons la perte de paquets UDP, la latence du réseau UDP, le bougé UDP et la réorganisation des paquets UDP. Un aperçu réseau s’affiche si l’un de ces éléments se trouve au-dessus de la plage autorisée.

## <a name="tcp-connectivity-tests"></a>Tests de connectivité TCP

Nous testons la connectivité HTTP à partir de l’emplacement du Bureau de l’utilisateur vers tous les points de terminaison réseau Office 365 requis. Ces éléments sont publiés [https://aka.ms/o365ip](https://aka.ms/o365ip)à l’adresse. Network Insight est illustré pour les points de terminaison réseau requis qui ne peuvent pas être connectés à.

La connectivité ay est bloquée par un serveur proxy, un pare-feu ou un autre périphérique de sécurité réseau sur le périmètre du réseau d’entreprise ou en cours d’utilisation en tant que proxy Cloud.

## <a name="ssl-interception-tests"></a>Tests d’interception SSL

Nous testons le certificat SSL à chaque point de terminaison réseau Office 365 requis qui se trouve dans la catégorie Optimize ou [https://aka.ms/o365ip](https://aka.ms/o365ip)Allow, comme défini sur. Si un ou plusieurs tests ne trouvent pas de certificat SSL Microsoft, le réseau chiffré doit avoir été intercepté par un périphérique réseau intermédiaire. Un Network Insight est illustré sur tous les points de terminaison réseau chiffrés interceptés.

Lorsqu’un certificat SSL n’est pas fourni par Microsoft, nous affichons le nom de domaine complet (FQDN) pour le test et le propriétaire du certificat SSL en cours d’utilisation. Ce propriétaire de certificat SSL peut être un fournisseur de serveur proxy, ou il peut s’agir d’un certificat auto-signé de l’entreprise.

## <a name="network-path-diagnostics"></a>Diagnostics de chemin d’accès réseau

Cette section présente les résultats d’un itinéraire ICMP vers le volet frontal du service Exchange Online, le volet frontal du service SharePoint Online et le porte de service frontal de Microsoft Teams. Il est fourni à des fins d’information uniquement et aucune analyse réseau n’est associée.

## <a name="related-topics"></a>Sujets associés

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Office 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Office 365 (préversion)](office-365-network-mac-perf-score.md)
