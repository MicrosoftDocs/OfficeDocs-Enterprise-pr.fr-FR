---
title: Feuille de route pour la fin de l’assistance pour Project Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: Le 10 octobre 2017, la prise en charge s’est terminée pour Project Server 2007, Project Portfolio Server et Project 2007. Utilisez cet article pour planifier votre mise à niveau maintenant.
ms.openlocfilehash: c21d9d1c2539f66587243f04d4d874649d6bf460
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746237"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Project Server 2007

*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 entreprise.*

Prise en charge terminée pour les serveurs et applications Office 2007 dans 2017, et vous devez prendre en compte les plans de migration. Si vous utilisez actuellement Project Server 2007, Notez qu’il et les autres produits associés ont les dates de fin de prise en charge suivantes :
  
|**Produit**|**Fin de la date de prise en charge**|
|:-----|:-----|
|Project Server 2007  <br/> |10 octobre 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 octobre 2017  <br/> |
|Project 2007 standard  <br/> |10 octobre 2017  <br/> |
|Project 2007 professionnel  <br/> |10 octobre 2017  <br/> |
   
Pour plus d’informations sur les serveurs Office 2007 qui arrivent à la retraite, voir [Upgrade from Office 2007 Servers and client Products](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

Project Server, comme presque tous les produits Microsoft, a un cycle de vie de la prise en charge au cours duquel nous fournissons de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit. Étant donné que Project Server 2007 a atteint sa fin de prise en charge le 10 octobre 2017, Microsoft ne fournit plus :
  
- Support technique pour les problèmes susceptibles de se produire.
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Project Server 2007 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées ci-dessus, nous vous recommandons vivement de procéder à une migration à partir de Project Server 2007 dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Si vous utilisez Project Server 2007, vous devez explorer vos options de migration, qui sont les suivantes :
  
- Migrer vers Project Online
    
- Migrer vers une version plus récente de Project Server (de préférence Project Server 2016).
    
|**Pourquoi migrer vers Project Online ?**|**Pourquoi migrer vers Project Server 2016**|
|:-----|:-----|
| J’ai des utilisateurs mobiles.  <br/>  Les coûts de migration sont un sujet important (matériel, logiciel, heures et efforts à mettre en œuvre, etc.).  <br/>  Après la migration, les coûts de maintenance de mon environnement sont importants (par exemple, mises à jour automatiques, temps de fonctionnement garanti, etc.).  <br/> | Les règles d’entreprise m’empêchent de faire fonctionner mon entreprise dans le Cloud.  <br/>  J’ai besoin de contrôler les mises à jour de mon environnement.  <br/> |
   
> [!NOTE]
> Pour plus d’informations sur les options de navigation à partir de vos serveurs Office 2007, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2007](upgrade-from-office-2007-servers-and-products.md). Notez que Project Server ne prend pas en charge une configuration hybride, car Project Server et Project Online ne peuvent pas partager la même liste de ressources. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Éléments importants à prendre en compte lors de la planification de la migration à partir de Project Server 2007

Vous devez tenir compte des éléments suivants lors de la planification de la migration à partir de Project Server 2007 :
  
- **Obtenir de l’aide auprès d’un partenaire Microsoft** : la mise à niveau à partir de Project Server 2007 peut être complexe et nécessite une préparation et une planification considérables. Cela peut s’avérer particulièrement complexe si vous n’étiez pas le seul à configurer et configuré à l’origine Project Server 2007. Heureusement, il existe des partenaires Microsoft que vous pouvez utiliser pour effectuer ces actions pour une vie, que vous envisagez de migrer vers Project Server 2016 ou Project online. Vous pouvez rechercher un partenaire Microsoft pour vous aider dans votre migration sur le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Vous pouvez extraire une liste de tous les partenaires Microsoft ayant une expertise dans Project en effectuant une recherche sur le terme *Gold Project and Portfolio Management* . 
    
- **Planifiez vos personnalisations** -sachez que la plupart des personnalisations que vous travaillez dans votre environnement project Server 2007 risquent de ne pas fonctionner lors de la migration vers project Server 2016 ou Project online. Il existe des différences importantes en matière d’architecture Project Server entre les versions, ainsi que les systèmes d’exploitation, les serveurs de bases de données et les navigateurs Web clients requis qui sont pris en charge pour fonctionner avec la version la plus récente. Préparez-vous à tester ou à recréer vos personnalisations selon vos besoins dans votre nouvel environnement. La planification de votre mise à niveau permettra également de vérifier si une personnalisation spécifique est réellement nécessaire lorsque vous avancez. [Créer un plan pour les personnalisations actuelles lors de la mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) dispose de certaines informations générales sur l’évaluation et la planification de vos personnalisations actuelles lors de la mise à niveau. 
    
