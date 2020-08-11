---
title: Évaluation de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
ms.openlocfilehash: eae7e56c13ab0d0799226c834dd7d9092c8f9551
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605800"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Évaluation de la connectivité réseau Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
  
Les clients qui envisagent d’utiliser Microsoft 365 doivent évaluer leurs besoins de connectivité Internet existants et prévisionnels dans le cadre du projet de déploiement. Pour les déploiements de classe d’entreprise, une connectivité Internet fiable et de taille appropriée est une partie essentielle de la consommation des fonctionnalités et des scénarios de Microsoft 365.
  
Les évaluations réseau peuvent être effectuées par de nombreuses personnes et organisations différentes en fonction de votre taille et de vos préférences. L’étendue réseau de l’évaluation peut également varier en fonction de l’endroit où vous vous trouvez dans votre processus de déploiement. Pour vous aider à mieux comprendre ce qu’il faut faire pour effectuer une évaluation réseau, nous avons créé un guide d’évaluation réseau pour vous aider à comprendre les options disponibles. Cette évaluation détermine les étapes et les ressources qui doivent être ajoutées au projet de déploiement pour vous permettre d’adopter correctement Microsoft 365.
  
Une évaluation réseau complète fournira des solutions aux défis de conception réseau, ainsi que les détails de l’implémentation. Certaines évaluations réseau indiquent que la connectivité réseau optimale à Microsoft 365 peut être prise en charge avec des modifications de configuration ou de conception mineures sur l’infrastructure de sortie réseau et Internet existante.

