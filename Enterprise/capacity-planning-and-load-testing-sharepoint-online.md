---
title: La capacité de planification et de test SharePoint Online de charge
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
description: Cet article explique comment vous pouvez déployer vers SharePoint Online sans effectuer de test de charge traditionnel car il n’est pas autorisée.
ms.openlocfilehash: 6a22ee089adc0817f5c52bbfee5f2b41d7e5d80c
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181025"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>La capacité de planification et de test SharePoint Online de charge

Cet article explique comment vous pouvez déployer vers SharePoint Online sans test de charge traditionnel, étant donné que le test de charge est fortement déconseillé.
  
Bien que le test sur SharePoint Online actif de la charge est fortement déconseillé, que vous pouvez vous assurer que d’autres manières un site ne produit pas une expérience utilisateur médiocre lorsque vous lancez le site. 
  
Avec SharePoint Online vous n’êtes pas obligé planifier la capacité, comme cette opération est effectuée pour vous dans le cadre de notre offre de service. Avec les environnements sur site, les tests de charge sont utilisé pour valider les hypothèses à l’échelle et finalement rechercher le point de dernière minute d’une batterie de serveurs ; par saturation en charge. Nous devons effectuer différemment avec SharePoint Online. Est un environnement de plusieurs client, nous avons protéger tous les clients dans la même batterie de serveurs, afin que nous sera automatiquement limiter les tests de charge. Cela signifie que vous recevrez triste et potentiellement trompeuses résultats si vous essayez de charger votre environnement de test.
  
Un des principaux avantages de SharePoint Online sur un déploiement sur site est l’élasticité du nuage. Notre environnement à grande échelle est configuré pour le service millions d’utilisateurs au quotidien est pourquoi il est important de traiter la capacité efficacement en développant automatiquement des batteries de serveurs, comme et si nécessaire. Cet article explique comment nous prévoir la croissance de la capacité et à l’échelle mise en place. Cet article décrit également les approches d’utiliser qui n’impliquent des tests de charge.
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a>Comment Office 365 prévoit charge et développe la capacité

SharePoint Online serveur capacity management est effectuée par le biais de deux méthodes :
  
- Prévision de la capacité
    
- Équilibrage de charge sur les batteries de serveurs unique
    
Contrairement à la planification pour un environnement local, pour la prévision des capacités dans SharePoint Online, nous sont en mesure de compiler des statistiques et exigences potentiels dans n’importe quel groupe d’un serveur donné du graphique. La demande globale peut ressembler à ceci les demandes dans la zone (où une zone est un groupe de batteries de serveurs SharePoint) ligne de croissance dans l’image ci-dessous :
  
![Graphique illustrant la capacité prédictive : prévisions](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
Lorsque la croissance est imprévisible en toute une batterie de serveurs, la somme agrégée de demandes dans une zone est prévisible. Identifier les tendances de croissance dans SharePoint Online, nous pouvons planifier extension future.
  
Afin d’utiliser la capacité efficacement et de gérer les problèmes liés à la croissance inattendue, dans n’importe quel batterie de serveurs, nous disposons d’automation qui effectue le suivi de la charge frontal et évolution en place, si nécessaire. La principale mesure que nous utilisons comme un signal à l’échelle en amont se termine est charge processeur. Notre objectif est de conserver la charge maximale de l’UC inférieure à 40 %. Il s’agit afin que la mémoire tampon assez d’absorber les pics inattendues. Charge approches 40 % dans un état instable, nous ajouter des serveurs frontaux pour les batteries de serveurs.
  
![Graphique illustrant la capacité prédictive : gestion des batteries de serveurs](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
Des serveurs supplémentaires peuvent être ajoutés rapidement à une batterie de serveurs, à l’aide de celles qui ont été précédemment ajoutés à la zone par le biais de l’utilisation de la prévision. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Comment planifier pour le lancement d’un site ?

Attendez-vous à ce que la batterie de serveurs sur lesquels votre nouveau site lance est automatiquement surveillé afin que les nouveaux serveurs frontaux sont ajoutés, comme indiqué ci-dessus. Pour cette raison, il est inutile toute notification pour le lancement d’un nouveau site.
  
Autres meilleures pratiques pour une seule page dans SharePoint Online, il est peu probable que lancement d’un nouveau site à même de 100 000 utilisateurs aura aucun impact sur la batterie de serveurs.
  
Il existe quelques stratégies pour planifier une version d’un nouveau site SharePoint Online. Comme indiqué dans l’image suivante, le nombre d’utilisateurs qui sont invités est souvent sensiblement supérieur à ceux qui utilisent réellement le site. Cette image montre une stratégie sur la façon de déployer une version. Cette méthode permet non seulement avec chargement performances mais également peut aider à identifier les méthodes permettant d’améliorer le site SharePoint avant de voir la grande majorité des utilisateurs.
  
![Graphique présentant les utilisateurs invités et actifs](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Dans la phase pilote, il est judicieux de recueillir les commentaires des utilisateurs que l’organisation approuve et sait vont être commencé. Ainsi, il est possible évaluer la façon dont le système est utilisé, ainsi que ses performances.
  
Après cela, commence un déploiement à tous les utilisateurs par vagues ; obtention des commentaires et consulter les performances régulièrement. Cela présente l’avantage de lentement présentation du système et améliorer le système permet d’obtenir plus d’utilisation. Cela vous permet également de réagir à l’augmentation de la charge, comme le site est déployée sur un plus grand d’utilisateurs.
  
Enfin, pendant les tests de charge sont interdits, les clients souhaitent configurer ping périodiques au service à mesure disponibilité et latence. Cela permet d’identifier une ligne de base pour leur site. Toutefois, ils doivent être conservés à faible fréquence pour éviter les problèmes décrits précédemment de limitation.
  

