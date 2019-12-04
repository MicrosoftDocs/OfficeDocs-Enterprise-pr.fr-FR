---
title: Gestion d’ExpressRoute pour la connectivité d’Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute pour Office 365 offre un autre chemin de routage pour atteindre de nombreux services Office 365 sans avoir besoin de tout le trafic vers Internet. Bien que la connexion Internet à Office 365 soit toujours nécessaire, les itinéraires spécifiques publiés par Microsoft par le biais de BGP sur votre réseau rendent le circuit direct ExpressRoute préféré, sauf si d’autres configurations sont présentes dans votre réseau. Les trois domaines courants que vous pouvez configurer pour gérer ce routage incluent le filtrage des préfixes, la sécurité et la conformité.
ms.openlocfilehash: 589d8e60d2826170b7eddb84406d1d3d0effbb43
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814242"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Gestion d’ExpressRoute pour la connectivité d’Office 365

ExpressRoute pour Office 365 offre un autre chemin de routage pour atteindre de nombreux services Office 365 sans avoir besoin de tout le trafic vers Internet. Bien que la connexion Internet à Office 365 soit toujours nécessaire, les itinéraires spécifiques publiés par Microsoft par le biais de BGP sur votre réseau rendent le circuit direct ExpressRoute préféré, sauf si d’autres configurations sont présentes dans votre réseau. Les trois domaines courants que vous pouvez configurer pour gérer ce routage incluent le filtrage des préfixes, la sécurité et la conformité.
  
> [!NOTE]
> Microsoft a modifié la façon dont le domaine de routage d’homologation Microsoft est révisé pour Azure ExpressRoute. À partir du 31 juillet 2017, tous les clients Azure ExpressRoute peuvent activer l’homologation Microsoft directement à partir de la console d’administration Azure ou via PowerShell. Une fois que vous avez activé l’homologation Microsoft, tout client peut créer des filtres d’itinéraires pour recevoir des annonces d’itinéraires BGP pour les applications d’engagement client Dynamics 365 (anciennement CRM Online). Les clients qui ont besoin d’Azure ExpressRoute pour Office 365 doivent obtenir la vérification auprès de Microsoft avant de pouvoir créer des filtres d’itinéraires pour Office 365. Veuillez contacter votre équipe de compte Microsoft pour savoir comment demander une révision pour l’activation d’Office 365 ExpressRoute. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraires pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrage des préfixes

Microsoft recommande que les clients acceptent tous les itinéraires BGP publiés par Microsoft, les itinéraires fournis par le biais d’un processus de validation et de validation rigoureux supprimant les avantages à ajouter. ExpressRoute fournit en mode natif les contrôles recommandés, tels que la propriété de préfixe IP, l’intégrité et l’étendue, sans filtrage de route entrant côté client.
  
