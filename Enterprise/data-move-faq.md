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
f1.keywords:
- NOCSH
description: Voici des réponses à des questions d’ordre général sur le transfert de données principales vers une nouvelle région de centre de données.
ms.openlocfilehash: 291f5068cc66ae761571992b462995fb6437b872
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735842"
---
# <a name="data-move-general-faq"></a>FAQ général relatif au déplacement de données

Voici des réponses à des questions d’ordre général sur le transfert de données principales vers une nouvelle région de centre de données.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>Quels clients peuvent demander un déplacement ?
  
Les clients commerciaux Microsoft 365 existants qui ont sélectionné un pays éligible pour la région de centre de donnée peuvent demander un déplacement.  Le programme existe uniquement pour les clients dont le code pays éligible est affecté au client Microsoft 365 pour migrer les données client principales au repos pour les charges de travail éligibles vers la région de centre de données Microsoft 365 correspondante.  Consultez la page [procédure de demande d’un déplacement de données](request-your-data-move.md) pour confirmer l’éligibilité du pays.   

## <a name="how-do-we-define-core-customer-data"></a>Comment définir des données client principales ?
 
Les données client principales sont un terme qui fait référence à un sous-ensemble de données client définies dans les [conditions de Microsoft Online Services](https://aka.ms/ost): 
- Contenu de boîte aux lettres Exchange Online (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes)
- Contenu de site SharePoint Online et fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive entreprise 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>À quel moment mon migration est-elle terminée afin que les données client essentielles de mon client soient stockées au repos dans ma nouvelle région ?

En raison des dépendances partagées entre Exchange Online et SharePoint Online/OneDrive entreprise, toute migration ne peut pas être considérée comme terminée tant que les deux services n’ont pas été migrés.  Exchange Online et SharePoint Online/OneDrive entreprise sont souvent migrés à des moments distincts et indépendamment les uns des autres.  Les administrateurs de client reçoivent une confirmation dans le centre de messages lorsque chaque migration de service est terminée et peut afficher la carte d’emplacement des données dans le centre d’administration à tout moment pour confirmer les données client principales à l’emplacement REST pour chaque service.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Comment vous assurez-vous que mes données client sont sécurisées lors du déplacement et qu’il n’y aura pas de temps d’arrêt ?
  
Les déplacements de données sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Les fonctionnalités qui peuvent être affectées sont répertoriées [pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité, de sorte que les clients ne doivent pas se préparer ou à surveiller pendant le déplacement. 
  
Tous les services Microsoft 365 exécutent les mêmes versions dans les centres de connaissances, ce qui vous garantit une fonctionnalité cohérente. Votre service est entièrement pris en charge tout au long du processus.

## <a name="what-is-in-scope-for-teams-migration"></a>Quelle est la portée de la migration de teams ?

En plus d’Exchange Online, de SharePoint Online et de OneDrive entreprise ; Microsoft migre les données de teams vers le centre de données local.  
- Les messages de conversation Teams, y compris les messages privés et les messages de canal. 
- Images de teams utilisées dans les conversations. 

Les fichiers teams sont stockés dans SharePoint Online et les fichiers de conversation teams sont stockés dans OneDrive entreprise.  La messagerie vocale, le calendrier, l’historique des conversations et les contacts sont stockés dans Exchange Online.  Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive entreprise sont déjà utilisés par le client dans la région de centre de donneurs locaux et font également partie du programme de migration Office 365 pour les pays clients éligibles.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Quel est l’impact de l’utilisation de différents services dans différents régions centres ?

Certains des services Microsoft 365 peuvent se trouver dans différents régions centres pour certains clients existants et pour les clients qui se trouvent au milieu du processus de déplacement. Nos services s’exécutent indépendamment les uns des autres et n’ont pas d’impact sur l’expérience utilisateur, le cas échéant.Toutefois, pour les besoins de la résidence des données, une migration de client ne peut pas être considérée comme terminée tant que Exchange Online et SharePoint Online/OneDrive entreprise n’ont pas été migrés vers la même région de centre de données.
  
## <a name="will-new-microsoft-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>Les nouveaux clients Microsoft 365 seront-ils automatiquement mis en service dans le nouveau centre de régions centres ?
  
Oui. Une fois qu’une nouvelle région de centre de données est disponible, les nouveaux clients Microsoft 365 qui sélectionnent un pays éligible pour la nouvelle région comme pays lors de l’inscription auront leurs données client principales stockées au repos dans la nouvelle région de centre de données.
  
 ## <a name="where-is-my-core-customer-data-located"></a>Où se trouvent mes données client principales ?

Les administrateurs clients peuvent afficher la carte d’emplacement des données dans le centre d’administration à tout moment pour confirmer les données principales du client au moment de l’emplacement REST pour chaque service, en particulier pour leur client.Nous publions également l’emplacement des régions centres de centre de données, des centres de données et l’emplacement des données client Office 365 sur [office 365 interactive Datacenter Maps](https://office.com/datamaps) comme référence pour les données client principales par défaut actuelles aux emplacements REST pour les nouveaux clients.  Vous pouvez vérifier l’emplacement de vos données client au repos via la section emplacement des données sous votre profil d’organisation dans le centre d’administration 365 de Microsoft.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>Quand pourrai-je demander un déplacement ?
  
Consultez la page relative [à la demande d’un déplacement de données](request-your-data-move.md) pour les périodes prises en charge pour votre région de centre de données.
  
## <a name="how-can-i-request-to-be-moved"></a>Comment effectuer ma demande de déplacement ?
  
Les clients éligibles verront une page dans leur [Centre d’administration 365 de Microsoft](https://admin.microsoft.com/). Reportez-vous à la section [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir des informations sur la demande de déplacement. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>Puis-je modifier ma sélection après avoir demandé un déplacement ?
  
Nous ne pouvons pas vous enlever du processus une fois que vous avez envoyé votre demande.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Que se passe-t-il si je ne fais pas la demande de déplacement avant la date d’échéance ?
  
Nous pouvons être en mesure d’accepter des demandes sur la base d’une exception pour accorder à votre client une échéance validée pour terminer le déplacement. Veuillez   contacter le [Support Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour effectuer la demande.

## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Que se passe-t-il si je veux déplacer mes données afin de bénéficier de meilleures performances réseau ?
  
La proximité physique d’un centre de contenu Microsoft 365 ne garantit pas une meilleure performance réseau. De nombreux facteurs et composants ont un impact sur les performances réseau entre l’utilisateur final et le service Microsoft 365. Pour plus d’informations à ce sujet et sur l’optimisation des performances, consultez la rubrique [Network Planning and Performance Tuning for Office 365](network-planning-and-performance.md).
  
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
  
## <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Je suis un client Microsoft 365 dans l’un des nouveaux centres de régions centres, mais lorsque je me suis inscrit, j’ai sélectionné un autre pays. Comment puis-je le déplacer vers la nouvelle région de centre de informations ?

Il n’est pas possible de modifier le pays d’abonnement associé à votre client. Au lieu de cela, vous devez créer un client Office 365 avec un nouvel abonnement et déplacer manuellement les utilisateurs et les données vers le nouveau client.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Que se passe-t-il si nous utilisons la migration des données de messagerie vers Microsoft 365 pendant le déplacement d’Exchange Online ?

Il s’agit d’un scénario très courant qui est entièrement pris en charge.  La migration Cloud entre Datacenter régions centres n’interfère pas avec les migrations de boîtes aux lettres premisis vers Cloud.
  
 ## <a name="can-i-pilot-some-users"></a>Puis-je piloter certains utilisateurs ?
  
Vous pouvez créer un client d'évaluation distinct pour tester la connectivité, mais il ne peut pas être associé à votre client existant.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Je ne souhaite pas attendre que Microsoft déplace mes données. Puis-je simplement créer un client et le déplacer moi-même ?
  
Oui, toutefois le processus ne sera pas aussi transparent que s’il était effectué par Microsoft.
  
Si vous créez un nouveau client une fois que la nouvelle région de centre de contenu est disponible, le nouveau client est hébergé dans la nouvelle région. Ce nouveau client est totalement distinct de votre ancien client et vous serez chargé de transférer toutes les boîtes aux lettres utilisateur, le contenu de site, les noms de domaine et toutes les autres données. Notez que vous ne pouvez pas déplacer le nom de client d’un client vers un autre. Nous vous recommandons d’attendre le programme de déplacement fourni par Microsoft pour pouvoir déplacer tous les paramètres, les données et les abonnements de vos utilisateurs.
  
## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Mes données client ont déjà été déplacées vers une nouvelle région de centre de données. Puis-je les déplacer vers l’ancienne région ?
 
Non, ce n’est pas possible. Les clients qui ont été déplacés vers de nouveaux centres de recherche géo ne peuvent pas être déplacés. En tant que client dans une région géographique, vous bénéficierez de la même qualité de service, de performances et de contrôles de sécurité que vous l’avez fait précédemment.  [Office 365 multi géo](https://aka.ms/multi-geo) est disponible pour certains clients en tant que module complémentaire et permet à un seul client de créer plusieurs régions centres satellites et de déplacer des données utilisateur vers ces régions centres avec des engagements de délégation de données.
  
## <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Les clients Microsoft 365 hébergés dans les nouveaux centres de connaissances seront-ils disponibles pour les utilisateurs en dehors du pays ?
  
Oui. Microsoft gère un vaste réseau mondial avec des connexions Internet publiques dans plus de 130 emplacements dans 35 pays dans le monde entier avec des accords d’homologation avec plus de 2 700 fournisseurs de services Internet (ISP). Les utilisateurs pourront accéder aux centres de données par Internet, où qu’ils soient.

## <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mon client a configuré le [complément multi-géo](https://aka.ms/multi-geo). Puis-je toujours m’inscrire à mon client dans le programme Microsoft 365 Move pour modifier mon emplacement géographique par défaut et déplacer les utilisateurs qui ne se trouvent pas dans une région satellite vers la nouvelle zone géographique par défaut ?

Oui, votre locataire peut être inscrit. Nous allons déplacer toutes les boîtes aux lettres EXO de votre région actuelle par défaut vers votre nouvelle région de centre de centres local.  Nous ne allons pas déplacer les boîtes aux lettres EXO configurées dans des régions multigéographiques satellites pour continuer à respecter la résidence des données des régions satellites comme prévu.  

SharePoint Online et OneDrive entreprise ne peuvent pas migrer vers la nouvelle région de centre de travail dans le cadre du programme de déplacement, mais vous pouvez configurer les partages de OneDrive entreprise pour passer à une région de votre choix via le programme multigéographique.
  
## <a name="related-topics"></a>Voir aussi

[Transfert de données principales vers le nouveau centre de données Microsoft 365 régions centres](moving-data-to-new-datacenter-geos.md)

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[Office 365 multi-géo](https://aka.ms/multi-geo)

[Plan interactive du centre de connaissances Microsoft 365](https://office.com/datamaps)

[Prise en charge de Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
