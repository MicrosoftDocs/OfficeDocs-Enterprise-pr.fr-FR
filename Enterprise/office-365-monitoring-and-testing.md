---
title: Office 365 surveillance et test des limites client
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Résumé : explique comment Microsoft surveille et teste les frontières client pour Office 365.'
ms.openlocfilehash: 4a986795537f8871d3f3e60c9ff4112e6fe3f668
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035514"
---
# <a name="monitoring-and-testing-tenant-boundaries"></a>Surveillance et test des limites du client

Microsoft surveille et teste explicitement les faiblesses et les vulnérabilités des clients, y compris la surveillance des intrusions, les tentatives de violation d’autorisation et la privation de ressources. Nous utilisons également plusieurs systèmes internes pour surveiller en permanence une utilisation inappropriée des ressources, qui, si elle est détectée, déclenche la limitation intégrée.

Office 365 dispose de systèmes de surveillance internes qui surveillent continuellement les pannes et génèrent une récupération automatisée en cas d’échec détecté. Les systèmes Office 365 analysent les écarts de comportement de service et déclenchent des processus d’auto-réparation intégrés au système. Office 365 utilise également la surveillance extérieure dans laquelle la surveillance est effectuée à partir de plusieurs emplacements à la fois de services tiers approuvés (pour une vérification de SLA indépendante) et de nos propres centres de ressources pour déclencher des alertes. Pour les Diagnostics, nous disposons d’une journalisation étendue, d’un audit et d’un suivi. Le suivi et la surveillance granulaires nous aident à isoler les problèmes et à effectuer une analyse des causes fondamentales rapide et efficace.

Si Office 365 dispose d’actions de récupération automatisées, dans la mesure du possible, les ingénieurs de Microsoft sur demande sont disponibles 24h/24, 7j/7 pour examiner toutes les escalades de gravité 1, et les analyses post mortem de chaque incident de service contribuent à l’apprentissage en continu et amélioration. Cette équipe comprend des ingénieurs de support technique, des développeurs de produits, des responsables de programme, des responsables de produits et un leadership senior. Nos professionnels de l’appel fournissent une sauvegarde opportune et peuvent souvent automatiser des actions de récupération, de sorte que la prochaine fois qu’un événement se produit, il peut être corrigé automatiquement.

