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
ms.openlocfilehash: 490d05598c42cd5d94f61dd21ee5a11701d4b4a7
ms.sourcegitcommit: 033156d46ac0fb5f05d2b1a594d5ef368b93b893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2018
ms.locfileid: "27134669"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="50182-103">La capacité de planification et de test SharePoint Online de charge</span><span class="sxs-lookup"><span data-stu-id="50182-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="50182-104">Cet article explique comment vous pouvez déployer vers SharePoint Online sans effectuer de test de charge traditionnel car il est fortement déconseillé.</span><span class="sxs-lookup"><span data-stu-id="50182-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is strongly discouraged.</span></span>
  
<span data-ttu-id="50182-105">Bien que le test sur SharePoint Online actif de la charge est fortement déconseillé, que vous pouvez vous assurer que d’autres manières un site ne produit pas une expérience utilisateur médiocre lorsque vous lancez le site.</span><span class="sxs-lookup"><span data-stu-id="50182-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="50182-p101">Avec SharePoint Online vous n’êtes pas obligé planifier la capacité, comme cette opération est effectuée pour vous dans le cadre de notre offre de service. Avec les environnements sur site, les tests de charge sont utilisé pour valider les hypothèses à l’échelle et finalement rechercher le point de dernière minute d’une batterie de serveurs ; par saturation en charge. Nous devons effectuer différemment avec SharePoint Online. Est un environnement de plusieurs client, nous avons protéger tous les clients dans la même batterie de serveurs, afin que nous sera automatiquement limiter les tests de charge. Cela signifie que vous recevrez triste et potentiellement trompeuses résultats si vous essayez de charger votre environnement de test.</span><span class="sxs-lookup"><span data-stu-id="50182-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="50182-p102">Un des principaux avantages de SharePoint Online sur un déploiement sur site est l’élasticité du nuage. Notre environnement à grande échelle est configuré pour le service millions d’utilisateurs au quotidien est pourquoi il est important de traiter la capacité efficacement en développant automatiquement des batteries de serveurs, comme et si nécessaire. Cet article explique comment nous prévoir la croissance de la capacité et à l’échelle mise en place. Cet article décrit également les approches d’utiliser qui n’impliquent des tests de charge.</span><span class="sxs-lookup"><span data-stu-id="50182-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="50182-115">Comment Office 365 prévoit charge et développe la capacité</span><span class="sxs-lookup"><span data-stu-id="50182-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="50182-116">SharePoint Online serveur capacity management est effectuée par le biais de deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="50182-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="50182-117">Prévision de la capacité</span><span class="sxs-lookup"><span data-stu-id="50182-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="50182-118">Équilibrage de charge sur les batteries de serveurs unique</span><span class="sxs-lookup"><span data-stu-id="50182-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="50182-p103">Contrairement à la planification pour un environnement local, pour la prévision des capacités dans SharePoint Online, nous sont en mesure de compiler des statistiques et exigences potentiels dans n’importe quel groupe d’un serveur donné du graphique. La demande globale peut ressembler à ceci les demandes dans la zone (où une zone est un groupe de batteries de serveurs SharePoint) ligne de croissance dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="50182-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Graphique illustrant la capacité prédictive : prévisions](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="50182-p104">Lorsque la croissance est imprévisible en toute une batterie de serveurs, la somme agrégée de demandes dans une zone est prévisible. Identifier les tendances de croissance dans SharePoint Online, nous pouvons planifier extension future.</span><span class="sxs-lookup"><span data-stu-id="50182-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="50182-p105">Afin d’utiliser la capacité efficacement et de gérer les problèmes liés à la croissance inattendue, dans n’importe quel batterie de serveurs, nous disposons d’automation qui effectue le suivi de la charge frontal et évolution en place, si nécessaire. La principale mesure que nous utilisons comme un signal à l’échelle en amont se termine est charge processeur. Notre objectif est de conserver la charge maximale de l’UC inférieure à 40 %. Il s’agit afin que la mémoire tampon assez d’absorber les pics inattendues. Charge approches 40 % dans un état instable, nous ajouter des serveurs frontaux pour les batteries de serveurs.</span><span class="sxs-lookup"><span data-stu-id="50182-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Graphique illustrant la capacité prédictive : gestion des batteries de serveurs](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="50182-130">Des serveurs supplémentaires peuvent être ajoutés rapidement à une batterie de serveurs, à l’aide de celles qui ont été précédemment ajoutés à la zone par le biais de l’utilisation de la prévision.</span><span class="sxs-lookup"><span data-stu-id="50182-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="50182-131">Comment planifier pour le lancement d’un site ?</span><span class="sxs-lookup"><span data-stu-id="50182-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="50182-p106">Attendez-vous à ce que la batterie de serveurs sur lesquels votre nouveau site lance est automatiquement surveillé afin que les nouveaux serveurs frontaux sont ajoutés, comme indiqué ci-dessus. Pour cette raison, il est inutile toute notification pour le lancement d’un nouveau site.</span><span class="sxs-lookup"><span data-stu-id="50182-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="50182-134">Autres meilleures pratiques pour une seule page dans SharePoint Online, il est peu probable que lancement d’un nouveau site à même de 100 000 utilisateurs aura aucun impact sur la batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="50182-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="50182-p107">Il existe quelques stratégies pour planifier une version d’un nouveau site SharePoint Online. Comme indiqué dans l’image suivante, le nombre d’utilisateurs qui sont invités est souvent sensiblement supérieur à ceux qui utilisent réellement le site. Cette image montre une stratégie sur la façon de déployer une version. Cette méthode permet non seulement avec chargement performances mais également peut aider à identifier les méthodes permettant d’améliorer le site SharePoint avant de voir la grande majorité des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="50182-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Graphique présentant les utilisateurs invités et actifs](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="50182-p108">Dans la phase pilote, il est judicieux de recueillir les commentaires des utilisateurs que l’organisation approuve et sait vont être commencé. Ainsi, il est possible évaluer la façon dont le système est utilisé, ainsi que ses performances.</span><span class="sxs-lookup"><span data-stu-id="50182-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="50182-p109">Après cela, commence un déploiement à tous les utilisateurs par vagues ; obtention des commentaires et consulter les performances régulièrement. Cela présente l’avantage de lentement présentation du système et améliorer le système permet d’obtenir plus d’utilisation. Cela vous permet également de réagir à l’augmentation de la charge, comme le site est déployée sur un plus grand d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="50182-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="50182-p110">Enfin, pendant les tests de charge sont interdits, les clients souhaitent configurer ping périodiques au service à mesure disponibilité et latence. Cela permet d’identifier une ligne de base pour leur site. Toutefois, ils doivent être conservés à faible fréquence pour éviter les problèmes décrits précédemment de limitation.</span><span class="sxs-lookup"><span data-stu-id="50182-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

