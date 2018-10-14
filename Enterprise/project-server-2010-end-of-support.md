---
title: Plan de Project Server 2010-fin du support
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Sur le 13 octobre 2020, fin du support pour Project Server 2010. Utilisez cet article pour planifier votre mise à niveau maintenant.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549781"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Fin du projet Server 2010 de prise en charge de la feuille de route

Fin prise en charge pour les applications et les serveurs Office 2010 dans 2010, et vous devez prendre en compte les plans pour la migration. Si vous utilisez Project Server 2010, notez qu’il et ces autres produits connexes a la fin des dates de prise en charge suivante :
  
|**Produit**|**fin de la date de la prise en charge**|
|:-----|:-----|
|Project Server 2010  <br/> |13 octobre 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 octobre 2020  <br/> |
|Project 2010 Standard  <br/> |13 octobre 2020  <br/> |
|Project 2010 Professional  <br/> |13 octobre 2020  <br/> |
   
Pour plus d’informations sur les serveurs Office 2010 a atteint sa retraite, voir [mise à niveau à partir des serveurs Office 2010 et les produits clients](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Quel ne prend fin moyenne de la prise en charge ?

Project Server, comme presque tous les produits Microsoft, a un cycle de vie de prise en charge au cours de laquelle nous fournissons des nouvelles fonctionnalités, des correctifs, des correctifs de sécurité et ainsi de suite. Ce cycle de vie dure généralement dix ans à compter de la date de publication initiale du produit, et la fin de ce cycle de vie est appelée fin du produit de prise en charge. Étant donné que Project Server 2010 arrivé à la fin de la prise en charge sur 10 octobre 2020, Microsoft ne fournira plus :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Bogue résout les problèmes qui ont été identifiés et qui peut avoir un impact sur la stabilité et la facilité d’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités qui sont découvertes et qui peuvent rendre le serveur vulnérables aux failles de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Project Server 2010 continuera à s’exécuter après cette date. Toutefois, en raison des modifications mentionnées ci-dessus, il est vivement recommandé que vous migrez à partir de Project Server 2010 dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Si vous utilisez Project Server 2010, vous devez Explorer vos options de migration, qui sont :
  
- Migrer vers Project Online
    
- Migrer vers une nouvelle version sur site de Project Server (préférence Project Server 2019).
    
|**Pourquoi préférez migration vers Project Online**|**Pourquoi préférez à la migration vers Project Server 2019**|
|:-----|:-----|
| Je dispose des utilisateurs mobiles.  <br/>  Coûts de migration sont un problème (matériel, logiciel, heures et effort à implémenter, etc.).  <br/>  Après la migration, les coûts de maintenance mon environnement sont un problème (par exemple, mises à jour automatiques, garantie de disponibilité, etc..).  <br/> | Règles métier m’empêchent de ma société dans le nuage.  <br/>  J’ai besoin de contrôle des mises à jour pour mon environnement.  <br/> |
   
> [!NOTE]
> Pour plus d’informations sur les options de déplacement de vos serveurs Office 2010, voir les [ressources pour vous aider à mettre à niveau à partir d’Office 2010 des serveurs et clients](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Notez que Project Server ne prend pas en charge une configuration hybride depuis Project Server et Project Online ne peuvent pas partager la même liste des ressources. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Considérations importantes que vous devez prendre lors de la planification de la migration à partir de Project Server 2010

Vous devez prendre en compte les éléments suivants lors de la planification de la migration à partir de Project Server 2010 :
  
- **Obtenir de l’aide d’un partenaire Microsoft** - mise à niveau de Project Server 2010 peut être difficile et nécessite beaucoup de préparation et planification. Il peut être difficile en particulier si vous n’avez pas celui pour installer et configurer Project Server 2010 à l’origine. Heureusement, il existe Microsoft Partners vous pouvez activer à qui cela vie, si vous envisagez de migration vers Project Server 2019 ou Project Online. Vous pouvez rechercher un Microsoft Partner faciliter votre migration sur le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Vous pouvez extraire à la liste de tous les Microsoft Partner technologiques offrant une expertise dans Project en effectuant une recherche sur le terme *projet or et gestion de portefeuille* . 
    
- **Planifier vos personnalisations** - à l’esprit que des personnalisations que vous avez fonctionne dans votre environnement Project Server 2010 peut ne pas fonctionneront lors de la migration vers Project Server 2019 ou Project Online. Il existe des différences big dans l’architecture de Project Server entre les versions, ainsi que les systèmes d’exploitation requis, les serveurs de base de données et les navigateurs web clients pris en charge pour fonctionner avec la version la plus récente. Disposer d’un plan en place pour tester ou reconstruire vos personnalisations selon vos besoins dans votre nouvel environnement. Planification de votre mise à niveau seront également une bonne occasion pour vérifier si une personnalisation spécifique est réellement nécessaire lorsque vous avancez. [Créer un plan pour les personnalisations actuelles pendant la mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) possède des informations très générales sur l’évaluation et planification de vos personnalisations actuelles lors de la mise à niveau. 
    
- **Temps et patience** - mise à niveau de planification, d’exécution et le test peut prendre beaucoup de temps et l’effort, en particulier si vous mettez à niveau vers Project Server 2019. Par exemple, si vous migrez à partir de Project Server 2010 vers Project Server 2019, vous serez devez migrer à partir de Project Server 2010 vers Project Server 2013, puis vérifier si vos données et puis faire la même chose lorsque vous migrez vers chaque version successive (projet Serveur 2016, puis 2019 de Project Server). Vous voudrez peut-être renseignez-vous auprès de Microsoft Partner pour comparer les coûts et leurs estimations de la durée nécessaire pour les faire et à quel coût estimés. 
    
## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer à partir de Project Server 2010 et Project Online, vous pouvez effectuer les opérations suivantes pour migrer manuellement les données de votre plan de projet :
  
1. Enregistrez vos plans de projet à partir de Project Server 2010. Format MPP.
    
2. À l’aide de Project Professionnel 2016, Project Professionnel 2019 ou le Client de bureau Project Online, ouvrir chaque fichier .mpp, puis enregistrer et publier dans Project Online.
    
Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréez les champs personnalisés nécessaires ou les calendriers d’entreprise). Microsoft Partners peuvent également vous aider à cela.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Prise en main de Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Comment configurer et utiliser Project Online.  <br/> |
|[Descriptions de Service en ligne de projet](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Plus d’informations sur les différents plans de projet en ligne sont disponibles pour vous.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une nouvelle version sur site de Project Server

Pendant que nous pensons fortement que vous pouvez obtenir la meilleure expérience utilisateur et la valeur par migration vers Project Online, aussi bien que certaines organisations ont besoin de conserver les données de projet dans un environnement sur site. Si vous choisissez de conserver votre projet données locaux, vous pouvez migrer votre environnement Project Server 2010 vers Project Server 2013, Project Server 2016 ou Project Server 2019.
  
Nous vous recommandons de migrer vers Project Server 2019 si vous ne pouvez pas migrer vers Project Online. Project Server 2019 inclut la plupart de la clé les fonctionnalités et les améliorations incluses avec les versions précédentes de Project Server, et il correspond le mieux à l’expérience disponible avec Project Online (bien que certaines fonctionnalités sont disponibles uniquement dans Project Online).
  
Après la fin de chaque migration, vous devez vérifier vos données pour vous assurer qu’il a été correctement migrées.
  
> [!NOTE]
> Si vous envisagez de migration uniquement vers Project Server 2013 si vous êtes limité à une solution sur site, il est important de noter qu’il a uniquement un petit nombre d’années de prise en charge de la gauche. Project Server 2013 avec Service Pack 2 est prise en charge de date de fin du 13/10/2023. Pour plus d’informations sur la prise en charge des dates de fin de, voir la [Politique de support Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Comment migrer vers Project Server 2019 ?

Les différences architecturales entre Project Server 2010 et Project Server 2019 empêche un chemin d’accès de la migration directe. Cela signifie que vous devrez migrer vos données Project Server 2010 vers la version suivante successive de Project Server jusqu'à ce que vous mettez à niveau vers Project Server 2019.
  
Vous devez effectuer les opérations suivantes pour mettre à niveau vers Project Server 2019 :
  
1. Étape 1 : Migrer vos données à partir de Project Server 2010 vers Project Server 2013.
    
2. Étape 2 : Migrer vos données à partir de Project 2013 de servir à Project Server 2016.
    
3. Étape 3 : Migrer vos données à partir de Project Server 2016 vers Project Server 2019.
    
Après la fin de chaque migration, vous devez vérifier vos données pour vous assurer qu’il a été correctement migrées.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Étape 1 : Effectuer une migration vers Project Server 2013

Votre première étape de migration des données de Project Server 2010 vers Project Server 2019 doit tout d’abord effectuer la migration vers Project Server 2013. 
  
Pour une présentation générale de ce que vous devez faire pour mettre à niveau à partir de Project Server 2010 vers Project Server 2013, consultez le jeu de contenu [de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) sur TechNet. 
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Obtenez une vision détaillée de ce que vous devez faire pour mettre à niveau à partir de Project Server 2010 vers Project Server 2013.  <br/> |
|[Planifier la mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Examinez les considérations que vous devez prendre lors de la mise à niveau à partir de Project Server 2010 vers Project Server 2013, y compris la configuration système requise.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Choses à savoir sur la mise à niveau vers cette version

[Nouveautés de la mise à niveau de Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) vous indique quelques modifications importantes pour la mise à niveau pour cette version, les plus notables en cours : 
  
- Il n’existe aucune mise à niveau sur place vers Project Server 2013. L’attachement de base de données est la seule méthode prise en charge pour la mise à niveau à partir de Project Server 2010 vers Project Server 2013.
    
- Le processus de mise à niveau seront convertir pas vos données Project Server 2010 au format de Project Server 2013, mais également consolide les quatre bases de données Project Server 2010 pour une base de données Project Web App.
    
- SharePoint Server 2013 et Project Server 2013 modifié à l’authentification basée sur les revendications à partir de la version précédente. Vous devrez prendre lors de la mise à niveau si vous utilisez l’authentification classique. Pour plus d’informations, voir [migrer à partir de l’authentification en mode classique pour l’authentification basée sur les revendications dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Ressources supplémentaires :
  
- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramme du processus de mise à jour Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La Consolidation une base de données Project Server 2010 pour 2013 Migration en 8 étapes](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Étape 2 migrer vers Project Server 2016

Après la migration vers Project Server 2013 et vérifier que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2016.
  
Pour une présentation générale de la marche à suivre pour mettre à niveau à partir de Project Server 2013 vers Project Server 2016, voir le jeu de contenu de [mise à niveau vers Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d'ensemble du processus de mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Obtenez une vision détaillée de ce que vous devez faire pour mettre à niveau à partir de Project Server 2013 vers Project Server 2016.  <br/> |
|[Planifier la mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau à partir de Project Server 2013 vers Project Server 2016.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Choses à savoir sur la mise à niveau vers cette version

[Choses à savoir à propos de Project Server 2016 mise à niveau](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) indique quelques modifications importantes pour la mise à niveau pour cette version, notamment : 
  
- Lorsque vous créez votre environnement Project Server 2016 à laquelle vous migrez vos données Project Server 2013, notez que les fichiers d’installation Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, voir [déployer Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Plans de ressources sont déconseillées dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrées à Engagements de ressources dans Project Server 2016 et Project Online. Voir [vue d’ensemble : engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) pour plus d’informations. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Étape 3 migrer vers Project Server 2019

Après la migration vers Project Server 2016 et vérifier que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2019.
  
Pour une présentation générale de la marche à suivre pour mettre à niveau à partir de Project Server 2016 vers Project Server 2019, voir le jeu de contenu de [mise à niveau vers Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble de la 2019 serveur Project des processus de mise à niveau](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Obtenez une vision détaillée de ce que vous devez faire pour mettre à niveau à partir de Project Server 2013 vers Project Server 2016.  <br/> |
|[Planifier la mise à niveau vers Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau à partir de Project Server 2016 vers Project Server 2019.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Choses à savoir sur la mise à niveau vers cette version

[Choses à savoir à propos de Project Server 2019 mise à niveau](https://go.microsoft.com/fwlink/p/?linkid=841827) indique quelques modifications importantes pour la mise à niveau pour cette version, notamment : 
  
- Le processus de mise à niveau doit migrer vos données à partir de votre base de données Project Server 2016 à la base de données de contenu de SharePoint Server 2019.  Project Server 2019 crée ne propriétaire de base de données Project Server dans la batterie de serveurs SharePoint.

- Après la mise à niveau, vous devez être conscient de plusieurs modifications dans Project Web App.  Pour obtenir une description, voir [Nouveautés de Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Migrer à partir de Portfolio Server 2010

Project Portfolio Server 2010 a été utilisé avec Project Server 2010 pour l’optimisation, définition des priorités et stratégie de portefeuille. Aucune version de Project Portfolio Server supplémentaires ont été créées après cette version. Toutefois, les fonctionnalités de gestion de portefeuille sont disponibles dans les versions ultérieures de Project Server et la version Premium de Project Online. Impossible de migrer vers des données à partir de Project Portfolio Server 2010. Données telles que les pilotes d’entreprise devra être recréée.
  
Autres ressources :
  
- [Descriptions du Service Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): voir les fonctionnalités de gestion de portefeuille qui sont incluses avec Project Server 2016 et Project Online Premium.
    
- [Guide de migration de Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Rubriques connexes

[Mise à niveau de SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Ressources pour vous aider à mettre à niveau à partir d’Office 2010 des serveurs et des clients](upgrade-from-office-2010-servers-and-products.md)
  

