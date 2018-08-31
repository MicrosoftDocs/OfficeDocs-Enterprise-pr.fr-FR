---
title: Gestion d’ExpressRoute pour la connectivité d’Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute pour Office 365 offre un autre chemin de routage pour accéder à de nombreux services Office 365 sans avoir besoin de tout le trafic vers la sortie vers internet. Bien que la connexion internet à Office 365 est toujours nécessaire, les itinéraires spécifiques que Microsoft publie via BGP à votre réseau rendre le circuit ExpressRoute direct par défaut, sauf si les autres configurations de votre réseau. Les trois zones courantes que vous souhaiterez peut-être configurer pour gérer ce routage inclure le préfixe de filtrage, de sécurité et conformité.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540384"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Gestion d’ExpressRoute pour la connectivité d’Office 365

ExpressRoute pour Office 365 offre un autre chemin de routage pour accéder à de nombreux services Office 365 sans avoir besoin de tout le trafic vers la sortie vers internet. Bien que la connexion internet à Office 365 est toujours nécessaire, les itinéraires spécifiques que Microsoft publie via BGP à votre réseau rendre le circuit ExpressRoute direct par défaut, sauf si les autres configurations de votre réseau. Les trois zones courantes que vous souhaiterez peut-être configurer pour gérer ce routage inclure le préfixe de filtrage, de sécurité et conformité.
  