- **Temps et patience** : la planification, l’exécution et le test de la mise à niveau prennent beaucoup de temps et de travail, en particulier si vous effectuez une mise à niveau vers Project Server 2016. Par exemple, si vous effectuez une migration de Project Server 2007 vers Project Server 2016, vous devez d’abord effectuer une migration de Project Server 2007 vers Project Server 2010, puis vérifier vos données, puis effectuer la même opération lors de la migration vers chaque version successive. Vous voudrez peut-être vérifier auprès d’un partenaire Microsoft Comment comparer vos coûts avec leurs estimations du temps qu’il leur faudra pour le faire et à quel coût. 
    
## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2007 vers Project Online, vous pouvez effectuer les opérations suivantes pour migrer manuellement vos données de plan de projet :
  
1. Enregistrez vos plans de projet à partir de Project Server 2003 vers. Format MPP.
    
2. À l’aide de Project Professionnel 2013, Project Professional 2016 ou le client de bureau Project Online, ouvrez chaque fichier. mpp, puis enregistrez-le et publiez-le dans Project online.
    
Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréer des champs personnalisés ou des calendriers d’entreprise nécessaires). Les partenaires de Microsoft peuvent également vous aider.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11). <br/> |Comment configurer et utiliser Project online.  <br/> |
|[Descriptions de service Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informations sur les différents plans Project Online disponibles.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Bien que nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en migrant vers Project Online, nous comprenons également que certaines organisations doivent conserver les données de projet dans un environnement local. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2007 vers Project Server 2010, Project Server 2013 ou Project Server 2016.
  
Nous vous recommandons de migrer vers Project Server 2016 si vous ne pouvez pas effectuer une migration vers Project online. Project Server 2016 inclut toutes les fonctionnalités et les améliorations incluses dans les versions précédentes de Project Server, et correspond le mieux à l’expérience disponible avec Project Online (même si certaines fonctionnalités sont disponibles uniquement dans Project Online).
  
Une fois toutes les migrations terminées, vérifiez vos données pour vous assurer qu’elles ont été correctement migrées.
  
> [!NOTE]
> Si vous envisagez de migrer uniquement vers Project Server 2010 si vous êtes limité à une solution locale, il est important de noter qu’il n’en a que quelques années supplémentaires. La date de fin de prise en charge de Project Server 2010 avec Service Pack 2 est 10/13/2020. Pour plus d’informations sur les dates de fin de prise en charge, consultez la rubrique [stratégie de cycle de vie des produits Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Comment migrer vers Project Server 2016 ?

Les différences d’architecture entre Project Server 2007 et Project Server 2016 empêchent un chemin de migration direct. Cela signifie que vous devrez migrer vos données Project Server 2007 vers la version suivante de Project Server jusqu’à ce que vous procédiez à la mise à niveau vers Project Server 2016.
  
Vous devrez effectuer les opérations suivantes pour effectuer une mise à niveau vers Project Server 2016 :
  
1. Étape 1 : migrer de Project Server 2007 vers Project Server 2010.
    
2. Étape 2 : migrer de Project serve 2010 vers Project Server 2013.
    
3. Étape 3 : migrer de Project Server 2013 vers Project Server 2016.
    
Une fois toutes les migrations terminées, vérifiez vos données pour vous assurer qu’elles ont été correctement migrées.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Étape 1 : migrer de Project Server 2007 vers Project Server 2010

Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2007 vers Project Server 2010, consultez la rubrique [mise à niveau vers Project server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) content Set on technet. 
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble de la mise à niveau vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2007 vers Project Server 2010.  <br/> |
|[Planifier une mise à niveau vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2007 vers Project Server 2010, y compris la configuration système requise.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Comment effectuer une mise à niveau ?

Bien que vous puissiez trouver des informations sur la mise à niveau dans le jeu de contenu [mise à niveau vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) , il est important de comprendre qu’il existe deux méthodes distinctes pour effectuer la mise à niveau : 
  
- **Mise à niveau avec attachement de base de données :** Cette méthode met uniquement à niveau le contenu de votre environnement, pas les paramètres de configuration. Cette opération est requise si vous effectuez une mise à niveau à partir d’Office Project Server 2007 déployé sur du matériel qui prend uniquement en charge un système d’exploitation de serveur 32 bits. Il existe deux types de méthodes de mise à niveau par attachement de base de données : 
    
  - **Mise à niveau complète avec liaison de base de données** : migre les données de projet stockées dans les bases de données Office project Server 2007, ainsi que les données de site Microsoft Project Web App (PWA) stockées dans une base de données de contenu SharePoint. 
    
  - **Mise à niveau principale avec liaison de base de données** : migre uniquement les données de projet stockées dans les bases de données Project Server. 
    
- **Mise à niveau sur place**: les données de configuration de la batterie de serveurs et tout le contenu de la batterie de serveurs sont mis à niveau sur le matériel existant, dans un ordre fixe. Lorsque vous démarrez le processus de mise à niveau sur place, le programme d’installation met l’ensemble de la batterie de serveurs hors connexion et les sites Web et Microsoft Project Web App ne sont pas disponibles jusqu’à ce que la mise à niveau soit terminée, puis le programme d’installation redémarre le serveur. Lorsque vous effectuez une mise à niveau sur place, vous ne pouvez ni suspendre la version précédente, ni la restaurer. Il est fortement recommandé de créer une image en miroir de votre environnement de production et de procéder à la mise à niveau sur place de cet environnement, et non à votre environnement de production. 
    
Ressources supplémentaires :
  
- [SuperFlow pour la mise à niveau de Microsoft Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Migration de Project Server 2007 vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Considérations relatives à la mise à niveau des composants WebPart Project Web App](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Kit de développement logiciel (SDK) Project](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>Étape 2 : migrer vers Project Server 2013

Après avoir effectué une migration vers Project Server 2010 et vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2013.
  
Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013, consultez la rubrique [mise à niveau vers Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) content Set on technet. 
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013.  <br/> |
|[Planifier une mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la configuration système requise.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à connaître sur la mise à niveau vers cette version

Les nouveautés [de la mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) vous indiquent des modifications importantes de la mise à niveau pour cette version : 
  
- Il n’existe pas de mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour la mise à niveau de Project Server 2010 vers Project Server 2013.
    
- Le processus de mise à niveau ne convertit pas uniquement vos données Project Server 2010 vers le format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.
    
- SharePoint Server 2013 et Project Server 2013 ont été remplacés par l’authentification basée sur les revendications à partir de la version précédente. Vous devrez prendre en compte lors de la mise à niveau si vous utilisez l’authentification classique. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Ressources supplémentaires :
  
- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La consolidation de base de données, Project Server 2010 vers 2013 migration en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Étape 3 : migrer vers Project Server 2016

Après avoir effectué une migration vers Project Server 2013 et vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2016.
  
Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016, consultez la rubrique mise à niveau vers Project Server 2016 content Set on TechNet.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d'ensemble du processus de mise à niveau vers Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.  <br/> |
|[Planifier la mise à niveau vers Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2013 vers Project Server 2016, y compris.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à connaître sur la mise à niveau vers cette version

Les [éléments que vous devez connaître à propos de la mise à niveau de Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841827) vous indiquent des modifications importantes pour la mise à niveau de cette version, notamment : 
  
- Lorsque vous créez votre environnement Project Server 2016 vers lequel vous allez migrer vos données Project Server 2013, Notez que les fichiers d’installation de Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, consultez la rubrique [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Les plans de ressources sont déconseillés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers les engagements de ressources dans Project Server 2016 et dans Project online. Pour plus d’informations, voir [vue d’ensemble : engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrer à partir du serveur de portefeuille 2007

Project Portfolio Server 2007 a été utilisé avec Project Server 2007 pour la stratégie de portefeuille, la définition des priorités et l’optimisation. Aucune version supplémentaire de Project Portfolio Server n’a été créée après cette version. Toutefois, les fonctionnalités de gestion de portefeuilles sont disponibles dans Project Server 2016 et dans la version Premium de Project online. Les données de Project Portfolio Server 2007 ne peuvent pas être migrées vers. Les données telles que les axes stratégiques doivent être recréées.
  
Autres ressources :
  
- [Descriptions du service Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): voir les fonctionnalités de gestion de portefeuille incluses dans project Server 2016 et Project Online Premium.
    
- [Guide de migration de Microsoft Office Project Portfolio Server 2007](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Sujets associés

[Feuille de route de prise en charge de SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  

