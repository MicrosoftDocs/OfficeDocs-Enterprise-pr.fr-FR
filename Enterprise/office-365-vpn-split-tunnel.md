---
title: 'Présentation : la segmentation de tunnel VPN avec Office 365'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Instructions d’utilisation de la segmentation de tunnel VPN avec Office 365 afin d’optimiser la connectivité d’Office 365 pour les utilisateurs distants.
ms.openlocfilehash: 6a41783a1660f17885b61a27ff605f445591ebbb
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592218"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunneling"></a>Optimiser la connectivité d’Office 365 pour les utilisateurs à distance à l’aide de la segmentation de tunnel VPN
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunneling for Office 365](office-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](office-365-networking-china.md).
-->

Pour les clients qui connectent leurs appareils de travail à distance au réseau d'entreprise ou à l'infrastructure cloud via un VPN, Microsoft recommande que les scénarios clés Office 365 **Microsoft Teams**, **SharePoint Online** et **Exchange Online** soient acheminés via une configuration de _segmentation de tunnel VPN_. Cette stratégie s’avère particulièrement importante dans le cadre de la stratégie de première ligne mise en place pour favoriser la productivité des employés, lors d'événements qui entraîne un travail à domicile à grande échelle, tels que la crise de COVID-19.

![Configuration de la segmentation de tunnel par VPN](media/vpn-split-tunneling/vpn-model-2.png)

_Image 1 : Une solution de segmentation de tunnel VPN avec des exceptions Office 365 définies, envoyées directement au service. Tout autre trafic traverse le tunnel VPN, indépendamment de la destination._

L’essentiel de cette approche consiste à offrir une méthode simple, permettant aux entreprises de limiter les risques liés à la saturation de l’infrastructure VPN et d’améliorer considérablement les performances d’Office 365 le plus rapidement possible. La configuration des clients VPN pour permettre au trafic Office 365 le plus important et le plus intense de contourner le tunnel VPN offre les avantages suivants :

