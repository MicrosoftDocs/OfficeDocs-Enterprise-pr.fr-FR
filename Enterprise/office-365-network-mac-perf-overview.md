---
title: Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Vue d’ensemble des recommandations en matière de performances réseau dans le centre d’administration 365 de Microsoft (version préliminaire)
ms.openlocfilehash: f2ff012d20c799925c571d8065e28859c4c81f71
ms.sourcegitcommit: 44a0e9a134373eb0d1292761089a6557b01ac327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "43081716"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)

Le centre d’administration Microsoft 365 inclut désormais des métriques de performances en temps réel collectées à partir de votre client Office 365 et accessibles uniquement par les utilisateurs administratifs de votre client. **Network Insights and performance Recommendations** et **évaluations réseau** sont affichées dans le centre d’administration 365 de Microsoft <https://portal.microsoft.com/adminportal/home#/networkperformance>à l’adresse. Vous trouverez la page dans le volet de navigation sous **intégrité | Performances réseau**.

![Page des performances du réseau](Media/m365-mac-perf/m365-mac-perf-page-nav.png)

Lorsque vous accédez à la page performances réseau, vous verrez un volet de vue d’ensemble contenant une carte des performances réseau globales, une évaluation du réseau pour l’étendue de l’ensemble du client, ainsi qu’une liste des problèmes actuels. À partir de la vue d’ensemble, vous pouvez accéder à des mesures et des problèmes de performances réseau spécifiques par emplacement. Pour plus d’informations, reportez-vous à [Network performance Overview dans le centre d’administration 365 de Microsoft](#network-performance-overview-in-the-microsoft-365-admin-center).

## <a name="pre-requisites-for-connectivity-measurements-to-appear"></a>Conditions préalables à l’affichage des mesures de connectivité

Pour que les mesures de connectivité apparaissent, vous devez disposer d’au moins deux ordinateurs en cours d’exécution sur chaque emplacement de bureau qui prennent en charge les conditions préalables. Le client de synchronisation OneDrive entreprise 19,232 ou version ultérieure doit être installé sur chaque ordinateur. Pour plus d’informations, consultez les [notes de publication de OneDrive](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0).

Le service d’emplacement Windows doit être accepté sur les ordinateurs. Vous pouvez le tester en exécutant l’application **Maps** et en vous localisant. Il peut être activé sur un seul ordinateur avec l'**emplacement** de**confidentialité** -> des **paramètres** -> où le paramètre « autoriser les applications à accéder à votre emplacement » doit être activé. Le consentement des services d’emplacement Windows peut être déployé sur des PC à l’aide de MDM ou de la stratégie de groupe avec le paramètre _LetAppsAccessLocation_.

Les machines doivent disposer de la mise en réseau Wi-Fi plutôt que d’un câble Ethernet. Les machines disposant d’un câble Ethernet ne disposent pas d’informations d’emplacement précises.

Les exemples de mesures et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été satisfaites.

## <a name="how-do-i-use-this-information"></a>Comment utiliser ces informations ?

**Network Insights**, leurs recommandations de performances et évaluations réseau associées sont destinées à faciliter la conception des périmètres réseau pour vos emplacements de bureau. Chaque vue fournit des informations détaillées sur les caractéristiques de performances d’un problème commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client. **Recommandations** en matière de performances pour chaque modèle Network Insight apporter des modifications de conception de l’architecture réseau spécifique que vous pouvez apporter pour améliorer l’expérience utilisateur liée à la connectivité réseau Office 365. L’évaluation du réseau montre l’impact de la connectivité réseau sur l’expérience utilisateur, ce qui permet de comparer différentes connexions réseau d’emplacement utilisateur.

Les **évaluations de réseau** convertissent un agrégat de nombreuses métriques de performances réseau en un instantané de l’état de votre réseau d’entreprise, représenté par une valeur de points comprise entre 1-100. Les évaluations réseau sont étendues à la fois à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, offrant ainsi aux administrateurs Office 365 un moyen facile de saisir instantanément un Gestalt de l’état du réseau de l’entreprise et d’accéder rapidement à un rapport détaillé sur un emplacement Office global.

Les entreprises complexes disposant de plusieurs emplacements de bureau et d’architectures de périmètre réseau non négligeables peuvent tirer parti de ces informations lors de leur intégration initiale à Office 365 ou pour corriger les problèmes de performances réseau découverts avec la croissance de l’utilisation. Cette fonction n’est généralement pas nécessaire pour les petites entreprises qui utilisent Office 365, ni dans les entreprises qui disposent déjà d’une connectivité réseau simple et directe. Les entreprises disposant de plus de 500 utilisateurs et de plusieurs emplacements de bureau sont censées tirer le meilleur parti.

>[!IMPORTANT]
>Les informations relatives au réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="enterprise-network-connectivity-challenges"></a>Défis de connectivité du réseau d’entreprise

![Réseau client vers Cloud](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

De nombreuses entreprises ont des configurations de périmètre réseau qui se sont produites au fil du temps et qui sont principalement conçues pour prendre en charge l’accès aux sites Web des employés où la plupart des sites Web ne sont pas connus à l’avance et ne sont pas approuvés. L’objectif de ce site est d’éviter les attaques de programmes malveillants et de pêche à partir de ces sites Web inconnus. Cette stratégie de configuration réseau, tout en étant utile pour des raisons de sécurité, peut entraîner une dégradation des performances utilisateur d’Office 365 et de l’expérience utilisateur.

## <a name="how-we-can-solve-these-challenges"></a>Comment nous pouvons résoudre ces problèmes

Les entreprises peuvent améliorer l’expérience utilisateur générale et sécuriser leur environnement en suivant les [principes de connectivité d’Office 365](https://aka.ms/pnc) et en utilisant la fonctionnalité de performances réseau du centre d’administration Microsoft 365. Dans la plupart des cas, le suivi de ces principes généraux aura un impact positif significatif sur la latence des utilisateurs finaux, la fiabilité des services et les performances globales d’Office 365.

Microsoft est parfois invité à enquêter sur les problèmes de performances réseau avec Office 365 pour les grandes entreprises et celles-ci ont fréquemment une cause principale liée à l’infrastructure de sortie du réseau des clients. Lors de la détection d’une cause racine commune d’un problème de périmètre réseau client, nous cherchons à identifier les mesures de test simples qui l’identifient. Un test avec un seuil de mesure qui identifie un problème spécifique est utile, car nous pouvons tester la même mesure dans n’importe quel emplacement, indiquer si cette cause première existe et la partager en tant que Network Insight avec l’administrateur.

Certains aspects du réseau indiquent simplement un problème qui nécessite une nouvelle enquête. Un Network Insight où nous avons suffisamment de tests pour afficher une action corrective spécifique pour corriger la cause principale est mentionné comme une **action recommandée**. Ces recommandations, basées sur des métriques vivantes qui révèlent des valeurs situées en dehors d’un seuil prédéterminé, sont bien plus importantes que les conseils de bonne pratique générale, car ils sont spécifiques à votre environnement et affichent l’amélioration effective une fois que les modifications recommandées ont été apportées.

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Vue d’ensemble des performances réseau dans le centre d’administration Microsoft 365

Microsoft a des mesures réseau existantes à partir de plusieurs clients de bureau et Web Office qui prennent en charge le fonctionnement d’Office 365. Ces mesures sont désormais utilisées pour fournir des informations sur la conception de l’architecture réseau et une évaluation des performances réseau qui s’affichent dans la page **performances réseau** du centre d’administration 365 de Microsoft.

Par défaut, les informations d’emplacement approximatives associées aux mesures du réseau identifient la ville où se trouvent les appareils clients. L’évaluation du réseau à chaque emplacement est illustrée par la couleur et le nombre d’utilisateurs par rapport à chaque emplacement est représenté par la taille du cercle.

![Plan de présentation du réseau](Media/m365-mac-perf/m365-mac-perf-overview-map.png)

La page vue d’ensemble indique également l’évaluation du réseau pour le client sous la forme d’une moyenne pondérée sur tous les bureaux.

![Évaluation du réseau](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Informations spécifiques sur les performances et les informations du réseau d’emplacement de bureau

La sélection d’un emplacement de bureau ouvre une page de résumé spécifique à l’emplacement présentant les détails de la sortie réseau identifiée à partir de mesures pour cet emplacement de bureau.

![Informations sur le réseau, détails par emplacement](Media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

La page de résumé des emplacements Office indique également l’évaluation du réseau de l’emplacement, l’historique de l’évaluation du réseau, une comparaison de l’évaluation de cet emplacement aux autres clients de la même ville, ainsi qu’une liste d’informations et de recommandations spécifiques que vous pouvez entreprendre pour améliorer les performances et la fiabilité du réseau. Les emplacements avec des recommandations spécifiques peuvent également inclure une amélioration potentielle de la latence.

Les comparaisons entre les clients de la même ville sont basées sur l’attente que tous les clients ont un accès égal aux fournisseurs de services réseau, à l’infrastructure de télécommunications et aux points de présence réseau Microsoft voisins.

![Emplacements des informations sur le réseau](Media/m365-mac-perf/m365-mac-perf-locations.png)

L’onglet Détails de la page emplacement du Bureau affiche les résultats de mesure spécifiques qui ont été utilisés pour trouver des informations, des recommandations et l’évaluation du réseau. Cela permet aux ingénieurs réseau de valider les recommandations et facteurs dans les contraintes ou les spécificités de leur environnement.

![Détails spécifiques à l’emplacement](Media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

Pour les clients qui souhaitent améliorer la précision des mesures et des recommandations propres à l’emplacement, nous autorisons la saisie d’informations plus spécifiques. Cela permet de réduire les approximations inhérentes aux informations d’emplacement disponibles pour les mesures réseau. Pour modifier l’adresse d’un emplacement de bureau spécifique <functionality not there yet>,.

## <a name="import-undiscovered-office-locations"></a>Importer des emplacements de bureau inconnus

L’onglet **emplacement** des performances du réseau affiche une liste d’emplacements Office automatiquement découverts à partir de la télémétrie réseau. Ces emplacements de bureau sont des villes découvertes. Vous pouvez ajouter manuellement des emplacements spécifiques dans ces villes si elles ne s’affichent pas automatiquement dans la liste en les important à partir d’un fichier CSV. Si les emplacements de bureau ne s’affichent pas du tout, il est recommandé de dépanner la raison pour laquelle les mesures de leur réseau ne s’affichent pas au lieu d’ajouter simplement l’emplacement ici. Vous pouvez également mettre à jour la valeur d’adresse des emplacements Office existants.

Dans le fichier CSV, l’emplacement de ville découvert est étiqueté **ville**, et un emplacement de bureau ajouté manuellement est **emplacement**.

1. Dans la fenêtre principale _connectivité à Microsoft 365_ , cliquez sur l’onglet **emplacements** .
1. Cliquez sur le bouton **Importer** situé au-dessus de la liste emplacements. Le menu volant **importer des emplacements de bureau** s’affiche.

   ![Message d’erreur d’importation CSV](Media/m365-mac-perf/m365-mac-perf-import.png)

1. Cliquez sur le lien **Télécharger les emplacements Office actifs (. csv)** pour exporter la liste des emplacements actuels vers un fichier CSV, puis enregistrez-le sur votre disque dur local. Vous obtiendrez un fichier CSV correctement formaté vers lequel vous pouvez ajouter des emplacements. Vous pouvez laisser les emplacements exportés tels quels ; elles ne sont pas dupliquées lorsque vous importez le fichier CSV mis à jour. Si vous souhaitez modifier l’adresse d’un emplacement existant, celle-ci est mise à jour lorsque vous importez le fichier CSV. Vous ne pouvez pas modifier l’adresse d’une ville découverte.
1. Ouvrez le fichier CSV et ajoutez vos emplacements en remplissant les champs suivants sur une nouvelle ligne pour chaque emplacement que vous souhaitez ajouter. Laissez tous les autres champs vides ; les valeurs que vous entrez dans d’autres champs seront ignorées.
   1. **Address** (Required) : adresse physique de l’Office
   1. **Latitude** (facultatif) : renseigné à partir de la recherche de cartes Bing si vide
   1. **Longitude** (facultative) : renseigné à partir de la recherche de cartes Bing si vide
   1. **Plages d’adresses IP sortantes 1-5** (facultatif) : pour chaque plage, entrez le nom du circuit suivi d’une liste d’adresses CIDR IPv4 ou IPv6 valides séparées par des espaces. Ces valeurs ne sont utilisées que si vous avez activé l’intégration SDWAN pour un emplacement de bureau donné.
1. Une fois que vous avez ajouté vos emplacements de bureau et enregistré le fichier, cliquez sur le bouton **Parcourir** en regard du champ **charger le champ terminé** , puis sélectionnez le fichier csv enregistré.
1. Le fichier sera automatiquement validé. S’il existe des erreurs de validation, le message d’erreur indique que _le fichier d’importation contient des erreurs. Examinez les erreurs, corrigez le fichier d’importation, puis réessayez._ Cliquez sur le lien Détails de l' **erreur Open** pour obtenir la liste des erreurs de validation de champ spécifiques.

   ![Message d’erreur d’importation CSV](Media/m365-mac-perf/m365-mac-perf-import-error.png)

1. S’il n’y a pas d’erreurs dans le fichier, le message _le rapport est prêt. Emplacements trouvés x à ajouter et emplacements à mettre à jour._ Cliquez sur le bouton **Importer** pour charger le fichier CSV.

   ![Message d’importation CSV prêt](Media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>FAQ

### <a name="what-is-an-office-365-service-front-door"></a>Qu’est-ce qu’une trappe frontale de service Office 365 ?

Le volet Office 365 service est un point d’entrée sur le réseau mondial de Microsoft où les clients et les services Office mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Office 365, il est recommandé que votre connexion réseau soit interrompue dans le volet frontal Office 365 le plus proche de votre ville ou de votre métro.

>[!NOTE]
>Le service frontal Office 365 service n’a pas de relation directe avec le produit du service de la porte frontale Azure disponible sur Azure Marketplace.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>Qu’est-ce qu’une trappe frontale d’Office 365 service optimale ?

Une porte de service frontale Office 365 optimale est celle qui est la plus proche de la sortie de votre réseau, généralement dans votre ville ou votre région de métro. Utilisez l' [outil d’intégration réseau office 365](office-365-network-mac-perf-onboarding-tool.md) pour déterminer l’emplacement de votre service Office 365 en cours d’utilisation et des portes frontales de service optimale. Si l’outil détermine que votre porte avant de l’utilisation est optimale, vous vous connectez de manière optimale au réseau global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Elle est également identifiée comme l’emplacement où vous avez un périphérique de traduction d’adresses réseau (NAT) et généralement l’endroit où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement Internet sortant, cela peut indiquer une sorte de trajet WAN important.

## <a name="related-topics"></a>Sujets associés

[Informations sur le réseau Office 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Office 365 (préversion)](office-365-network-mac-perf-score.md)

[Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Office 365 (préversion)](office-365-network-mac-location-services.md)
