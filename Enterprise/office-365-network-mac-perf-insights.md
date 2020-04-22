---
title: Informations sur le réseau Microsoft 365 (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Informations sur le réseau Microsoft 365 (aperçu)
ms.openlocfilehash: 0146019d1424cda696104d68eeda32ce28a26391
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612904"
---
# <a name="microsoft-365-network-insights-preview"></a>Informations sur le réseau Microsoft 365 (aperçu)

Les informations sur le **réseau** sont des mesures de performances en direct collectées à partir de votre client Microsoft 365 et disponibles uniquement par les utilisateurs administratifs de votre client. Les informations s’affichent dans le centre d’administration Microsoft 365 <https://portal.microsoft.com/adminportal/home#/networkperformance>à l’adresse.

Les informations sont destinées à vous aider à concevoir des périmètres réseau pour vos emplacements de bureau. Chaque vue fournit des informations détaillées sur les caractéristiques de performances d’un problème commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client.

Cinq aspects spécifiques du réseau peuvent être affichés pour chaque emplacement de bureau :

- [Sortie réseau retractée](#backhauled-network-egress)
- [Meilleures performances détectées pour les clients proches de vous](#better-performance-detected-for-customers-near-you)
- [Utilisation d’un service frontal Exchange Online non optimal](#use-of-a-non-optimal-exchange-online-service-front-door)
- [Utilisation d’un service SharePoint Online non optimal](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="backhauled-network-egress"></a>Sortie réseau retractée

Cette vue s’affiche si le service réseau Insights détecte que la distance entre un emplacement utilisateur donné et la sortie réseau est supérieure à 500 kilomètres (800 kilomètres), ce qui indique que le trafic Microsoft 365 est replacé vers un périphérique ou un proxy Internet Edge commun.

Cette vue est abrégée en « sortie » dans certains affichages de résumés.

![Sortie réseau retractée](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>Scénario

Cela indique que la distance entre l’emplacement du bureau et la sortie du réseau est supérieure à 500 kilomètres (800 kilomètres). L’emplacement du Bureau est identifié par un emplacement de l’ordinateur client masqué et l’emplacement de sortie du réseau est identifié à l’aide de l’adresse IP inverse pour les bases de données d’emplacement. L’emplacement du Bureau peut être inexact si les services d’emplacement Windows sont désactivés sur les ordinateurs. L’emplacement de sortie réseau peut être inexact si les informations de la base de données d’adresses IP inversées sont inexactes.

Les détails de cette analyse incluent l’emplacement du bureau, le pourcentage estimé du nombre total d’utilisateurs clients à l’emplacement, l’emplacement de sortie du réseau actuel, la pertinence de l’emplacement de sortie, la distance entre l’emplacement et le point de sortie actuel, la date du premier détection de la condition et la date à laquelle la condition a été résolue.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour cette vue d’ensemble, nous recommandons un accès réseau plus proche de l’emplacement du Bureau de sorte que la connectivité puisse acheminer les performances de façon optimale vers le réseau mondial de Microsoft et vers le service frontal Microsoft 365 service le plus proche. Une sortie étroite du réseau vers les bureaux des utilisateurs permet également d’améliorer les performances à l’avenir à mesure que Microsoft étend à la fois les points de présence réseau et les portes frontales du service Microsoft 365.

Pour plus d’informations sur la façon de résoudre ce problème, reportez-vous à la rubrique [sortie locale des connexions réseau](office-365-network-connectivity-principles.md#egress-network-connections-locally) dans [Office 365 principes de connectivité réseau](office-365-network-connectivity-principles.md).

## <a name="better-performance-detected-for-customers-near-you"></a>Meilleures performances détectées pour les clients proches de vous

Cette vue s’affiche si le service réseau Insights détecte qu’un nombre important de clients dans votre zone de métro offre de meilleures performances que les utilisateurs de votre organisation à cet emplacement de bureau.

Cette vue est abrégée en « pairs » dans certains affichages de résumés.

![Performances réseau relatives](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>Scénario

Cette vue d’ensemble examine les performances totales des clients Microsoft 365 dans la même ville que cet emplacement de bureau. Cette vue s’affiche si la latence moyenne de vos utilisateurs est supérieure de 10% à la latence moyenne des clients voisins.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Il peut y avoir plusieurs raisons à cette condition, notamment la latence de votre réseau d’entreprise ou de votre fournisseur de services Internet, des goulots d’étranglement ou des problèmes de conception de l’architecture. Examinez la latence entre chaque tronçon de l’itinéraire entre votre réseau Office et le porte-avant Microsoft 365 actuel. Pour plus d’informations, consultez la rubrique [Office 365 Network Connectivity principes](office-365-network-connectivity-principles.md).

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Utilisation d’un service frontal Exchange Online non optimal

Cette vue s’affiche si le service réseau Insights détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas à un service frontal Exchange Online optimal.

Cette vue est abrégée en « routage » dans certains affichages de résumés.

![Porte de façade non optimale](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>Scénario

Nous répertorions les portes frontales du service Exchange Online qui peuvent être utilisées à partir de la ville de l’emplacement du bureau avec de bonnes performances. Si le test actuel indique l’utilisation d’un service frontal Exchange Online qui ne figurent pas sur cette liste, nous appelons cette recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une trappe frontal non optimale d’un service Exchange Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct. Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>Utilisation d’un service SharePoint Online non optimal

Cette vue s’affiche si le service réseau Insights détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas au porte-tout du service SharePoint Online le plus proche.

Cette vue est abrégée sous la forme « AFD » dans certains affichages de résumés.

![Porte de façade non optimale](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>Scénario

Nous allons identifier la porte d’écran du service SharePoint Online à laquelle le client de test se connecte. Ensuite, pour la ville de l’emplacement du bureau, nous comparons cette ville avec le service SharePoint Online attendu pour cette ville. S’il ne correspond pas, nous en faisons la recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une trappe frontal non optimale de service SharePoint Online pourrait être causée par le système de test réseau avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct. Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint

Cette vue s’affiche si le service réseau Insights détecte que la bande passante entre l’emplacement de bureau spécifique et SharePoint Online est inférieure à 1 MBps.

Cette vue est abrégée en « débit » dans certains affichages de résumés.

### <a name="what-does-this-mean"></a>Scénario

La vitesse de téléchargement qu’un utilisateur peut obtenir à partir de SharePoint Online et des portes frontales du service OneDrive entreprise est exprimée en mégaoctets par seconde (Mbits/s). Si cette valeur est inférieure à 1 MBps, nous fournissons cette vue.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour améliorer la vitesse de téléchargement, vous devrez peut-être augmenter la bande passante. Par ailleurs, il peut y avoir une congestion réseau entre les ordinateurs des utilisateurs à l’emplacement du bureau et le capot frontal du service SharePoint Online. Cette opération est parfois appelée perte de congestion et limite la vitesse de téléchargement disponible aux utilisateurs, même si la bande passante disponible est suffisante.

## <a name="china-user-optimal-network-egress"></a>Sortie du réseau chinois utilisateur optimal

Cette vue s’affiche si votre organisation a des utilisateurs en Chine se connectent à votre client Microsoft 365 dans d’autres emplacements géographiques. 

### <a name="what-does-this-mean"></a>Scénario

Si votre organisation possède une connectivité WAN privée, nous vous recommandons de configurer un circuit WAN réseau à partir de vos emplacements de bureau en Chine qui dispose de la sortie réseau vers Internet dans l’un des emplacements suivants :

- Hong Kong (R.A.S.)
- Japon
- Taïwan
- Corée du Sud
- Singapour
- Malaisie

Une sortie Internet plus éloignée des utilisateurs que ces emplacements réduira les performances, et la sortie en Chine peut entraîner des problèmes de latence et de connectivité élevés en raison d’une congestion transfrontalière.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour plus d’informations sur la façon d’atténuer les problèmes de performances liés à cette vue, consultez la rubrique [Office 365 global client Optimization for China Users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).

## <a name="related-topics"></a>Voir aussi

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Microsoft 365 Network Assessment (aperçu)](office-365-network-mac-perf-score.md)

[Test de connectivité Microsoft 365 dans le centre d’administration M365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)
