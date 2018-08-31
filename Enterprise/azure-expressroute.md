---
title: Azure ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Découvrez comment ExpressRoute Azure est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui est requis si vous déployez ExpressRoute Azure pour une utilisation avec Office 365.
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540362"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute pour Office 365

Découvrez comment ExpressRoute Azure est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui est requis si vous déployez ExpressRoute Azure pour une utilisation avec Office 365. Services d’infrastructure et de plateforme en cours d’exécution dans Azure bénéficieront souvent en évitant les considérations relatives à l’architecture et les performances réseau. Nous vous recommandons de ExpressRoute pour Azure dans ces cas. Logiciel en tant qu’un offres de services tels que Office 365 et Dynamics 365 ont été conçus pour être accessibles en toute sécurité et de manière fiable via Internet. En conséquence, nous ne recommandons que ExpressRoute pour ces applications dans des scénarios spécifiques. Vous pouvez lire sur la sécurité et les performances d’Internet et lorsque vous pouvez envisager ExpressRoute Azure pour Office 365 dans l’article de la [connectivité réseau vers Office 365](network-connectivity.md).

> [!NOTE]
> Démarrage du 31 juillet 2017, vous pouvez activer Microsoft Peering directement à partir de la console d’administration Azure ou à l’aide de PowerShell. Après avoir activé Microsoft Peering, vous pouvez créer des filtres d’itinéraires pour recevoir des annonces d’itinéraires BGP spécifiques. Vous aurez besoin d’autorisation pour créer des filtres pour Office 365 et que vous pouvez créer des filtres d’applications (anciennement appelé CRM Online) Dynamics 365 client Engagement à tout moment. Parler à votre équipe Microsoft Account pour obtenir l’autorisation de créer des filtres de routage Office 365. Abonnements non autorisés tente de créer des filtres d’itinéraires pour Office 365 reçoit un [message d’erreur](https://support.microsoft.com/kb/3181709)

Vous pouvez maintenant ajouter une connexion réseau directe vers Office 365 pour le trafic réseau Office 365 sélectionné. ExpressRoute Azure offre une connexion directe, des performances prévisibles et est fourni avec un SLA de 99,95 % de disponibilité pour les composants réseau Microsoft. Vous allez toujours besoin d’une connexion internet pour les services qui ne sont pas pris en charge sur Azure ExpressRoute.

## <a name="planning-azure-expressroute-for-office-365"></a>Planification ExpressRoute Azure pour Office 365

Outre la connectivité internet, vous pouvez choisir de router un sous-ensemble d’Office 365 le trafic réseau via une connexion directe offrant prévisibilité et un SLA de disponibilité 99,95 % pour les composants réseau Microsoft. ExpressRoute Azure fournit cette connexion réseau dédié à Office 365 et d’autres services de cloud Microsoft.

Que vous ayez un WAN MPLS existant, ExpressRoute peut être ajouté à votre architecture de réseau de trois façons ; via un fournisseur de colocalisation pris en charge dans le nuage exchange, un fournisseur de connexion point à point Ethernet, ou via un fournisseur de connexion MPLS. Voir quels [fournisseurs sont disponibles dans votre région](https://azure.microsoft.com/documentation/articles/expressroute-locations/). La connexion directe ExpressRoute activera connectivité aux applications décrites dans [services qu’Office 365 sont incluses ?](azure-expressroute.md#BKMK_WhatDoIGet) ci-dessous. Le trafic réseau pour toutes les autres applications et services continuera à parcourir internet.

Envisagez le diagramme de réseau de haut niveau suivant qui affiche un client Office 365 type connexion vers les centres de données de Microsoft via internet pour accéder à toutes les applications Microsoft telles que Office 365, Windows Update et TechNet. Les clients utiliser un chemin d’accès réseau similaire indépendamment si elles vous connectez à partir d’un réseau local ou d’une connexion internet indépendants.

![Connectivité du réseau Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Observez le diagramme mis à jour qui représente un client Office 365 qui utilise internet et ExpressRoute pour se connecter à Office 365. Notez que certaines connexions telles que les nœuds DNS Public et Content Delivery Network nécessitent toujours la connexion internet publique. Notez également les utilisateurs du client qui ne se trouvent pas dans leur ExpressRoute construction connectée se connectent via Internet.

![Connectivité d’Office 365 avec ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Vraiment plus d’informations ? Découvrez comment [gérer le trafic réseau avec ExpressRoute Azure pour Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) et découvrez comment [configurer ExpressRoute Azure pour Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Nous avons également enregistré une série 10 [ExpressRoute Azure pour Office 365 formation](https://channel9.msdn.com/series/aer) sur Channel 9 pour vous aider à comprendre les concepts plus en détail.

([ExpressRoute azure pour Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>Les services Office 365 sont inclus ?
<a name="BKMK_WhatDoIGet"> </a>

Le tableau suivant répertorie les services Office 365 sont pris en charge via ExpressRoute. Consultez l' [article de points de terminaison Office 365](https://aka.ms/o365endpoints) pour comprendre les demandes du réseau pour ces applications requièrent une connectivité internet.

|**Applications incluses**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Entrez<sup>1</sup> <br/> |
|Skype pour Business en ligne<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive entreprise<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portail et partagé<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> DAS connecter<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> Chacune de ces applications ont des exigences de connectivité internet non pris en charge sur ExpressRoute, consultez l' [article de points de terminaison Office 365](https://aka.ms/o365endpoints) pour plus d’informations.

Les services qui ne sont pas inclus avec ExpressRoute pour Office 365 sont les téléchargements de client Office 365 ProPlus, On-premises identité fournisseur de connexion et service Office 365 (exploité par 21 Vianet) en Chine.

([ExpressRoute azure pour Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

L’implémentation ExpressRoute requiert la participation des propriétaires de réseau et des applications et une planification pour déterminer la nouvelle [architecture de routage réseau](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), les besoins en bande passante, où la sécurité sera mis en œuvre, une haute disponibilité, et ainsi de suite. Pour mettre en œuvre ExpressRoute, vous devez :

1. Comprendre le besoin Qu'expressroute satisfait dans votre planification de connectivité Office 365. Comprendre les applications utiliseront internet ou ExpressRoute et entièrement planifier la capacité de votre réseau, sécurité et une haute disponibilité doivent dans le contexte de l’utilisation d’internet et ExpressRoute pour Office 365 le trafic.

2. Déterminer les emplacements homologation pour internet et du trafic ExpressRoute<sup>1</sup>sortant.

3. Déterminer la capacité requise sur internet et les connexions ExpressRoute.

4. Disposer d’un plan en place pour l’implémentation de la sécurité et autres contrôles de périmètre standard<sup>1</sup>.

5. Posséder un compte Microsoft Azure valid pour vous abonner au ExpressRoute.

6. Sélectionnez un modèle de connectivité et un [approuvé fournisseur](https://azure.microsoft.com/documentation/articles/expressroute-locations/). N’oubliez pas, les clients peuvent sélectionner plusieurs modèles de connectivité ou partenaires et le partenaire ne doit pas être identique à votre fournisseur de réseau existant.

7. Valider le déploiement avant de diriger le trafic vers ExpressRoute.

8. Vous pouvez [implémenter QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) et évaluer le développement régional.

<sup>1</sup> Considérations en matière de performances. Décisions ici peuvent affecter considérablement la latence qui est essentiel pour les applications telles que Skype pour les entreprises.

Pour des références supplémentaires, utilisez notre [guide de routage](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) en plus de la [documentation ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Pour acheter ExpressRoute pour Office 365, vous devez travailler avec un ou plusieurs [approuvé fournisseurs](https://azure.microsoft.com/documentation/articles/expressroute-locations/) pour mettre en service le numéro de votre choix et circuits de taille avec un abonnement ExpressRoute Premium. Il n’existe aucune licence supplémentaire sur l’achat d’Office 365.

Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Prêts à d’inscription [ExpressRoute pour Office 365](https://aka.ms/ert)?

([ExpressRoute azure pour Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Voir aussi
<a name="BKMK_End"> </a>

[Connectivité réseau à Office 365](network-connectivity.md)

[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)

[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)

[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)

[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)

[Utilisation de communautés BGP dans ExpressRoute pour les scénarios d’Office 365 (preview)](bgp-communities-in-expressroute.md)

[La qualité des médias et des performances pour la connectivité réseau dans Skype pour les entreprises en ligne](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Réseau Office 365 et réglage des performances](network-planning-and-performance.md)
