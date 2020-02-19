---
title: Évaluation du réseau Office 365 (préversion)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Évaluation du réseau Office 365 (préversion)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106304"
---
# <a name="office-365-network-assessment-preview"></a>Évaluation du réseau Office 365 (préversion)

L’évaluation du réseau Office 365 indique l’impact de l’expérience utilisateur relative à partir de la connectivité du réseau client. L’impact de toute connectivité réseau appartenant à Microsoft est exclu de cette façon pour permettre aux clients d’optimiser les conceptions réseau dont ils sont responsables.

Elle est calculée à partir de mesures qui influent sur l’expérience utilisateur dans les charges de travail Office 365 principales et affichées sous la forme d’un pourcentage d’une plage comprise entre 0 et 100.

Un score réseau très faible suggère que les clients Office 365 auront des problèmes importants de connexion ou de réactivité de l’utilisateur. Un score de 80% représente une connectivité réseau où vous ne devriez pas vous attendre à recevoir des plaintes des utilisateurs concernant votre expérience utilisateur Office 365 en raison des performances de votre réseau. À mesure que les améliorations de connectivité réseau sont apportées, ce score augmentera en même temps que l’expérience utilisateur.

>[!IMPORTANT]
>Les recommandations en matière de performances réseau, les informations et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont disponibles uniquement pour les locataires Office 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="exchange-online"></a>Exchange Online

Pour Exchange Online, la latence TCP entre l’ordinateur client et le serveur frontal Exchange est mesurée. Cela peut être influencé par la distance que le réseau traverse sur le réseau local et le réseau étendu du client. Elle peut également être affectée par les appareils ou services intermédiaires réseau qui retardent la connectivité ou provoquent le renvoi des paquets.

## <a name="sharepoint-online"></a>SharePoint Online

Pour SharePoint Online, la vitesse de téléchargement disponible pour un utilisateur pour accéder à un document est mesurée. Cela peut être influencé par la bande passante disponible sur les circuits réseau entre l’ordinateur client et le réseau Microsoft. Il est également souvent influencé par la congestion du réseau qui se trouve dans des périphériques réseau complexes ou dans des zones de non-fidélité de mauvaise qualité.

## <a name="microsoft-teams"></a>Microsoft Teams

Pour Microsoft Teams, la qualité du réseau est mesurée en tant que latence UDP, gigue UDP et perte de paquets UDP. UDP est utilisé pour la connectivité audio et vidéo d’appel et de conférence pour Microsoft Teams. Cela peut être influencé par les mêmes facteurs que pour la latence et la vitesse de téléchargement en plus des lacunes de connectivité dans la prise en charge UDP d’un réseau étant donné que le protocole UDP est configuré séparément pour le protocole TCP le plus courant.

## <a name="tenant-network-score-and-office-location-network-score"></a>Score réseau du client et score réseau de l’emplacement du Bureau

Un score réseau mesure la conception du périmètre réseau d’un emplacement de bureau sur le réseau de Microsoft. Les améliorations apportées au périmètre réseau sont les meilleures à chaque emplacement de bureau, ou lorsque la connectivité réseau est agrégée, il peut y avoir des améliorations qui ont un impact sur plusieurs emplacements.
Nous affichons un score réseau pour l’ensemble du client Office 365 sur la page de vue d’ensemble des performances réseau et un score réseau spécifique pour chaque emplacement de bureau détecté sur la page de résumé de cet emplacement.

## <a name="network-score-panel"></a>Panneau de score réseau

Chaque score réseau indique si le client ou un emplacement de bureau spécifique affiche un panneau avec des détails sur le score. Ce panneau affiche un graphique à barres du score à la fois sous forme de pourcentage et de total pour chaque charge de travail de composant, y compris les charges de travail où les données de mesure ont été reçues. Pour un score réseau d’un emplacement de bureau, nous affichons également un test qui est la médiane de tous les clients Office 365 qui ont signalé des données dans la même ville que votre emplacement de bureau.

La décomposition du score dans le panneau indique le score de chacune des charges de travail des composants.

L’historique des scores indique les 30 derniers jours de la note et le benchmark.

## <a name="related-topics"></a>Voir aussi

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Office 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Outil d’intégration réseau Office 365 dans le centre d’administration M365 (version préliminaire)](office-365-network-mac-perf-onboarding-tool.md)