Certaines évaluations indiquent que la connectivité réseau à Microsoft 365 nécessite des investissements supplémentaires dans les composants réseau. Par exemple, les réseaux d’entreprise qui s’étendent sur des succursales et dans plusieurs régions géographiques peuvent nécessiter des investissements dans des solutions SD-WAN ou une infrastructure de routage optimisée pour prendre en charge la connectivité Internet à Microsoft 365. Il arrive qu’une évaluation indique que la connectivité réseau à Microsoft 365 est influencée par la réglementation ou les performances requises pour des scénarios tels que la [qualité des médias Skype entreprise Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Ces exigences supplémentaires peuvent conduire à des investissements dans l’infrastructure de connectivité Internet, l’optimisation du routage et une connectivité directe spécialisée.

Certaines ressources pour vous aider à évaluer votre réseau :

- Consultez la rubrique [microsoft 365 Network Connectivity Overview](office-365-networking-overview.md) pour obtenir des informations conceptuelles sur la mise en réseau Microsoft 365.
- Consultez les [principes de connectivité réseau de microsoft 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité permettant de gérer le trafic Microsoft 365 de manière sécurisée et d’obtenir les meilleures performances possibles.
- Inscrivez-vous à [Microsoft FastTrack](https://www.microsoft.com/fasttrack) pour obtenir une assistance interactive concernant la planification, la conception et le déploiement de Microsoft 365. 
- Consultez la section [test de connectivité de Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) ci-dessous pour exécuter des tests de connectivité de base qui fournissent des conseils spécifiques sur les améliorations de connectivité réseau pouvant être effectuées entre un emplacement utilisateur donné et Microsoft 365.

> [!NOTE]
> L’autorisation Microsoft est requise pour utiliser ExpressRoute pour Office 365. Microsoft révise chaque demande de client et autorise uniquement l’utilisation d’ExpressRoute pour Office 365 lorsque la configuration requise par le client impose une connectivité directe. Si vous avez ces exigences, indiquez l’extrait de texte et le lien Web du règlement que vous interprétez pour signifier que la connectivité directe est requise dans le [formulaire de demande ExpressRoute pour Office 365](https://aka.ms/O365ERReview) pour commencer une révision Microsoft. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraires pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709).
  
Points clés à prendre en compte lors de la planification de votre évaluation réseau pour Microsoft 365 :
  
- Microsoft 365 est un service sécurisé, fiable et performant qui s’exécute sur Internet public. Nous continuons à investir pour améliorer ces aspects du service. Tous les services Microsoft 365 sont disponibles via la connectivité Internet.

- Nous optimisons constamment les aspects principaux de Microsoft 365 tels que la disponibilité, l’étendue globale et les performances pour la connectivité Internet. Par exemple, de nombreux services Microsoft 365 tirent parti d’un ensemble de nœuds Edge accessibles sur Internet. Ce réseau Edge offre la meilleure proximité et les mêmes performances pour les connexions entrantes sur Internet.

- Lorsque vous envisagez d’utiliser Microsoft 365 pour n’importe quel service inclus, comme teams ou Skype entreprise Online, les fonctionnalités vocales, vidéo ou de réunion, les clients doivent terminer l’évaluation du réseau de bout en bout et répondre aux exigences de connectivité à l’aide de [Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Si vous évaluez Microsoft 365 et que vous ne savez pas où commencer avec votre évaluation du réseau ou si vous avez rencontré des problèmes de conception réseau pour lesquels vous avez besoin d’aide pour surmonter votre concours, contactez votre équipe de compte Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Test de connectivité de Microsoft 365

Le [test de connectivité de Microsoft 365](https://aka.ms/netonboard) est un outil d’évaluation réseau de preuve de concept (POC) qui exécute des tests de connectivité de base sur votre client Microsoft 365 et fait des recommandations de conception réseau spécifiques pour des performances optimales de Microsoft 365. L’outil met en évidence les choix courants de la conception du périmètre du réseau d’entreprise, qui sont utiles pour la navigation Web Internet, mais qui influent sur les performances des applications SaaS volumineuses telles que Microsoft 365.

L’outil d’intégration réseau effectue les opérations suivantes :

- Détecte votre emplacement ou vous pouvez spécifier un emplacement pour le tester
- Vérifie l’emplacement de la sortie de votre réseau
- Teste le chemin d’accès réseau vers le volet frontal du service Microsoft 365 le plus proche
- Fournit des tests avancés à l’aide d’une application Windows 10 téléchargeable qui fait des recommandations de conception du réseau de périmètre liées aux serveurs proxy, aux pare-feux et au DNS. L’outil exécute également des tests de performances pour Skype entreprise Online, Microsoft Teams, SharePoint Online et Exchange Online.

L’outil comporte deux composants : une interface utilisateur basée sur un navigateur qui recueille des informations de connectivité de base et une application Windows 10 téléchargeable qui exécute les tests avancés et renvoie des données d’évaluation supplémentaires.

L’outil basé sur un navigateur affiche les informations suivantes :

- Onglet résultats et impact
  - Emplacement sur une carte de la porte d’appel du service en cours d’utilisation
  - Emplacement sur une carte d’autres portes de service qui fournirait une connectivité optimale
  - Performances relatives comparées aux autres clients Microsoft 365 près de chez vous
- Onglet Détails et solutions
  - Emplacement de l’utilisateur par ville et par pays
  - Emplacement de sortie réseau par ville, État et pays
  - Distance entre l’utilisateur et le réseau
  - Emplacement de la porte avant du service Exchange Online Microsoft 365
  - Façade de Microsoft 365 Exchange Online Service (s) pour l’emplacement de l’utilisateur
  - Clients de votre région de métro avec de meilleures performances

L’application téléchargeable de tests avancés fournit les informations supplémentaires suivantes :

- Onglet Détails et solutions (ajouté)
  - Passerelle par défaut de l’utilisateur
  - Serveur DNS client
  - Solveur récursive DNS client
  - Serveur DNS Exchange Online
  - Serveur DNS SharePoint Online
  - Identification du serveur proxy
  - Vérification de la connectivité multimédia
  - Perte de paquets de la qualité des médias
  - Latence de la qualité des médias
  - Gigue de la qualité des médias
  - Réorganisation des paquets de qualité des médias
- Tests de connectivité vers plusieurs points de terminaison propres aux fonctionnalités
- Diagnostics de chemin d’accès réseau qui incluent les données tracert et de latence pour les services Exchange Online, SharePoint Online et Teams

Pour plus d’informations sur le test de connectivité de Microsoft 365, consultez le billet de blog [microsoft 365 Connectivity Test POC avec New Network Design Recommendations](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) . Des informations sur les mises à jour futures de cet outil et d’autres mises à jour de la mise en réseau Microsoft 365 seront publiées sur le blog de [mise en réseau Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) .
  
Voici un petit lien que vous pouvez utiliser pour revenir : [ https://aka.ms/o365networkconnectivity .](https://aka.ms/o365networkconnectivity)
  
## <a name="related-topics"></a>Rubriques connexes

[Vue d’ensemble de la connectivité réseau Microsoft 365](office-365-networking-overview.md)

[Principes de connectivité réseau Microsoft 365](https://aka.ms/o365networkingprinciples)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](office-365-ip-web-service.md)

[Réglage des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
