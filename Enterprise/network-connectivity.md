---
title: Connectivité réseau à Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
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
description: Office 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité d’Office 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069870"
---
# <a name="network-connectivity-to-office-365"></a>Connectivité réseau à Office 365

Office 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité d’Office 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
  
Les clients qui envisagent d’utiliser Office 365 doivent évaluer leurs besoins de connectivité Internet existants et prévisionnels dans le cadre du projet de déploiement. Pour les déploiements de classe d’entreprise, une connectivité Internet fiable et de taille appropriée est une partie essentielle de la consommation des fonctionnalités et des scénarios Office 365.
  
Les évaluations réseau peuvent être effectuées par de nombreuses personnes et organisations différentes en fonction de votre taille et de vos préférences. L’étendue réseau de l’évaluation peut également varier en fonction de l’endroit où vous vous trouvez dans votre processus de déploiement. Pour vous aider à mieux comprendre ce qu’il faut faire pour effectuer une évaluation réseau, nous avons créé un guide d’évaluation réseau pour vous aider à comprendre les options disponibles. Cette évaluation détermine les étapes et les ressources qui doivent être ajoutées au projet de déploiement pour vous permettre d’adopter correctement Office 365.
  
Une évaluation du réseau complète, telle que celle qui est prescrite dans l' [infrastructure d’opérations Skype](https://www.skypeoperationsframework.com/) , offre des solutions possibles aux défis de conception réseau, ainsi que les détails de l’implémentation. La plupart des évaluations réseau indiquent que la connectivité réseau à Office 365 peut être prise en charge avec des [modifications mineures de configuration ou de conception](https://aka.ms/manageo365endpoints) de l’infrastructure réseau existante et de sortie Internet.

Certaines évaluations indiquent que la connectivité réseau à Office 365 nécessite des investissements supplémentaires dans les composants réseau. Par exemple, les investissements dans la bande passante de réseau étendu ou l’infrastructure de routage optimisée pour prendre en charge la connectivité Internet à Office 365. Il arrive qu’une évaluation indique que la connectivité réseau à Office 365 est influencée par la réglementation ou les performances requises pour des scénarios tels que la [qualité des médias Skype entreprise Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Ces exigences supplémentaires peuvent conduire à des investissements dans l’infrastructure de connectivité Internet, l’optimisation du routage et une connectivité directe spécialisée.
  
> [!NOTE]
> L’autorisation Microsoft est requise pour utiliser ExpressRoute pour Office 365. Microsoft révise chaque demande de client et autorise uniquement l’utilisation d’ExpressRoute pour Office 365 lorsque la configuration requise par le client impose une connectivité directe. Si vous avez ces exigences, indiquez l’extrait de texte et le lien Web du règlement que vous interprétez pour signifier que la connectivité directe est requise dans le [formulaire de demande ExpressRoute pour Office 365](https://aka.ms/O365ERReview) pour commencer une révision Microsoft. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraires pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709).
  
Points clés à prendre en compte lors de la planification de votre évaluation réseau pour Office 365:
  
- Office 365 est un service sécurisé, fiable et performant qui s’exécute sur Internet public. Nous continuons à investir pour améliorer ces aspects du service. Tous les services Office 365 sont disponibles via la connectivité Internet.

- Nous optimisons en permanence les aspects principaux d’Office 365 tels que la disponibilité, l’étendue globale et les performances pour la connectivité Internet. Par exemple, de nombreux services Office 365 tirent parti d’un ensemble étendu de nœuds Edge accessibles sur Internet. Ce réseau Edge offre la meilleure proximité et les mêmes performances pour les connexions entrantes sur Internet.

- Lorsque vous envisagez d’utiliser Office 365 pour l’un des services inclus tels que les fonctionnalités vocales, vidéo ou de réunion de Skype entreprise Online, les clients doivent effectuer une évaluation du réseau de bout en bout et répondre aux besoins à l’aide de notre infrastructure d’opérations Skype. Ces clients disposeront de plusieurs options pour répondre à des exigences spécifiques en matière de connectivité Cloud, notamment ExpressRoute.

Consultez l’étude de cas de Microsoft relative à l' [optimisation des performances réseau pour Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Si vous évaluez Office 365 et que vous ne savez pas où commencer avec votre évaluation réseau ou si vous avez rencontré des problèmes de conception réseau pour lesquels vous avez besoin d’aide pour le surmonter, contactez votre équipe de compte Microsoft.
  
En outre, lisez les [principes de connectivité réseau office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité permettant de gérer le trafic Office 365 de manière sécurisée et d’obtenir les meilleures performances possibles. Cet article vous aidera à comprendre les instructions les plus récentes pour optimiser en toute sécurité la connectivité réseau Office 365.
  
Voici un petit lien que vous pouvez utiliser pour revenir: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365 (aperçu)](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)