- Atténue immédiatement la cause principale de la majorité des problèmes de performances et de capacité réseau, signalés par les clients dans les architectures VPN d'entreprise, ayant un impact sur l'expérience utilisateur Office 365
  
  La solution recommandée cible spécifiquement les points de terminaison du service Office 365 classés dans la catégorie **Optimiser** dans l’article [URL et plages d'adresses IP Office 365](https://aka.ms/o365ips). Le trafic vers ces points de terminaison est très sensible à la latence et à la limitation de la bande passante, et lui permettre de contourner le tunnel VPN peut considérablement améliorer l'expérience de l'utilisateur final et réduire la charge du réseau d’entreprise. Les connexions Office 365 qui ne constituent pas la majorité de la bande passante ou de l'empreinte de l'expérience utilisateur peuvent continuer à être acheminées via le tunnel VPN avec le reste du trafic lié à Internet. Si vous souhaitez en savoir plus, consultez l’article [la stratégie de segmentation de tunnel VPN](#the-vpn-split-tunnel-strategy).

- Peut être configurée, testée et implémentée rapidement par les clients, sans infrastructure ou configuration d’application supplémentaires. 

  En fonction de la plateforme VPN et de l’architecture réseau, l’implémentation peut prendre quelques heures. Si vous souhaitez en savoir plus, consultez l’article [Implémenter la segmentation de tunnel VPN](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Préserve la posture de sécurité des implémentations VPN client en ne modifiant pas la façon dont les autres connexions sont acheminées, notamment le trafic vers Internet

  La configuration recommandée respecte les principes de **moindre privilège** pour les exceptions de trafic VPN et permet aux clients d’implémenter une segmentation de tunnel VPN sans exposer les utilisateurs ou l’infrastructure à des risques de sécurité supplémentaires. Le trafic réseau acheminé directement vers les points de terminaison Office 365 est chiffré, validé pour son intégrité par les piles d'applications clientes Office, et étendu aux adresses IP dédiées aux services Office 365, qui sont renforcées à la fois au niveau de l'application et au niveau du réseau. Si vous souhaitez en savoir plus, consultez l’article [Des moyens alternatifs pour les professionnels de la sécurité et les services informatiques de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Est pris en charge nativement par la plupart des plateformes VPN d’entreprise

  Microsoft continue de collaborer avec des partenaires de production de solutions VPN commerciales pour aider les partenaires à développer des instructions et des modèles de configuration ciblés pour leurs solutions, conformément aux recommandations ci-dessus. Si vous souhaitez en savoir plus, consultez l’article [Guides d’utilisation pour les plateformes VPN courantes](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft recommande de concentrer la configuration de la segmentation du tunnel VPN sur les plages d’adresses IP dédiées aux services Office 365. Bien que les configurations de segmentation de tunnel basées sur des FQDN ou AppID soient possibles sur certaines plates-formes clientes VPN, elles peuvent ne pas couvrir entièrement les scénarios clés d'Office 365 et peuvent entrer en conflit avec les règles de routage VPN basées sur IP. Pour cette raison, Microsoft vous déconseille d’utiliser les FQDN Office 365 pour configurer la segmentation de tunnel VPN. L’utilisation de la configuration des FQDN peut être utile dans d’autres cas connexes, tels que les personnalisations de fichier .pac ou pour implémenter la dérivation par proxy.

Si vous souhaitez obtenir des instructions complètes sur l’implémentation, consultez l’article [Implémentation de la segmentation de tunnel VPN pour Office 365](office-365-vpn-implement-split-tunnel.md).

## <a name="the-vpn-split-tunnel-strategy"></a>La stratégie de segmentation de tunnel VPN

Les réseaux d’entreprise traditionnels sont souvent conçus pour fonctionner de façon sécurisée dans un environnement préexistant dans lequel les données, les services et les applications les plus importants sont hébergés en local et sont directement connectés au réseau interne de l’entreprise, comme la plupart des utilisateurs. Ainsi, l'infrastructure réseau est construite autour de ces éléments et, en ce sens, les succursales sont connectées au siège social via des réseaux _MPLS (Multiprotocol Label Switching)_, et les utilisateurs distants doivent se connecter au réseau d'entreprise via un VPN pour accéder à la fois aux points de terminaison locaux et à Internet. Dans ce modèle, tout le trafic provenant d’utilisateurs distants traverse le réseau d’entreprise et est acheminé vers le service cloud via un point de sortie commun.

![Configuration VPN obligatoire](media/vpn-split-tunneling/vpn-model-1.png)

_Image 2 : Une solution VPN commune pour les utilisateurs distants où tout le trafic est renvoyé vers le réseau d’entreprise, quelle que soit la destination_

Au fur et à mesure que les organisations transfèrent les données et les applications vers le cloud, ce modèle devient moins efficace car il est rapidement lourd, coûteux et non évolutif, ce qui a un impact significatif sur les performances du réseau et sur l'efficacité des utilisateurs et restreint la capacité de l'organisation à s'adapter à l'évolution des besoins. De nombreux clients Microsoft ont rapporté qu’il y a quelques années, 80% du trafic réseau avait une destination interne, mais qu’en 2020, 80% plus de trafic se connecte à une ressource cloud externe.

La crise du COVID-19 a aggravé ce problème et a exigé des solutions immédiates pour la grande majorité des organisations. De nombreux clients ont trouvé que le modèle de VPN obligatoire n’était pas suffisamment évolutif ou performant pour les scénarios de travail se faisant à 100% à distance, comme le nécessite cette crise. Des solutions rapides sont nécessaires pour que ces organisations continuent de fonctionner de manière efficace.

Pour le service Office 365, Microsoft a conçu les exigences de connectivité pour le service avec ce problème à l'esprit. Un ensemble de points de terminaison de service ciblés, étroitement contrôlés et relativement statiques peut être optimisé très simplement et rapidement afin de fournir des performances élevées aux utilisateurs accédant au service, et de réduire la charge sur l'infrastructure VPN afin qu'il puisse être utilisé par le trafic qui en a encore besoin .

Office 365 classe les points de terminaison requis pour Office 365 en trois catégories : **Optimiser**, **Autoriser** et **Par défaut**. **Optimiser** les points de terminaison est notre objectif ici et présente les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Sont-ils dédiés aux principales charges de travail Office 365 comme Exchange Online, SharePoint Online, Skype Entreprise Online et Microsoft Teams
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Ils sont sensibles au volume et / ou à la latence
- Ils sont en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représente environ 70 à 80% du volume de trafic vers le service Office 365

Cet ensemble de points de terminaison étroitement limité peut être séparé du tunnel VPN obligatoire et envoyé directement, et en toute sécurité, au service Office 365 via l'interface locale de l'utilisateur. C’est ce qu’on appelle **la segmentation du tunnel**.

Les éléments de sécurité tels que la DLP, la protection antivirus, l’authentification et le contrôle d’accès peuvent être fournis beaucoup plus efficacement contre ces points d'extrémité dans les différentes couches du service. Cela permet également de dérouter l’essentiel du volume de trafic à partir de la solution VPN, ce qui libère la capacité VPN pour le trafic important de l’entreprise qui en dépend encore. Cela devrait également supprimer la nécessité, dans de nombreux cas, de passer par un programme de mise à niveau long et coûteux pour faire face à ce nouveau mode de fonctionnement.

![Configuration de la segmentation de tunnel VPN](media/vpn-split-tunneling/vpn-model-2.png)

_Image 3 : Une solution de segmentation de tunnel VPN avec des exceptions Office 365 définies, envoyées directement au service. Tout autre trafic est renvoyé dans le réseau d'entreprise, quelle que soit la destination._

Du point de vue de la sécurité, Microsoft dispose d'une gamme de fonctionnalités de sécurité qui peuvent être utilisées pour fournir une sécurité similaire, voire améliorée, à celle fournie par l'inspection en ligne par des piles de sécurité locales. L’article de blog de l’équipe de sécurité Microsoft, [Des moyens alternatifs pour les professionnels de la sécurité et l'informatique de réaliser des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d'aujourd'hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) propose un résumé clair des fonctionnalités disponibles. Vous trouverez aussi des instructions plus détaillées dans cet article. Vous pouvez également en apprendre plus sur l’implémentation Microsoft de la segmentation de tunnel VPN en consultant l’article [Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Dans de nombreux cas, cette implémentation peut être réalisée en quelques heures, ce qui permet de résoudre rapidement l'un des problèmes les plus urgents auxquels sont confrontées les organisations, qui passent rapidement au travail à distance de façon exclusive. Si vous souhaitez obtenir des instructions sur l’implémentation de la segmentation du tunnel VPN, consultez l’article [Implémentation de la segmentation de tunnel VPN pour Office 365](office-365-vpn-implement-split-tunnel.md).

>[!NOTE]
>Microsoft s’est engagé à interrompre les modifications apportées à **optimiser** les points de terminaison pour Office 365 jusqu’au **30 juin 2020** minimum, ce qui permet aux clients de se concentrer sur d’autres défis plutôt que de maintenir la liste blanche des points de terminaison une fois initialement implémentée.

## <a name="related-topics"></a>Voir aussi

[Implémentation d'un tunnel VPN partagé pour Office 365](office-365-vpn-implement-split-tunnel.md)

[Optimisation des performances de Microsoft Office 365 pour les utilisateurs résidant en Chine](office-365-networking-china.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Test de connectivité Microsoft 365](https://aka.ms/netonboard)
