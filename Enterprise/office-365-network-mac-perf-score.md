---
title: Microsoft 365 Network Assessment (aperçu)
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
description: Microsoft 365 Network Assessment (aperçu)
ms.openlocfilehash: 3554c86b94e6b24cf82231da640b7e010fe07c11
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612894"
---
# <a name="microsoft-365-network-assessment-preview"></a>Microsoft 365 Network Assessment (aperçu)

Dans la page 365 connectivité du centre d’administration 365 de Microsoft, les **évaluations réseau** convertissent un ensemble de nombreuses mesures de performances réseau en un instantané de l’état de votre réseau d’entreprise, représenté par une valeur de points comprise entre 1-100. Les évaluations réseau sont étendues à la fois à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, ce qui permet aux administrateurs de Microsoft 365 de mieux appréhender instantanément un Gestalt de l’état du réseau de l’entreprise et d’accéder rapidement à un rapport détaillé sur un emplacement Office global.

La valeur points d’évaluation réseau est une mesure moyenne de la latence, de la bande passante, de la vitesse de téléchargement et des mesures de qualité de la connexion compilées en direct au moment où elles sont affichées. Les mesures de performances des réseaux appartenant à Microsoft sont exclues de ces mesures afin de s’assurer que les résultats de l’évaluation ne sont pas ambigus et spécifiques au réseau d’entreprise.

![Valeur d’évaluation du réseau](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Une évaluation réseau très faible suggère que les clients Microsoft 365 auront des problèmes importants pour se connecter au client ou maintenir une expérience utilisateur réactive, tandis qu’une valeur élevée indique un réseau correctement configuré avec peu de problèmes de performances. Une valeur de 80% représente une base saine, dans laquelle vous ne devez pas vous attendre à recevoir des plaintes d’utilisateur normales concernant la connectivité ou la réactivité Microsoft 365 en raison des performances du réseau. À mesure que des améliorations de connectivité réseau itératives sont apportées, cette valeur augmente en fonction de l’expérience utilisateur.

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="network-assessment-panel"></a>Panneau d’évaluation du réseau

Chaque évaluation réseau, qu’elle soit portée au client ou à un emplacement de bureau spécifique, présente un panneau détaillant les détails de l’évaluation. Ce panneau affiche un graphique à barres de l’évaluation à la fois sous forme de pourcentage et de total pour chaque charge de travail de composant, y compris les charges de travail où les données de mesure ont été reçues. Pour une évaluation du réseau d’emplacements de bureau, nous affichons également un benchmark qui est la médiane de tous les clients Microsoft 365 qui ont signalé des données dans la même ville que votre emplacement de bureau.

![Exemple de valeur d’évaluation du réseau](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

La **répartition** de l’évaluation dans le panneau indique l’évaluation de chacune des charges de travail des composants.

L' **historique** de l’évaluation indique les 30 derniers jours de l’évaluation et du benchmark.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Évaluations du réseau client et évaluation du réseau de l’emplacement Office

Une évaluation réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Les améliorations apportées au périmètre réseau sont les meilleures à chaque emplacement de bureau, ou lorsque la connectivité réseau est agrégée, il peut y avoir des améliorations qui ont un impact sur plusieurs emplacements.

Nous affichons une valeur d’évaluation réseau pour l’ensemble du client Microsoft 365 sur la page de présentation des performances réseau et une valeur spécifique pour chaque emplacement Office détecté sur la page de résumé de cet emplacement.

## <a name="exchange-online"></a>Exchange Online

Pour Exchange Online, la latence TCP entre l’ordinateur client et le serveur frontal Exchange est mesurée. Cela peut être influencé par la distance que le réseau traverse sur le réseau local et le réseau étendu du client. Elle peut également être affectée par les appareils ou services intermédiaires réseau qui retardent la connectivité ou provoquent le renvoi des paquets.

## <a name="sharepoint-online"></a>SharePoint Online

Pour SharePoint Online, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document est mesurée. Cela peut être influencé par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau Microsoft. Il est également souvent influencé par la congestion du réseau qui se trouve dans des périphériques réseau complexes ou dans des zones de non-fidélité de mauvaise qualité.

## <a name="microsoft-teams"></a>Microsoft Teams

Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP. UDP est utilisé pour la connectivité audio et vidéo d’appel et de conférence pour Microsoft Teams. Cela peut être influencé par les mêmes facteurs que pour la latence et la vitesse de téléchargement en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau étant donné que le protocole UDP est configuré séparément pour le protocole TCP le plus courant.

## <a name="related-topics"></a>Voir aussi

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Test de connectivité Microsoft 365 dans le centre d’administration M365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)