Microsoft effectue une analyse approfondie après incident chaque fois qu’un incident de sécurité Office 365 se produit, indépendamment de la magnitude de l’impact. Une révision post-incident se compose d’une analyse de ce qui s’est passé, de la façon dont nous avons répondu et de la façon dont nous prévoyons les incidents similaires à l’avenir. Dans un souci de transparence et de responsabilisation, nous partageons la révision après incident pour les principaux incidents de service avec les clients concernés. Pour plus d’informations, reportez-vous à la rubrique [Office 365 Security Incident Management](https://aka.ms/Office365SIM).

## <a name="assume-breach-methodology"></a>Adopter une méthodologie de violation

Sur la base d’une analyse détaillée des tendances de sécurité, Microsoft préconise et souligne le besoin d’investissements supplémentaires dans les technologies et les processus de sécurité réactifs qui se concentrent sur la détection et la réponse aux menaces émergentes, et non uniquement la prévention des ces menaces. En raison des modifications apportées au paysage des menaces et à l’analyse approfondie, Microsoft a affiné la stratégie de sécurité au-delà de la simple prévention des violations de sécurité à une solution mieux adaptée pour traiter les violations lorsqu’elles se produisent – une stratégie qui prend en compte les principaux événements de sécurité non par exemple, si, lorsque.

Bien que les pratiques en matière de [violations](https://www.microsoft.com/TrustCenter/Security/default.aspx) aient été en place depuis plusieurs années, de nombreux clients ignorent le travail effectué en arrière-plan pour renforcer le Cloud de Microsoft. Supposons que la violation est une mentalité qui guide les investissements de sécurité, les décisions de conception et les pratiques de sécurité opérationnelle. Supposer la violation limite la confiance placée dans les applications, les services, les identités et les réseaux en les traitant tous, internes et externes, comme étant non sécurisées et déjà compromises. Bien que la stratégie supposée violation n’ait pas été prise en charge d’une violation réelle de tout service Microsoft Enterprise ou Cloud, il s’agissait d’une reconnaissance que de nombreuses organisations, dans l’industrie, étaient violées malgré toutes les tentatives de blocage. Tout en empêchant les violations est une partie essentielle des opérations d’une organisation, ces pratiques doivent être testées et complétées en permanence pour gérer efficacement les adversaires modernes et les menaces permanentes. Pour qu’une organisation se prépare à une violation, elle doit d’abord créer et maintenir des procédures de réponse à la sécurité robustes, reproductibles et rigoureusement testées.

Bien que les processus de sécurité de violation, tels que la modélisation des menaces, les révisions de code et les tests de sécurité soient très utiles dans le cadre du [cycle de vie du développement](https://www.microsoft.com/securityengineering/sdl/)de la sécurité, il est possible que la violation offre de nombreux avantages pour prendre en compte la sécurité globale en exerçant et en mesurant les capacités réactives en cas de violation.

Chez Microsoft, nous nous contenterons de le faire par le biais d’exercices de jeux de guerre et de tests de pénétration de site en direct de nos plans de réponse de sécurité dans le but d’améliorer nos capacités de détection et de réponse. Microsoft simule régulièrement des violations du monde réel, effectue une surveillance continue de la sécurité et pratique la gestion des incidents de sécurité pour valider et améliorer la sécurité d’Office 365, Azure et d’autres services Cloud Microsoft.

Microsoft exécute sa stratégie de sécurité supposée en violation à l’aide de deux groupes principaux :
- Équipes de rouge (attaquants)
- Équipe bleue (défendeurs)

Les équipes Microsoft Azure et Office 365 séparent les équipes rouges à plein temps et les équipes bleues.

Appelé «[équipe rouge](https://go.microsoft.com/fwlink/?linkid=518599)», l’approche consiste à tester les systèmes et les opérations Azure et Office 365 à l’aide des mêmes tactiques, techniques et procédures en tant que véritables adversaires, par rapport à l’infrastructure de production en direct, sans l’foreknowledge des équipes d’ingénierie ou d’exploitation. Cela permet de tester les fonctionnalités de détection et de réponse de sécurité de Microsoft et d’identifier les vulnérabilités de production, les erreurs de configuration, les hypothèses non valides et d’autres problèmes de sécurité de manière contrôlée. Chaque violation d’équipe rouge est suivie d’une divulgation complète entre les équipes afin d’identifier les lacunes, les résultats d’adresses et l’amélioration de la réponse aux violations.

**Remarque**: aucune donnée client n’est délibérément ciblée lors des tests de pénétration ou de pénétration de site en direct. Les tests concernent l’infrastructure et les plateformes Office 365 et Azure, ainsi que les propres clients, applications et données de Microsoft. Les locataires, les applications et le contenu des clients hébergés dans Office 365 ou Azure ne sont jamais ciblés.

## <a name="red-teams"></a>Équipe rouge

L’équipe rouge est un groupe de personnes travaillant à plein temps dans Microsoft qui se concentre sur la violation de l’infrastructure, de la plateforme et des propres clients et applications de Microsoft. Il s’agit de l’adversaire dédié (groupe de pirates éthiques) effectuant des attaques ciblées et persistantes contre les services en ligne (infrastructure, plateformes et applications Microsoft, mais pas les applications ou le contenu des clients finaux).

Le rôle de l’équipe rouge est d’attaquer et de pénétrer dans les environnements en suivant les mêmes étapes qu’un adversaire :
 
![Étapes de violation](media/office-365-isolation-breach-stages.png)

Parmi les autres fonctions, les équipes rouges tentent spécifiquement de violer les limites d’isolation client pour trouver des bogues ou des lacunes dans notre conception d’isolation.

## <a name="blue-teams"></a>Équipe bleue

L’équipe bleue se compose d’un ensemble dédié de répondeurs de sécurité ou de membres du travers des organisations de réponse aux incidents de sécurité, d’ingénierie et d’exploitation. Quelle que soit leur marque, ils sont indépendants et fonctionnent indépendamment de l’équipe rouge. L’équipe Blue suit les processus de sécurité établis et utilise les outils et technologies les plus récents pour détecter et répondre aux attaques et à la pénétration. À l’instar des attaques réelles, l’équipe bleue ne sait pas quand ou comment les attaques de l’équipe rouge se produisent ou quelles méthodes peuvent être utilisées. Leur travail, qu’il s’agisse d’une attaque d’équipe rouge ou d’une agression réelle, consiste à détecter et à répondre à tous les incidents de sécurité. Pour cette raison, l’équipe bleue est continuellement en communication et doit réagir aux violations d’équipe rouge de la même manière que pour toute autre violation.

Lorsqu’un adversaire, tel qu’une équipe rouge, a enfreint un environnement, l’équipe bleue doit :

- Collecte des preuves laissées par l’adversaire
- Détection des preuves comme indication de compromission
- Alerter les équipes d’ingénierie et d’exploitation appropriées
- Triez les alertes afin de déterminer si elles justifient une nouvelle enquête.
- Rassemblement du contexte de l’environnement pour l’étendue de la violation
- Former un plan de correction pour contenir ou supprimer l’adversaire
- Exécuter le plan de correction et récupérer suite à une violation

Ces étapes forment la réponse aux incidents de sécurité qui s’exécute parallèlement à l’adversaire, comme indiqué ci-dessous :
 
![Étapes de réponse aux violations](media/office-365-isolation-breach-response-stages.png)

Les violations de l’équipe rouge permettent à l’équipe bleue de détecter et de répondre aux attaques réelles de bout en bout. Plus important encore, il permet une réponse aux incidents de sécurité en cas de violation d’urgence. En outre, en raison de violations de l’équipe rouge, l’équipe bleue améliore sa sensibilisation à la situation, qui peut être précieuse lorsqu’elle traite des violations futures (par rapport à l’équipe rouge ou à un autre adversaire). Tout au long du processus de détection et de réponse, l’équipe bleue fournit une intelligence et une visibilité sur les conditions réelles des environnements qu’elles essaient de défendre. Cette opération est souvent réalisée via l’analyse des données et les analyses d’investigation, effectuées par l’équipe bleue, lors de la réponse à des attaques d’équipe rouge et en établissant des indicateurs de menace, tels que des indicateurs de compromission. De la même manière que l’équipe rouge identifie les lacunes dans l’histoire de la sécurité, les équipes bleues identifient les lacunes de leur capacité à détecter et à répondre. Par ailleurs, étant donné que les équipes rouges de Team modélisent des attaques réelles, l’équipe bleue peut être évaluée avec précision sur leur aptitude ou leur incapacité à gérer les adversaires identifiés et persistants. Enfin, les violations d’équipe rouge mesurent la disponibilité et l’impact de notre réponse de violation.
