---
title: FAQ général relatif au déplacement de données
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Voici des réponses à des questions d’ordre général sur le transfert de données principales vers une nouvelle région de centre de données.
ms.openlocfilehash: fd133dfb28ae99115198977e2e6d637a872078d8
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756583"
---
# <a name="data-move-general-faq"></a>FAQ général relatif au déplacement de données

Voici des réponses à des questions d’ordre général sur le transfert de données principales vers une nouvelle région de centre de données.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>Quels clients peuvent demander un déplacement ?
  
Les clients commerciaux Office 365 existants qui ont sélectionné un pays éligible pour la région de centre de donnée peuvent demander un déplacement.  Le programme existe uniquement pour les clients disposant d’un code pays éligible attribué au client Office 365 pour migrer les données client principales vers REST pour les charges de travail éligibles vers la région de centre de données Office 365 correspondante.  Consultez la page [procédure de demande d’un déplacement de données](request-your-data-move.md) pour confirmer l’éligibilité du pays.   

## <a name="how-do-we-define-core-customer-data"></a>Comment définir des données client principales ?
 
Les données client principales sont un terme qui fait référence à un sous-ensemble de données client définies dans les [conditions de Microsoft Online Services](https://aka.ms/ost): 
- Contenu de boîte aux lettres Exchange Online (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes)
- Contenu de site SharePoint Online et fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive entreprise 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>À quel moment mon migration est-elle terminée afin que les données client essentielles de mon client soient stockées au repos dans ma nouvelle région ?

En raison des dépendances partagées entre Exchange Online et SharePoint Online/OneDrive entreprise, toute migration ne peut pas être considérée comme terminée tant que les deux services n’ont pas été migrés.  Exchange Online et SharePoint Online/OneDrive entreprise sont souvent migrés à des moments distincts et indépendamment les uns des autres.  Les administrateurs de client reçoivent une confirmation dans le centre de messages lorsque chaque migration de service est terminée et peut afficher la carte d’emplacement des données dans le centre d’administration à tout moment pour confirmer les données client principales à l’emplacement REST pour chaque service.

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>Mon client sera-t-il déplacé automatiquement vers la nouvelle région de centre de de centres ?
 
Il existe deux actions que vous pouvez prendre en tant qu’administrateur client.

- Abonnez-vous.Inscrivez-vous au programme Office 365 Move et recevez une date d’échéance pour vos services afin de migrer les données client principales au repos vers la nouvelle région de centre de données.Consultez la page [procédure de demande d’un déplacement de données](request-your-data-move.md) pour obtenir des instructions sur la manière d’opter pour le programme.
- Ne rien faire.Aucune action n’est effectuée, ce qui permet à Microsoft de déplacer vos données client principales au repos sur votre nouveau Geo dans le cadre de la gestion et de l’optimisation des services.Vos données ne peuvent être déplacées que vers votre nouvelle région de centre de données, pas vers une autre région.Nous avertissons via le centre de messages quand un tel déplacement de gestion de service est terminé.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Comment vous assurez-vous que mes données client sont sécurisées lors du déplacement et qu’il n’y aura pas de temps d’arrêt ?
  
Les déplacements de données sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Les fonctionnalités qui peuvent être affectées sont répertoriées [pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité, de sorte que les clients ne doivent pas se préparer ou à surveiller pendant le déplacement. 
  
Tous les services Office 365 sont exécutés avec les mêmes versions dans les centres de données. Vous pouvez ainsi être certain de la cohérence des fonctionnalités. Votre service est entièrement pris en charge tout au long du processus.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Quel est l’impact de l’utilisation de différents services dans différents régions centres ?

Certains des services Office 365 peuvent se trouver dans différents régions centres pour certains clients existants et pour les clients qui se trouvent au milieu du processus de déplacement.  Nos services s’exécutent indépendamment les uns des autres et n’ont pas d’impact sur l’expérience utilisateur si c’est le cas.Toutefois, pour les besoins de la résidence des données, une migration de client ne peut pas être considérée comme terminée tant que Exchange Online et SharePoint Online/OneDrive entreprise n’ont pas été migrés vers la même région de centre de données.
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>Les nouveaux clients Office 365 seront-ils automatiquement mis en service dans le nouveau centre de régions centres ?
  
Oui. Une fois qu’une nouvelle région de centre de données est disponible, les nouveaux clients Office 365 pour les entreprises qui sélectionnent un pays éligible pour la nouvelle région comme pays lors de l’inscription auront leurs données client principales stockées au repos dans la nouvelle région de centre de données.
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>Où se trouvent mes données client principales ?

Les administrateurs clients peuvent afficher la carte d’emplacement des données dans le centre d’administration à tout moment pour confirmer les données principales du client au moment de l’emplacement REST pour chaque service, en particulier pour leur client.Nous publions également l’emplacement des régions centres de centre de données, des centres de données et l’emplacement des données client Office 365 sur [ office 365 interactive Datacenter Maps](https://office.com/datamaps) comme référence pour les données client principales par défaut actuelles aux emplacements REST pour les nouveaux clients.  Vous pouvez vérifier l’emplacement de vos données client au repos via la section emplacement des données sous votre profil d’organisation dans le centre d’administration 365 de Microsoft.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>Quand pourrai-je demander un déplacement ?
  
Consultez la page relative [à la demande d’un déplacement de données](request-your-data-move.md) pour les périodes prises en charge pour votre région de centre de données.
  
## <a name="how-can-i-request-to-be-moved"></a>Comment effectuer ma demande de déplacement ?
  
Les clients éligibles verront une page correspondante dans leur [portail d'administration Office 365](https://portal.office.com/). Reportez-vous à la section [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir des informations sur la demande de déplacement. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>Puis-je modifier ma sélection après avoir demandé un déplacement ?
  
Nous ne pouvons pas vous enlever du processus une fois que vous avez envoyé votre demande.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Que se passe-t-il si je ne fais pas la demande de déplacement avant la date d’échéance ?
  
 Nous pouvons être en mesure d’accepter une demande sur la base d’une exception pour accorder à votre client une échéance engagée afin de finaliser le déplacement.Veuillez  contacter le [Support Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour effectuer la demande.  Rappelez-vous que certaines charges de travail peuvent être transférées vers votre nouvelle zone géographique, même si aucune demande d’abonnement ne se traduit par le fait que Microsoft ne peut pas déplacer vos données client principales au repos dans le cadre de la gestion et de l’optimisation des services.Vos données ne peuvent être déplacées que vers votre nouvelle région de centre de données, pas vers une autre région.  Nous avertissons via le centre de messages quand un tel déplacement de gestion de service est terminé.
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Que se passe-t-il si je veux déplacer mes données afin de bénéficier de meilleures performances réseau ?
  
Le fait d’être proche d’un centre de données Office 365 ne garantit pas que vous bénéficiiez de meilleures performances réseau. De nombreux facteurs et composants ont une incidence sur les performances réseau entre l’utilisateur final et le service Office 365. Pour plus d’informations à ce sujet et sur l’optimisation des performances, consultez la rubrique [Network Planning and Performance Tuning for Office 365](network-planning-and-performance.md).
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Les données de tous les services sont-elles déplacées le même jour ?
 
Chaque service se déplace de façon indépendante et risque de déplacer ses données à différents moments.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Puis-je choisir la date du déplacement de mes données ?
 
 Les clients ne peuvent pas sélectionner une date spécifique, ils ne peuvent pas retarder leur déplacement et nous ne pouvons pas partager une date ou une période spécifique pour les déplacements.
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>Pouvez-vous m’indiquer quand mes données seront déplacées ?
  
Les déplacements de données sont des opérations principales qui ont une incidence minime sur les utilisateurs finals. La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Que se passe-t-il si les utilisateurs accèdent à des services lors du déplacement des données ?

Reportez-vous à la section [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md) pour consulter la liste complète des fonctionnalités qui peuvent être limitées à certains moments du déplacement des données pour chaque service. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>Comment savoir que le déplacement est terminé ?
  
Regardez le centre de messages Office 365 pour confirmer que le déplacement des données de chaque service est terminé. Lorsque les données de chaque service sont déplacées, nous allons publier un avertissement de fin d’opération pour obtenir trois notifications d’achèvement : une pour Exchange Online, SharePoint Online et Skype entreprise online.  Vous pouvez également vérifier l’emplacement de vos données client au repos via la section emplacement des données sous votre profil d’organisation dans le centre d’administration 365 de Microsoft.  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Je suis un client Office 365 dans l’un des nouveaux centres de régions centres, mais lorsque je me suis inscrit, j’ai sélectionné un autre pays. Comment puis-je le déplacer vers la nouvelle région de centre de informations ?

Il n’est pas possible de modifier le pays d’abonnement associé à votre client. Au lieu de cela, vous devez créer un client Office 365 avec un nouvel abonnement et déplacer manuellement les utilisateurs et les données vers le nouveau client.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>Que se passe-t-il si nous sommes en train de migrer des données de messagerie électronique vers Office 365 lors du déplacement d’Exchange Online ?

Il s’agit d’un scénario très courant qui est entièrement pris en charge.  La migration Cloud entre Datacenter régions centres n’interfère pas avec les migrations de boîtes aux lettres premisis vers Cloud.
  
 ## <a name="can-i-pilot-some-users"></a>Puis-je piloter certains utilisateurs ?
  
Vous pouvez créer un client d'évaluation distinct pour tester la connectivité, mais il ne peut pas être associé à votre client existant.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Je ne souhaite pas attendre que Microsoft déplace mes données. Puis-je simplement créer un client et le déplacer moi-même ?
  
Oui, toutefois le processus ne sera pas aussi transparent que s’il était effectué par Microsoft.
  
Si vous créez un nouveau client une fois que la nouvelle région de centre de contenu est disponible, le nouveau client est hébergé dans la nouvelle région. Ce nouveau client est totalement distinct de votre ancien client et vous serez chargé de transférer toutes les boîtes aux lettres utilisateur, le contenu de site, les noms de domaine et toutes les autres données. Notez que vous ne pouvez pas déplacer le nom de client d’un client vers un autre. Nous vous recommandons d’attendre le programme de déplacement fourni par Microsoft pour pouvoir déplacer tous les paramètres, les données et les abonnements de vos utilisateurs.
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>Je ne suis pas prêt à être déplacé, puis-je choisir une date de déplacement spécifique ?
  
Non, il n’est pas possible de modifier le déplacement des données client principales de chaque service.
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Mes données client ont déjà été déplacées vers une nouvelle région de centre de données. Puis-je les déplacer vers l’ancienne région ?
 
Non, cela n’est pas possible. Les clients qui ont été déplacés vers de nouveaux centres de recherche géo ne peuvent pas être déplacés. En tant que client dans une région géographique, vous bénéficierez de la même qualité de service, de performances et de contrôles de sécurité que vous l’avez fait précédemment.  [Office 365 multi géo](https://aka.ms/multi-geo) est disponible pour certains clients en tant que module complémentaire et permet à un seul client de créer plusieurs régions centres satellites et de déplacer des données utilisateur vers ces régions centres avec des engagements de délégation de données.
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>Le nouveau centre de régions centres utilise-t-il les mêmes versions des services Office 365 que le centre de régions centres actuel ?

Oui.
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Les clients Office 365 hébergés dans les nouveaux centres de données seront-ils disponibles pour les utilisateurs situés dans un autre pays ?
  
R. Oui. Microsoft gère un vaste réseau mondial avec des connexions Internet publiques dans plus de 130 emplacements dans 35 pays dans le monde entier avec des accords d’homologation avec plus de 2 700 fournisseurs de services Internet (ISP). Les utilisateurs pourront accéder aux centres de données par Internet, où qu’ils soient.

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mon client est configuré pour [Office 365 multi géo](https://aka.ms/multi-geo).  Puis-je toujours m’inscrire à mon client dans le programme Office 365 Move pour modifier mon emplacement géographique par défaut et déplacer les utilisateurs qui ne se trouvent pas dans une région satellite vers la nouvelle zone géographique par défaut ?

Oui, votre locataire peut être inscrit.  Nous allons déplacer toutes les boîtes aux lettres EXO de votre région actuelle par défaut vers votre nouvelle région de centre de centres local.  Nous ne allons pas déplacer les boîtes aux lettres EXO configurées dans des régions multigéographiques satellites pour continuer à respecter la résidence des données des régions satellites comme prévu.  SharePoint Online et OneDrive entreprise ne peuvent pas migrer vers la nouvelle région de centre de travail dans le cadre du programme de déplacement, mais vous pouvez configurer les partages de OneDrive entreprise pour passer à une région de votre choix via le programme multigéographique.
  
## <a name="related-topics"></a>Sujets associés

[Transfert de données principales vers le nouveau centre de données Office 365 régions centres](moving-data-to-new-datacenter-geos.md)

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[Office 365 multi-géo](https://aka.ms/multi-geo)

[Carte Office 365 interactive Datacenter](https://office.com/datamaps)

[Prise en charge d’Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