> [!NOTE]
> Microsoft a modifié la façon dont le domaine de routage Peering Microsoft est passé en revue pour Azure ExpressRoute. Démarrage du 31 juillet 2017, tous les clients ExpressRoute Azure peuvent activer Microsoft Peering directement à partir de la console d’administration Azure ou via PowerShell. Après avoir activé Microsoft Peering, n’importe quel client peut créer des filtres d’itinéraires pour recevoir des annonces d’itinéraires BGP pour les applications de l’Engagement client Dynamics 365 (anciennement appelé CRM Online). Clients nécessitant ExpressRoute Azure pour Office 365 doivent obtenir révision de Microsoft avant de pouvoir créer des filtres d’itinéraires pour Office 365. Veuillez contacter votre équipe Account Microsoft pour découvrir comment demander un examen de l’activation d’Office 365 ExpressRoute. Abonnements non autorisés tente de créer des filtres d’itinéraires pour Office 365 reçoit un [message d’erreur](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Préfixe de filtrage

Microsoft recommande que les clients acceptent tous les itinéraires BGP publiés à partir de Microsoft, les itinéraires fournies sont soumis à un processus de révision et de validation rigoureux suppression des avantages offerts par contrôle ajouté. En mode natif ExpressRoute offre les contrôles recommandés, telles que la propriété préfixe IP, l’intégrité et à l’échelle - aucun itinéraire entrant filtrage sur le côté client.
  
Si vous avez besoin d’une validation supplémentaire de possession de l’itinéraire entre peering public ExpressRoute, vous pouvez vérifier les itinéraires publiés par rapport à la liste de tous les préfixes IPv4 et IPv6 qui représentent les [plages d’adresses IP publiques de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Ces plages traitent de l’espace d’adressage Microsoft complète et modifier rarement, fournir un ensemble de plages de filtre de fiable qui fournit également une protection supplémentaire pour les clients préoccupées non-Microsoft appartenant itinéraires fuite dans leurs environnement. Dans les événements est modifié, il sera effectué sur le 1er du mois et le numéro de version dans la section **Détails** de la page change chaque fois que le fichier est mis à jour.
  
Il existe plusieurs raisons pour éviter l’utilisation de [plages d’adresses IP et les URL d’Office 365](https://aka.ms/o365endpoints) pour générer des listes de filtre de préfixe. Notamment les suivantes :
  
- Les préfixes d’Office 365 IP sont soumis à nombreuses modifications régulièrement.

- L’adresse IP et le Office 365 URL plages sont conçus pour la gestion des pare-feu permettent des listes et infrastructure de Proxy, ne pas de routage.

- Les plages d’adresses IP et Office 365 URL ne couvrent pas les autres services Microsoft qui peuvent être dans la portée de vos connexions ExpressRoute.

| |
|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Accepter tous les itinéraires de Microsoft  <br/> |**Faible :** Client s’appuie sur les contrôles de Microsoft pour vérifier que tous les itinéraires sont correctement la propriété.  <br/> |Aucun  <br/> |
|Microsoft Filter appartient supernets  <br/> |**Support :** Client implémente des listes de filtre de préfixe résumées pour autoriser uniquement les Microsoft propriété des itinéraires.  <br/> |Les clients doivent veiller que les mises à jour peu fréquentes sont répercutées dans les filtres de routage.  <br/> |
|Filtrer les plages d’adresses IP de Office 365  <br/> [!CAUTION] Non recommandé
|**Haute :** Client filtre itinéraires en fonction de préfixes d’Office 365 IP définies.  <br/> |Les clients doivent implémenter un processus de gestion des changements robuste pour les mises à jour tous les mois.  <br/> [!CAUTION]Cette solution nécessite des modifications significatives en cours. Modifications non implémentées dans l’heure aura une interruption de service.   |

Connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur les publicités BGP de sous-réseaux IP spécifiques qui représentent les réseaux où les points de terminaison Office 365 sont déployés. En raison de la nature globale d’Office 365 et le nombre de services d’Office 365, les clients ont souvent besoin de gérer les publications qu'ils acceptent sur leur réseau. Si vous êtes concerné avec le nombre de préfixes publiés dans votre environnement, la fonctionnalité de [la Communauté BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) permet de filtrer les publications à un ensemble spécifique de services Office 365. Cette fonctionnalité est maintenant en mode Aperçu.
  
Quelle que soit la façon dont vous gérez les annonces de routage BGP provenant de Microsoft, vous ne la visibilité des spéciaux aux services Office 365 par rapport à la connexion à Office 365 sur un circuit d’internet uniquement. Microsoft conserve la même sécurité, de conformité et performances, quel que soit le type de circuit qu'un client utilise pour se connecter à Office 365.
  
### <a name="security"></a>Sécurité

Microsoft recommande que vous gérez vos propres contrôles de périmètre de réseau et de sécurité pour les connexions vers et depuis ExpressRoute public et Microsoft peering, sur le point qui inclut les connexions vers et depuis les services Office 365. Contrôles de sécurité à mettre en place pour les demandes de réseau qui se déplacent sortant de votre réseau au réseau de Microsoft ainsi que de trafic entrant à partir du réseau Microsoft sur votre réseau.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Sortie d’un client à Microsoft
  
Lorsque les ordinateurs se connectent à Office 365, ils se connectent au même ensemble de points de terminaison indépendamment indique si la connexion est établie via internet ou par circuit ExpressRoute. Quel que soit le circuit utilisé, Microsoft vous recommande de traiter les services Office 365 comme plus sécurisée que générique destinations internet. Vos contrôles de sécurité sortante doivent se concentrer sur les ports et protocoles pour réduire l’exposition et réduire la maintenance régulière. Les informations de port requis sont disponibles dans l’article de référence des [points de terminaison Office 365](https://aka.ms/o365endpoints) .
  
Pour les contrôles ajoutés, vous pouvez utiliser le filtrage dans votre infrastructure de serveur proxy au niveau de nom de domaine complet restreindre ou inspecter certaines ou toutes les requêtes réseau destinés à internet ou à Office 365. Maintenance de la liste des noms de domaine complets que les fonctionnalités sont disponibles et les offres Office 365 évoluent nécessite la gestion des modifications plus robuste et suivi des modifications des [points de terminaison Office 365](https://aka.ms/o365endpoints)publié.
  
> [!CAUTION]
> Microsoft recommande que vous ne vous fiez uniquement les préfixes IP pour gérer la sécurité du courrier sortant vers Office 365.

|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Aucune restriction  <br/> |**Faible :** Client permet un accès sortant illimité à Microsoft.  <br/> |Aucun  <br/> |
|Restrictions de port  <br/> |**Faible :** Client restreint l’accès sortant à Microsoft par les ports attendues.  <br/> |Rare.  <br/> |
|Restrictions de nom de domaine complet  <br/> |**Haute :** Client limite l’accès sortant vers Office 365 basée sur les noms de domaines complets publiés.  <br/> |Modifications de tous les mois.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Trafic entrant à partir de Microsoft au client
  
Il existe plusieurs scénarios facultatifs qui nécessitent Microsoft pour établir des connexions à votre réseau.
  
- ADFS lors de la validation de mot de passe pour la connexion.

- [Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- À partir d’un client Exchange Online le courrier vers un hôte local.

- SharePoint Online messagerie envoyer à partir de SharePoint Online à un hôte local.

- [SharePoint fédéré de recherche hybride](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint hybride BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype pour un environnement hybride Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) et/ou [Skype pour la fédération de l’entreprise](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype pour Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft recommande que vous acceptez ces connexions sur votre circuit internet au lieu de votre circuit ExpressRoute pour réduire la complexité. Si votre conformité ou les performances doit dicter que ces connexions entrantes doivent être acceptées sur un circuit ExpressRoute, à l’aide d’un pare-feu ou un proxy inverse pour les connexions acceptées d’étendue est recommandé. Vous pouvez utiliser les [points de terminaison Office 365](https://aka.ms/o365endpoints) pour déterminer les noms de domaine complets de droite et les préfixes d’IP.
  
### <a name="compliance"></a>Conformité

Nous ne s’appuient sur le chemin de routage que vous utilisez pour tous les contrôles de conformité. Quelle que soit la si vous connecter aux services Office 365 un circuit ExpressRoute ou internet, ne modifie pas les contrôles de conformité. Vous devez examiner la conformité et les niveaux de certification de sécurité pour Office 365 déterminer la meilleure solution pour répondre aux besoins de votre organisation.
  
Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Voir aussi

[Réseaux de distribution de contenu](content-delivery-networks.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)
