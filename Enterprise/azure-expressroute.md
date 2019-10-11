---
title: Azure ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
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
description: Découvrez comment Azure ExpressRoute est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui sera requis si vous déployez Azure ExpressRoute pour une utilisation avec Office 365.
ms.openlocfilehash: 360cae39010f35b5a921ec95f6e8ed1d02afb808
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435408"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute pour Office 365

*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 Enterprise*

Découvrez comment Azure ExpressRoute est utilisé avec Office 365 et comment planifier le projet d’implémentation réseau qui sera requis si vous déployez Azure ExpressRoute pour une utilisation avec Office 365. Les services d’infrastructure et de plateforme exécutés dans Azure tireront souvent parti de l’architecture réseau et des considérations relatives aux performances. Nous vous recommandons d’utiliser ExpressRoute pour Azure dans ces cas. Les logiciels en tant qu’offres de service comme Office 365 et Dynamics 365 ont été conçus pour être accessibles en toute sécurité et fiabilité via Internet. Vous trouverez des informations sur les performances et la sécurité d’Internet et sur la façon dont vous pouvez envisager d’utiliser Azure ExpressRoute pour Office 365 dans l’article évaluation de la [connectivité réseau office 365](assessing-network-connectivity.md).

> [!NOTE]
> L’autorisation Microsoft est requise pour utiliser ExpressRoute pour Office 365. Microsoft révise chaque demande de client et autorise l’utilisation d’ExpressRoute pour Office 365 lorsque la configuration requise par le client impose une connectivité directe. Si vous avez ces exigences, indiquez l’extrait de texte et le lien Web du règlement que vous interprétez pour signifier que la connectivité directe est requise dans le [formulaire de demande ExpressRoute pour Office 365](https://aka.ms/O365ERReview) pour commencer une révision Microsoft. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraires pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709).

Vous pouvez désormais ajouter une connexion réseau directe à Office 365 pour le trafic réseau Office 365 sélectionné. Azure ExpressRoute offre une connexion directe, des performances prévisibles et est accompagné d’un contrat SLA de 99,95% pour les composants réseau Microsoft. Vous aurez toujours besoin d’une connexion Internet pour les services qui ne sont pas pris en charge par Azure ExpressRoute.

## <a name="planning-azure-expressroute-for-office-365"></a>Planification d’Azure ExpressRoute pour Office 365

Outre la connectivité Internet, vous pouvez choisir d’acheminer un sous-ensemble du trafic réseau Office 365 via une connexion directe offrant une prévisibilité et un contrat SLA de 99,95% pour les composants réseau Microsoft. Azure ExpressRoute fournit cette connexion réseau dédiée à Office 365 et d’autres services Cloud Microsoft.

Qu’il s’agisse d’un réseau étendu MPLS existant, ExpressRoute peut être ajouté à votre architecture réseau de trois façons différentes ; par le biais d’un fournisseur de colocalisation Exchange Cloud pris en charge, d’un fournisseur de connexion point à point Ethernet ou d’un fournisseur de connexion MPLS. Consultez la rubrique relative [aux fournisseurs disponibles dans votre région](https://azure.microsoft.com/documentation/articles/expressroute-locations/). La connexion ExpressRoute directe permettra la connectivité aux applications décrites dans [Quels services Office 365 sont inclus ?](azure-expressroute.md#BKMK_WhatDoIGet) ci-dessous. Le trafic réseau de toutes les autres applications et services continuera de traverser Internet.

Considérez le diagramme de réseau de haut niveau suivant qui montre un client Office 365 classique se connectant aux centres de donnes de Microsoft via Internet pour accéder à toutes les applications Microsoft telles que Office 365, Windows Update et TechNet. Les clients utilisent un chemin d’accès réseau similaire, qu’ils se connectent à partir d’un réseau local ou d’une connexion Internet indépendante.

![Connectivité réseau Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Examinez maintenant le diagramme mis à jour qui illustre un client Office 365 qui utilise Internet et ExpressRoute pour se connecter à Office 365. Notez que certaines connexions telles que les nœuds de réseau DNS public et de distribution de contenu nécessitent toujours la connexion Internet publique. Notez également que les utilisateurs du client qui ne sont pas situés dans le bâtiment connecté à ExpressRoute sont connectés sur Internet.

![Connectivité Office 365 avec ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Souhaitez-vous toujours obtenir plus d’informations ? Découvrez comment [gérer votre trafic réseau avec Azure ExpressRoute pour office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) et découvrez comment [configurer Azure ExpressRoute pour Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Nous avons également enregistré une série de formation de 10 parties sur [Azure ExpressRoute pour Office 365](https://channel9.msdn.com/series/aer) sur Channel 9 afin de mieux comprendre les concepts.

## <a name="what-office-365-services-are-included"></a>Quels sont les services Office 365 inclus ?
<a name="BKMK_WhatDoIGet"> </a>

Le tableau suivant répertorie les services Office 365 pris en charge sur ExpressRoute. Consultez l’article relatif aux [points de terminaison Office 365](https://aka.ms/o365endpoints) pour savoir quelles demandes réseau pour ces applications nécessitent une connectivité Internet.

|**Applications incluses**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype entreprise Online<sup>1</sup> <br/> Microsoft teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive entreprise<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portail et partage<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD Connect<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1</sup> Chacune de ces applications a des exigences de connectivité Internet qui ne sont pas prises en charge sur ExpressRoute, consultez l’article relatif aux [points de terminaison Office 365](https://aka.ms/o365endpoints) pour plus d’informations.

Les services qui ne sont pas inclus dans ExpressRoute pour Office 365 sont les téléchargements de client Office 365 ProPlus, la connexion au fournisseur d’identité sur site et Office 365 (géré par 21 VIANET) du service en Chine.

## <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

L’implémentation de ExpressRoute nécessite l’implication des propriétaires de réseau et d’application et nécessite une planification soignée pour déterminer la nouvelle [architecture de routage réseau](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), les besoins en bande passante, où la sécurité sera implémentée, la haute disponibilité et ainsi de suite. Pour implémenter ExpressRoute, vous devez :

1. Maîtrisez entièrement les besoins ExpressRoute en fonction de la planification de la connectivité d’Office 365. Comprendre les applications qui utiliseront Internet ou ExpressRoute et planifier entièrement les besoins en matière de capacité réseau, de sécurité et de haute disponibilité dans le contexte de l’utilisation d’Internet et de ExpressRoute pour le trafic Office 365.

2. Déterminez les emplacements de sortie et d’homologation pour le trafic Internet et ExpressRoute<sup>1</sup>.

3. Déterminez la capacité requise sur Internet et les connexions ExpressRoute.

4. Disposer d’un plan de mise en place de la sécurité et d’autres contrôles de périmètre standard<sup>1</sup>.

5. Disposer d’un compte Microsoft Azure valide pour s’abonner à ExpressRoute.

6. Sélectionnez un modèle de connectivité et un [fournisseur approuvé](https://azure.microsoft.com/documentation/articles/expressroute-locations/). N’oubliez pas que les clients peuvent sélectionner plusieurs modèles ou partenaires de connectivité et que le partenaire n’a pas besoin d’être le même que celui de votre fournisseur de réseau existant.

7. Validez le déploiement avant de diriger le trafic vers ExpressRoute.

8. [Implémentez QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) et évaluez l’expansion régionale.

<sup>1</sup> Considérations importantes en matière de performances. Les décisions peuvent avoir un impact considérable sur la latence, ce qui est essentiel pour les applications telles que Skype entreprise.

Pour obtenir des références supplémentaires, utilisez notre [Guide de routage](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) en plus de la [documentation ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Pour acheter ExpressRoute pour Office 365, vous devez travailler avec un ou plusieurs [fournisseurs approuvés](https://azure.microsoft.com/documentation/articles/expressroute-locations/) afin de mettre en service les circuits de nombre et de taille souhaités avec un abonnement ExpressRoute Premium. Il n’existe aucune licence supplémentaire à acheter auprès d’Office 365.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Vous êtes prêt à vous inscrire à [ExpressRoute pour Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)

[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)

[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)

[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)

[Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365 (aperçu)](bgp-communities-in-expressroute.md)

[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[URL et plages d’adresses IP Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