Si vous avez besoin d’une validation supplémentaire de la propriété de l’itinéraire sur l’homologation publique ExpressRoute, vous pouvez vérifier les itinéraires publiés par rapport à la liste de tous les préfixes IP IPv4 et IPv6 qui représentent les [plages d’adresses IP publiques de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Ces plages couvrent l’espace d’adressage Microsoft complet et changent peu fréquemment, ce qui fournit un ensemble fiable de plages à filtrer, ce qui offre également une protection supplémentaire aux clients concernés par les routes appartenant à des non-Microsoft qui fuient dans leurs contexte. Si une modification est apportée, elle est effectuée le 1er du mois et le numéro de version dans la section **Détails** de la page est modifié chaque fois que le fichier est mis à jour.
  
Il existe plusieurs raisons d’éviter l’utilisation des [URL et des plages d’adresses IP Office 365](https://aka.ms/o365endpoints) pour la génération de listes de filtres de préfixe. Notamment :
  
- Les préfixes IP d’Office 365 subissent beaucoup de modifications de façon fréquente.

- Les plages d’adresses IP et les URL Office 365 sont conçues pour la gestion des listes de pare-feu et des infrastructures proxy, et non par routage.

- Les URL et les plages d’adresses IP Office 365 ne couvrent pas les autres services Microsoft susceptibles d’être inclus dans le cadre de vos connexions ExpressRoute.

|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Accepter tous les itinéraires Microsoft  <br/> |**Faible :** Le client s’appuie sur des contrôles Microsoft pour s’assurer que tous les itinéraires sont correctement détenus.  <br/> |Aucun  <br/> |
|Filtrage des superréseaus appartenant à Microsoft  <br/> |**Moyenne :** Le client met en œuvre des listes de filtres de préfixes résumées pour autoriser uniquement les itinéraires appartenant à Microsoft.  <br/> |Les clients doivent s’assurer que les mises à jour infréquentes sont reflétées dans les filtres d’itinéraires.  <br/> |
|Filtrer les plages d’adresses IP Office 365  <br/> [!CAUTION] Non recommandé
|**Haute :** Le client filtre les itinéraires en fonction des préfixes IP d’Office 365.  <br/> |Les clients doivent implémenter un processus de gestion des modifications robuste pour les mises à jour mensuelles.  <br/> [!CAUTION] Cette solution nécessite des modifications importantes. Les modifications non mises en œuvre dans le temps entraîneront probablement une panne de service.   |

La connexion à Office 365 à l’aide d’Azure ExpressRoute repose sur des publicités BGP de sous-réseaux IP spécifiques qui représentent des réseaux sur lesquels les points de terminaison Office 365 sont déployés. En raison de la nature internationale d’Office 365 et du nombre de services qui composent Office 365, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. Si vous êtes préoccupé par le nombre de préfixes annoncés dans votre environnement, la fonctionnalité [communautaire BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) vous permet de filtrer les publicités sur un ensemble spécifique de services Office 365. Cette fonctionnalité est maintenant en aperçu.
  
Quelle que soit la façon dont vous gérez les annonces d’itinéraires BGP provenant de Microsoft, vous n’obtiendrez aucune exposition spéciale aux services Office 365 par rapport à la connexion à Office 365 par le biais d’un circuit Internet seul. Microsoft conserve les mêmes niveaux de sécurité, de conformité et de performances quel que soit le type de circuit utilisé par le client pour se connecter à Office 365.
  
### <a name="security"></a>Sécurité

Microsoft vous recommande de maintenir vos propres contrôles de périmètre de sécurité et de réseau pour les connexions allant vers et à partir d’ExpressRoute publics et Microsoft, qui incluent les connexions vers et à partir des services Office 365. Les contrôles de sécurité doivent être en place pour les demandes réseau qui voyagent en provenance de votre réseau vers le réseau de Microsoft, ainsi que les ports entrants du réseau Microsoft vers votre réseau.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Trafic sortant du client vers Microsoft
  
Lorsque les ordinateurs se connectent à Office 365, ils se connectent au même ensemble de points de terminaison, que la connexion soit établie via Internet ou un circuit ExpressRoute. Quel que soit le circuit utilisé, Microsoft vous recommande de traiter les services Office 365 comme étant plus approuvés que les destinations Internet génériques. Vos contrôles de sécurité sortants doivent se concentrer sur les ports et les protocoles pour réduire l’exposition et réduire la maintenance en cours. Les informations de port requises sont disponibles dans l’article de référence des [points de terminaison Office 365](https://aka.ms/o365endpoints) .
  
Pour les contrôles ajoutés, vous pouvez utiliser le filtrage au niveau du nom de domaine complet au sein de votre infrastructure de proxy pour restreindre ou vérifier une partie ou la totalité des demandes réseau destinées à Internet ou Office 365. La gestion de la liste des noms de domaine complets à mesure que les fonctionnalités sont publiées et que les offres Office 365 évoluent nécessitent une gestion des modifications plus robuste et le suivi des modifications apportées aux [points de terminaison office 365](https://aka.ms/o365endpoints)publiés.
  
> [!CAUTION]
> Microsoft vous recommande de ne pas dépendre uniquement des préfixes IP pour gérer la sécurité sortante vers Office 365.

|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Aucune restriction  <br/> |**Faible :** Le client autorise l’accès sortant non restreint à Microsoft.  <br/> |Aucun  <br/> |
|Restrictions de port  <br/> |**Faible :** Le client limite l’accès sortant à Microsoft par les ports attendus.  <br/> |Rares.  <br/> |
|Restrictions de nom de domaine complet  <br/> |**Haute :** Le client limite l’accès sortant à Office 365 en fonction des noms de domaine complets publiés.  <br/> |Modifications mensuelles.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Trafic entrant de Microsoft vers le client
  
Il existe plusieurs scénarios facultatifs qui requièrent que Microsoft initie des connexions à votre réseau.
  
- ADFS lors de la validation du mot de passe pour la connexion.

- [Déploiements hybrides Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Courrier à partir d’un client Exchange Online vers un hôte local.

- SharePoint Online mail envoyer depuis SharePoint Online vers un hôte local.

- [Recherche hybride fédérée SharePoint](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS SharePoint hybride](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype entreprise hybride](https://technet.microsoft.com/library/jj205403.aspx) et/ou [Fédération Skype entreprise](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype entreprise, Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft recommande d’accepter ces connexions sur votre circuit Internet au lieu de votre circuit ExpressRoute pour réduire la complexité. Si vos besoins en matière de conformité ou de performances imposent que ces connexions entrantes doivent être acceptées via un circuit ExpressRoute, l’utilisation d’un pare-feu ou d’un proxy inverse pour l’étendue des connexions acceptées est recommandée. Vous pouvez utiliser les [points de terminaison Office 365](https://aka.ms/o365endpoints) pour déterminer les noms de domaine complets et les préfixes IP corrects.
  
### <a name="compliance"></a>Conformité

Nous ne faisons pas confiance au chemin de routage que vous utilisez pour nos contrôles de conformité. Que vous vous connectiez aux services Office 365 via un ExpressRoute ou un circuit Internet, nos contrôles de conformité ne changent pas. Vous devez passer en revue les différents niveaux de certification de sécurité et de conformité pour Office 365 afin de déterminer le meilleur choix pour répondre aux besoins de votre organisation.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Voir aussi

[Réseaux de distribution de contenu](content-delivery-networks.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)
