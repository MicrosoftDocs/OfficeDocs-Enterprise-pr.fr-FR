---
title: Connectivité réseau à Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 est conçu pour permettre aux clients dans le monde entier pour se connecter au service à l’aide d’une connexion internet. Comme le service évolue, la sécurité, de performances et la fiabilité d’Office 365 sont améliorées sur les clients qui utilisent internet pour établir une connexion au service.
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540568"
---
# <a name="network-connectivity-to-office-365"></a>Connectivité réseau à Office 365

Office 365 est conçu pour permettre aux clients dans le monde entier pour se connecter au service à l’aide d’une connexion internet. Comme le service évolue, la sécurité, de performances et la fiabilité d’Office 365 sont améliorées sur les clients qui utilisent internet pour établir une connexion au service.
  
Les clients de la planification de l’utilisation d’Office 365 doivent évaluer leurs besoins de connectivité internet existants et prévus dans le cadre du projet de déploiement. Pour les déploiements de classe entreprise une connectivité internet fiable et taille appropriée est un élément essentiel de la consommation des scénarios et fonctionnalités d’Office 365.
  
Évaluations réseau peuvent être réalisées par de nombreuses personnes et organisations en fonction de vos préférences et taille. L’étendue de l’évaluation du réseau peut également varient selon où vous êtes au niveau du processus de déploiement. Pour vous aider à mieux comprendre ce qu’il faut effectuer une évaluation réseau, nous avons produit un guide d’évaluation du réseau pour vous aider à comprendre les options disponibles pour vous. Cette évaluation détermine ce que les ressources et les étapes doivent être ajouté au projet de déploiement qui vous permettent d’adopter avec succès Office 365.
  
Une évaluation complète du réseau, comme les DCI préconisée l' [Infrastructure d’opérations Skype](https://www.skypeoperationsframework.com/) fournit des solutions possibles pour les problèmes de conception réseau ainsi que des détails d’implémentation. La plupart des évaluations réseau indique la connectivité réseau vers Office 365 peut être prise en charge avec [configuration secondaire ou des modifications de conception](https://aka.ms/manageo365endpoints) pour l’infrastructure de sortie d’internet et le réseau existant.

Des évaluations indique la connectivité réseau vers Office 365 nécessite des investissements supplémentaires dans des composants réseau. Par exemple, les investissements dans la bande passante WAN ou l’infrastructure de routage optimisée pour prendre en charge la connectivité internet à Office 365. Une évaluation indiquera occasionnellement connectivité réseau vers Office 365 est influencée par des exigences réglementaires et de performances pour des scénarios tels que [Skype pour la qualité des médias en ligne Business](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Ces exigences supplémentaires peuvent conduire à des investissements dans l’infrastructure de connectivité internet, optimisation de routage et une connectivité directe spécialisée.
  
> [!NOTE]
> Microsoft a modifié la façon dont le domaine de routage Peering Microsoft est passé en revue pour Azure ExpressRoute. Démarrage du 31 juillet 2017, tous les clients ExpressRoute Azure peuvent activer Microsoft Peering directement à partir de la console d’administration Azure ou via PowerShell. Après avoir activé Microsoft Peering, n’importe quel client peut créer des filtres d’itinéraires pour recevoir des annonces d’itinéraires BGP pour les applications de l’Engagement client Dynamics 365 (anciennement appelé CRM Online). Clients nécessitant ExpressRoute Azure pour Office 365 doivent obtenir révision de Microsoft avant de pouvoir créer des filtres d’itinéraires pour Office 365. Veuillez contacter votre équipe Account Microsoft pour découvrir comment demander un examen de l’activation d’Office 365 ExpressRoute. Abonnements non autorisés tente de créer des filtres d’itinéraires pour Office 365 reçoit un [message d’erreur](https://support.microsoft.com/kb/3181709).
  
Points clés à prendre en compte lors de la planification de votre évaluation du réseau pour Office 365 :
  
- Office 365 est un service d’informations sécurisé, fiable et hautes performances qui s’exécute sur le réseau internet public. Nous continuer à investir pour améliorer ces aspects du service. Tous les services Office 365 sont disponibles via la connectivité internet.

- Nous effectuons optimisation en permanence des principaux aspects d’Office 365, par exemple, disponibilité, globale atteint et connectivité en fonction des performances d’internet. Par exemple, de nombreux services Office 365 tirer parti d’un ensemble d’internet vers les nœuds edge. Ce réseau de périphérie offre les meilleures proximité et performances aux connexions bientôt sur internet.

- Lorsque vous envisagez l’utilisation d’Office 365 pour les services inclus tel que Skype pour Business Online voix, vidéo ou réunions fonctions, les clients doivent effectuer une évaluation du réseau de bout en bout et répondre à l’aide de notre infrastructure d’opérations Skype. Ces clients doivent plusieurs options pour répondre aux besoins spécifiques pour la connectivité de nuage, y compris ExpressRoute.

Jetez un œil à l’étude de cas de Microsoft [Optimisation des performances réseau pour Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Si vous êtes d’évaluation Office 365 et ne sont pas bien sûr où commencer votre évaluation du réseau ou se conception d’un réseau défis que vous avez besoin d’aide pour résoudre, veuillez fonctionnent avec l’équipe de votre compte Microsoft.
  
En outre, lisez les [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité de gérer en toute sécurité le trafic d’Office 365 et d’obtenir les meilleures performances possibles. Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau.
  
Voici un lien court, vous pouvez utiliser pour revenir : [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Réseau Office 365 et réglage des performances](network-planning-and-performance.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Utilisation de communautés BGP dans ExpressRoute pour les scénarios d’Office 365 (preview)](bgp-communities-in-expressroute.md)
  
[La qualité des médias et des performances pour la connectivité réseau dans Skype pour les entreprises en ligne](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)
