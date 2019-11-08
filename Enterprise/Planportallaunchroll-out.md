---
title: Planification de votre plan de déploiement de lancement de portail dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
description: Cet article explique comment planifier le lancement de votre portail dans SharePoint Online et les étapes à suivre pour réussir le lancement de votre portail.
ms.openlocfilehash: cbb2c58498f682d68ac464d224522361a085b062
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027658"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planification de votre plan de déploiement de lancement de portail dans SharePoint Online
Un portail est le site SharePoint par défaut pour votre société ; dans les grandes organisations, il peut y en avoir plusieurs. Vous pouvez considérer qu’il s’agit d’une page de portail à partir du moment où vous vous attendez à ce que plus de 20 % des utilisateurs au sein de votre entreprise accèdent à cette page. Le portail ne doit pas être confondu avec un site d’équipe utilisé par votre service pour collaborer et partager des documents au sein de votre équipe.

Cet article explique comment planifier votre déploiement et déployer un plan de déploiement vers SharePoint Online. Elle fournit également des approches de suivi de la charge traditionnelle qui ne sont pas autorisées sur SharePoint Online. SharePoint Online est un service Cloud et les capacités de chargement, l’intégrité et l’équilibre global de la charge dans le service sont gérées par Microsoft.

Pour vous aider à créer un portail réussi, suivez les principes de base, pratiques et recommandations détaillés dans la rubrique [création, lancement et maintenance d’un portail intègre](https://go.microsoft.com/fwlink/?linkid=2105838) . 

L’approche de déploiement est mise en évidence ci-dessous.

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Vue d’ensemble de la planification de la capacité dans SharePoint Online
Afin d’utiliser efficacement la capacité et de faire face à une croissance inattendue, nous avons Automation dans n’importe quelle batterie de serveurs pour suivre certains scénarios d’utilisation. Bien que la croissance exacte ne soit pas prévisible pour un seul client dans une batterie de serveurs, la somme agrégée des demandes est prévisible dans le temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier une expansion future. Pour plus d’informations sur la planification de la [capacité et le test de charge SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online).

Une partie essentielle du lancement réussi est l’approche « vague » ou « déploiement échelonné » décrite ci-dessous. 

## <a name="can-i-load-test-sharepoint-online"></a>Puis-je charger SharePoint Online de test ?
SharePoint Online est un environnement partagé qui est réparti entre les batteries de serveurs et la mise à l’échelle est ajusté de façon continue. Test de charge d’un environnement, tel que SharePoint Online, dont l’évolution continue entraîne non seulement des résultats inattendus, mais ce n’est pas autorisé. 

En savoir plus : [planification de la capacité et test de charge SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimiser les pages en suivant les recommandations recommandées
Les pages d’un déploiement sur site ne doivent pas simplement être déplacées, car elles se trouvent sur SharePoint Online sans les consulter par rapport aux recommandations pour SharePoint Online. La meilleure approche consiste à toujours optimiser une page d’accueil pour n’importe quel site ou portail dans SharePoint, car c’est ici que la plupart des utilisateurs de votre organisation auront accès comme point de départ pour vos sites.

Voici quelques facteurs de base à prendre en considération :
- Les déploiements sur site peuvent tirer parti des caches traditionnels côté serveur, comme le cache d’objets, le cache de sortie et le cache BLOB. Avec les différences de topologie dans le Cloud, ces options ne sont pas nécessairement disponibles, car les différences d’ampleur considérable les rendent moins viables.
- Toutes les pages/fonctionnalités/personnalisations utilisées pour la consommation en nuage doivent être optimisées pour une latence supérieure, ainsi que pour les emplacements distribués des utilisateurs, de sorte que les utilisateurs dans des régions ou régions différentes bénéficient d’une expérience plus cohérente. Le Cloud offre des optimisations telles que les réseaux de distribution de contenu (CDN) à optimiser pour une base d’utilisateurs distribués, ainsi que pour SharePoint moderne, la dernière bonne configuration (LKG) est utilisée par nos composants WebPart de la zone (OOTB).

### <a name="what-to-do"></a>Que faire :
 - Pour toutes les pages de site dans SharePoint Online, utilisez l' [outil de diagnostic de page](https://aka.ms/perftool), qui est une extension de chrome qui vous aidera à analyser et à fournir des instructions. Il peut être utilisé par les propriétaires de site, les éditeurs, les administrateurs et les développeurs, car il est conçu pour être un point de départ pour l’analyse et l’optimisation.
 - Les développeurs doivent également utiliser des outils de développement comme les outils de développement F12 et CTRL + F12 dans le navigateur sur les pages modernes. [Fiddler](https://www.telerik.com/download/fiddler) peut également être utilisé pour vérifier l’épaisseur de la taille (la taille de la page en mégaoctets) de la page, ainsi que le nombre d’appels et d’éléments influant sur le chargement global de la page. 

Cette section est un bref résumé de l’optimisation des pages.  Pour plus d’informations, consultez la rubrique suivante : [Creating, lancementing and Maintaining a sain Portal](https://go.microsoft.com/fwlink/?linkid=2105838).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Suivre une approche de déploiement Wave/phase
L’approche de grand Bang traditionnelle pour les lancements de site n’autorise pas la vérification que les personnalisations, les sources externes, les services ou les processus ont été testés à l’étendue appropriée. Cela ne signifie pas qu’il prendra des mois pour démarrer, mais il est recommandé pendant au moins plusieurs jours en fonction de la taille de votre organisation. Le suivi d’un plan de déploiement Wave vous offre donc la possibilité de suspendre et de résoudre les problèmes avant de passer à la phase suivante, et donc de diminuer le nombre d’utilisateurs potentiels concernés par les problèmes. SharePoint As a service ajuste votre capacité en fonction de l’utilisation et de l’utilisation prévue, et Pendant que nous n’avons pas besoin de nous avertir de votre lancement, suivez les instructions pour garantir la réussite.
  
Comme indiqué dans l’image suivante, le nombre d’utilisateurs invités est souvent beaucoup plus élevé que ceux qui utilisent le site. Cette image illustre une stratégie de déploiement d’une version. Cette méthode permet d’identifier les moyens d’améliorer le site SharePoint avant que la majorité des utilisateurs ne le voient.
  
![Graphique présentant les utilisateurs invités et actifs](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Dans la phase pilote, il est recommandé d’obtenir les commentaires des utilisateurs que l’organisation approuve et sait être engagés. Ainsi, il est possible d’évaluer la façon dont le système est utilisé, ainsi que la façon dont il est en cours d’exécution.
  
Lors de chaque vague, recueillez les commentaires des utilisateurs sur les fonctionnalités, ainsi que sur les performances pendant chaque vague de déploiement. Cela présente l’avantage d’introduire lentement le système et d’apporter des améliorations au fur et à mesure que le système l’utilise. Cela nous permet également de réagir à l’augmentation de la charge lorsque le site est déployé pour de plus en plus d’utilisateurs et combiné aux instructions de l’optimisation de page, ce qui garantit une expérience positive pour vos utilisateurs.

### <a name="what-to-do"></a>Que faire :
- Déterminez le moment de chaque phase et assurez-vous que vous avez une opportunité d’urgence/de pause, si vous devez effectuer des ajustements avant de poursuivre.
- Planifiez votre premier groupe d’utilisateurs que vous souhaitez activer, afin de vous assurer que vous recevez les commentaires dont vous avez besoin pour aller plus loin. Cela signifie que lorsque cela est possible, sélectionnez un groupe actif d’utilisateurs qui fourniront des commentaires de manière opportune.
- Lors de la planification de chaque vague, essayez de commencer avec une base d’utilisateurs de petite taille (moins de 5000 utilisateurs), puis augmentez la taille des groupes lorsque vous procédez à chaque vague. Cela permet de créer une approche échelonnée et de suspendre facilement les opportunités pouvant être nécessaires.
