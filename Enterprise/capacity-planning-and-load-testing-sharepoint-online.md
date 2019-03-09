---
title: Capacity planning and load testing SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Cet article explique comment déployer sur SharePoint Online sans effectuer de tests de charge traditionnels, car il n'est pas autorisé.
ms.openlocfilehash: ef5d6c043b4be2e8c5358a9c060459b4c6a92156
ms.sourcegitcommit: 468c8e8d2f951e08cf50301445ad650ef17328aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "30512719"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planification de la capacité et test de charge SharePoint Online.

Cet article explique comment déployer sur SharePoint Online sans test de charge classique, étant donné que le test de charge n'est pas autorisé sur SharePoint Online. SharePoint Online est un service en nuage les capacités de chargement, l'intégrité et l'équilibre global de la charge dans le service sont gérées par Microsoft.
  
La meilleure approche pour garantir le succès du lancement de votre site est de suivre les principes, pratiques et recommandations de base présentés ci-dessous.
  
Dans les environnements locaux, le test de charge permet de valider l'hypothèse d'envergure et de trouver le point de fin d'une batterie de serveurs; en le saturant avec Load. Avec SharePoint Online, nous devons effectuer des opérations différemment. En tant qu'environnement mutualisée, nous devons protéger tous les clients de la même batterie de serveurs; nous allons donc limiter automatiquement les tests de charge. Cela signifie que vous recevrez des résultats dénominations et potentiellement trompants si vous tentez de charger le test de votre environnement.
  
L'un des principaux avantages de SharePoint Online par rapport à un déploiement sur site est l'élasticité du Cloud. Notre environnement à grande échelle est configuré pour traiter des millions d'utilisateurs quotidiennement, de sorte qu'il est important de gérer efficacement les capacités en équilibrant et en étendant les batteries de serveurs. L'article aborde également les approches que vous pouvez utiliser qui n'impliquent pas de tests de charge, mais qui impliquent des instructions qui vous permettront de configurer le lancement réussi. 
  
Si la croissance n'est pas prévisible pour un seul client dans une batterie de serveurs, la somme agrégée des demandes est prévisible dans le temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier une expansion future.
  
Afin d'utiliser efficacement la capacité et de traiter une croissance inattendue, dans n'importe quelle batterie de serveurs, nous disposons d'une automatisation qui effectue le suivi de la charge frontale et évolue, le cas échéant. Il existe plusieurs métriques utilisées avec l'une des principales charges de processeur qui est utilisée comme signal pour mettre à l'horizontale les serveurs frontaux. De plus, comme vous le configurerez dans l'article, nous vous recommandons d'utiliser une approche en phase/vague, car les environnements SQL seront évolutifs en fonction de la charge et de la demande, et le respect des phases et des vagues permet une distribution correcte de la charge et de la croissance. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Comment puis-je planifier un lancement de site?

### <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimiser les pages en suivant les recommandations recommandées
Les pages d'un déploiement sur site ne doivent pas être simplement prises comme sur SharePoint Online sans les consulter par rapport aux recommandations pour SharePoint Online.

Voici quelques facteurs clés à prendre en considération:
- Les déploiements sur site peuvent tirer parti des caches traditionnels côté serveur, comme le cache d'objets, mais avec les différences de topologie dans le Cloud, ces options ne sont pas disponibles.
- Toutes les pages/fonctionnalités/personnalisations utilisées pour la consommation en nuage doivent être optimisées pour plusieurs emplacements, de sorte que les utilisateurs dans des régions ou régions différentes aient une expérience cohérente. Le Cloud offre des optimisations telles que les réseaux de distribution de contenu (CDN) pour optimiser une base d'utilisateurs distribués.

Pour les pages de publication classiques dans SharePoint Online, vous pouvez utiliser l'extension chrome de l' [outil de diagnostic de page](https://aka.ms/perftool) , qui vous aidera à analyser les principales pages d'accueil utilisées par les utilisateurs.
Les outils de développement F12 dans le navigateur ou [Fiddler](https://www.telerik.com/download/fiddler) peuvent être utilisés pour vérifier le poids de la page et le nombre d'appels et d'éléments influant sur le chargement global de la page doit être revu et optimisé. Une liste de recommandations, y compris l'utilisation de réseaux de distribution de contenu et d'autres optimisations, peut être consultée dans l'article [régler les performances de SharePoint Online](https://aka.ms/spoperformance) .

### <a name="wave--phase-approach"></a>Approche Wave/phase
L'approche de grand Bang traditionnelle pour les lancements de sites n'autorise pas efficacement la vérification que les personnalisations, les sources externes, les services ou les processus ont été testés à la bonne taille. SharePoint As a redimensionne également votre capacité en fonction de l'utilisation et de l'utilisation prévue et, même si nous n'avons pas besoin de vous avertir de votre lancement de site, suivez les instructions ci-dessous pour vous assurer de la réussite.
  
Comme indiqué dans l'image suivante, le nombre d'utilisateurs invités est souvent beaucoup plus élevé que ceux qui utilisent le site. Cette image illustre une stratégie de déploiement d'une version. Cette méthode permet d'identifier les moyens d'améliorer le site SharePoint avant que la majorité des utilisateurs ne le voient. Elle permet également de suspendre un déploiement si vous rencontrez des problèmes dans l'une des phases/ondes, limitant ainsi le nombre potentiel d'utilisateurs concernés.
  
![Graphique présentant les utilisateurs invités et actifs](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Dans la phase pilote, il est recommandé d'obtenir les commentaires des utilisateurs que l'organisation approuve et sait être engagés. Ainsi, il est possible d'évaluer la façon dont le système est utilisé, ainsi que la façon dont il est en cours d'exécution.
  
Lors de chaque vague, recueillez les commentaires des utilisateurs sur les fonctionnalités, ainsi que sur les performances pendant chaque vague de déploiement. Cela présente l'avantage d'introduire lentement le système et d'apporter des améliorations au fur et à mesure que le système l'utilise. Cela nous permet également de réagir à l'augmentation de la charge lorsque le site est déployé pour de plus en plus d'utilisateurs.
