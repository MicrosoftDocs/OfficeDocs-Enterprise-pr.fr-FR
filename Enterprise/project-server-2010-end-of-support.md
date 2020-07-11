---
title: Feuille de route Project Server 2010 end-support
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Les fins de prise en charge de Project Server 2010 se terminent le 13 avril 2021. Utilisez cet article pour effectuer une mise à niveau vers Project Online ou une version plus récente de Project Server en local.
ms.openlocfilehash: cd209b51c94abe1a32b5d48bde79a3d1a443a092
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102592"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge de Project Server 2010

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Project Server 2010 atteindra la fin de la prise en charge le **13 avril 2021**. Cette date a été étendue à partir de la date de fin de prise en charge précédente du 13 octobre 2020. Si vous utilisez actuellement Project Server 2010, Notez que les autres produits associés ont les dates de fin de prise en charge suivantes :
  
|**Produit**|**Fin de la date de prise en charge**|
|:-----|:-----|
|Project 2010 standard <br/> |13 octobre 2020  <br/> |
|Project 2010 professionnel  <br/> |13 octobre 2020  <br/> |

   
Pour plus d’informations sur les serveurs Office 2010 qui arrivent à la fin de la prise en charge, consultez la rubrique [Upgrade from Office 2010 Servers and client Products](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

Project Server, comme presque tous les produits Microsoft, a un cycle de vie de la prise en charge au cours duquel nous fournissons de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans après la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit. Lorsque Project Server 2010 atteint sa fin d’assistance le 13 avril 2021, Microsoft ne fournit plus les éléments suivants :
  
- Support technique pour les problèmes susceptibles de se produire.
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Project Server 2010 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées ci-dessus, nous vous recommandons vivement de procéder à une migration à partir de Project Server 2010 dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Si vous utilisez Project Server 2010, vous devez explorer vos options de migration, qui sont les suivantes :
  
- Migrer vers Project Online
    
- Migrer vers une version plus récente de Project Server (de préférence Project Server 2019).

Voici les deux chemins que vous pouvez suivre pour éviter la fin de la prise en charge de Project Server 2010.

![Chemins de mise à niveau vers Project Server 2010](./media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

    


|**Pourquoi choisir de migrer vers Project Server 2019 ?**|**Pourquoi choisir de migrer vers Project Online ?**|
|:-----|:-----|
|Les règles d’entreprise m’empêchent de faire fonctionner mon entreprise dans le Cloud.  <br/>  J’ai besoin de contrôler les mises à jour de mon environnement.  <br/> | J’ai des utilisateurs mobiles ou distants.  <br/>  Les coûts de migration des serveurs locaux constituent une préoccupation majeure (matériel, logiciel, heures et efforts à mettre en œuvre, etc.).  <br/>  Après la migration, les coûts de maintenance de mon environnement sont importants (par exemple, mises à jour automatiques, temps de fonctionnement garanti, etc.).  <br/>  |

   
> [!NOTE]
> Pour plus d’informations sur les options de navigation à partir de vos serveurs Office 2010, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Notez que Project Server ne prend pas en charge une configuration hybride, car Project Server et Project Online ne peuvent pas partager la même liste de ressources. 

### <a name="what-are-my-options-for-project-client"></a>Quelles sont les options de mon client Project ?
Si vous utilisez Project Professionnel 2010 ou Project standard 2010 et que vous souhaitez explorer vos options de migration, vous avez le choix entre :
- Passer à une version plus récente de Project Professionnel ou de Project standard.
- Passage à une solution en ligne telle que Project Online ou Project pour le Web.
 
#### <a name="moving-to-a-newer-version-of-project-client"></a>Passage à une version plus récente du client Project

Si vous effectuez une migration à partir de Project standard 2010, vous pouvez migrer vers une version plus récente de Project standard (Project standard 2016 ou Project standard 2019).  Nous vous recommandons de passer à la version la plus récente afin de tirer parti des fonctionnalités et fonctionnalités les plus récentes. Par ailleurs, la migration vers une version moins récente (Project standard 2016) signifie que vous devrez migrer à partir de cette version plus tôt car sa fin de prise en charge arrivera à son terme.

De même, si vous effectuez une migration à partir de Project Professionnel 2010, vous pouvez choisir de migrer vers une version plus récente (Project Professionnel 2019 ou Project Professionnel 2016). Nous vous recommandons de passer à la version la plus récente, si possible.  Si vous utilisez Project professionnel pour vous connecter à Project Server, assurez-vous d’effectuer la migration vers une version de Project Professionnel prise en charge pour la connexion à la version de Project Server que vous utilisez.

Project Professionnel 2010 les utilisateurs peuvent également choisir de migrer vers le client de bureau Project online. Il s’agit d’une version basée sur les abonnements de Project Professional 2019, qui est incluse dans les abonnements de plan de projet 3 et de plan de projet 5. 

#### <a name="moving-to-an-online-solution"></a>Passage à une solution en ligne

Vous pouvez également choisir de migrer de Project Professionnel 2010 ou Project standard 2010 vers les solutions en ligne basées sur les abonnements d’un projet. Project Plan 3 et plan 5 incluent Project Online et la dernière offre Cloud, [Project pour le Web](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Les deux proposent un certain nombre de nouvelles fonctionnalités et de nombreux avantages qui méritent d’être explorés.

Pour plus d’informations sur les fonctionnalités incluses dans les deux, ainsi que sur les licences de plan de projet dans lesquelles elles sont incluses, voir la [Description du service Microsoft Project](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description).



  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Éléments importants à prendre en compte lors de la planification de la migration à partir de Project Server 2010

Vous devez tenir compte des éléments suivants lors de la planification de la migration à partir de Project Server 2010 :
  
- **Obtenir de l’aide auprès d’un fournisseur de solutions Microsoft** : la mise à niveau à partir de Project Server 2010 peut s’avérer difficile et nécessite une préparation et une planification très nombreuses. Cela peut s’avérer particulièrement complexe si vous n’étiez pas le seul à configurer et configuré à l’origine Project Server 2010. Heureusement, il existe des fournisseurs de solutions Microsoft que vous pouvez utiliser pour effectuer ces actions pour une vie, que vous envisagez de migrer vers Project Server 2019 ou Project online. Vous pouvez rechercher un fournisseur de solutions Microsoft pour vous aider dans votre migration sur le [Centre de fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). 
    
- **Planifiez vos personnalisations** -sachez que la plupart des personnalisations que vous travaillez dans votre environnement project Server 2010 risquent de ne pas fonctionner lors de la migration vers project Server 2019 ou Project online. Il existe des différences importantes en matière d’architecture Project Server entre les versions, ainsi que les systèmes d’exploitation, les serveurs de bases de données et les navigateurs Web clients requis qui sont pris en charge pour fonctionner avec la version la plus récente. Préparez-vous à tester ou à recréer vos personnalisations selon vos besoins dans votre nouvel environnement. La planification de votre mise à niveau permettra également de vérifier si une personnalisation spécifique est réellement nécessaire lorsque vous avancez. [Créer un plan pour les personnalisations actuelles lors de la mise à niveau vers SharePoint 2013]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013) dispose de certaines informations générales sur l’évaluation et la planification de vos personnalisations actuelles lors de la mise à niveau. 
    
- **Temps et patience** : la planification, l’exécution et le test de la mise à niveau prennent un peu de temps et de travail, en particulier si vous effectuez une mise à niveau vers Project Server 2019. Par exemple, si vous effectuez une migration de Project Server 2010 vers Project Server 2019, vous devez d’abord effectuer une migration de Project Server 2010 vers Project Server 2013, puis vérifier vos données, puis effectuer la même opération lorsque vous effectuez une migration vers chaque version successive (vers Project Server 2016, puis vers Project Server 2019). Vous pouvez vérifier auprès d’un fournisseur de solutions Microsoft Comment comparer vos coûts estimés avec leurs estimations de la durée nécessaire à leur exécution et à quel coût. 
    
## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2010 vers Project Online, vous pouvez effectuer les opérations suivantes pour migrer manuellement vos données de plan de projet :
  
1. Enregistrez vos plans de projet à partir de Project Server 2010 vers. Format MPP.
    
2. À l’aide de Project Professionnel 2016, Project Professional 2019 ou le client de bureau Project Online, ouvrez chaque fichier. mpp, puis enregistrez-le et publiez-le dans Project online.
    
Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréer des champs personnalisés ou des calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également vous en aider.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Comment configurer et utiliser Project online.  <br/> |
|[Description du service Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informations sur les différents plans Project Online disponibles.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Bien que nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en migrant vers Project Online, nous comprenons également que certaines organisations doivent conserver les données de projet dans un environnement local. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2010 vers Project Server 2013, Project Server 2016 ou Project Server 2019.
  
Nous vous recommandons de migrer vers Project Server 2019 si vous ne pouvez pas effectuer une migration vers Project online. Project Server 2019 inclut la plupart des fonctionnalités et des améliorations incluses dans les versions précédentes de Project Server, et correspond le mieux à l’expérience disponible avec Project Online (même si certaines fonctionnalités sont disponibles uniquement dans Project Online).
  
Une fois toutes les migrations terminées, vérifiez vos données pour vous assurer qu’elles ont été correctement migrées.
  
> [!NOTE]
> Si vous envisagez de migrer uniquement vers Project Server 2013 si vous êtes limité à une solution locale, il est important de noter qu’il n’en a que quelques années supplémentaires. La date de fin de prise en charge de Project Server 2013 avec Service Pack 2 est 10/13/2023. Pour plus d’informations sur les dates de fin de prise en charge, consultez la rubrique [stratégie de cycle de vie des produits Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Comment migrer vers Project Server 2019 ?

Les différences d’architecture entre Project Server 2010 et Project Server 2019 empêchent un chemin de migration direct. Cela signifie que vous devrez migrer vos données Project Server 2010 vers la version suivante de Project Server jusqu’à ce que vous procédiez à la mise à niveau vers Project Server 2019.
  
Vous devrez effectuer les étapes suivantes pour mettre à niveau Project Server 2010 vers Project Server 2019 :
  
1. Migrer vers Project Server 2013.
    
2. Migrer de Project serve 2013 vers Project Server 2016.
    
3. Migrer de Project Server 2016 vers Project Server 2019.
    
Une fois toutes les migrations terminées, vérifiez vos données pour vous assurer qu’elles ont été correctement migrées.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Étape 1 : migrer vers Project Server 2013

La première étape de la migration de vos données Project Server 2010 vers Project Server 2019 est d’abord migrer vers Project Server 2013. 
  
Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013, consultez la rubrique [Upgrade to Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822). 
  
Ressources clés :
  
|||
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013.  <br/> |
|[Planifier une mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la configuration système requise.  <br/> |
   
Les nouveautés [de la mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) vous indiquent des modifications importantes de la mise à niveau pour cette version : 
  
- Il n’existe pas de mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour la mise à niveau de Project Server 2010 vers Project Server 2013.
    
- Le processus de mise à niveau ne convertit pas uniquement vos données Project Server 2010 vers le format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.
    
- SharePoint Server 2013 et Project Server 2013 ont été remplacés par l’authentification basée sur les revendications à partir de la version précédente. Vous devrez prendre en compte lors de la mise à niveau si vous utilisez l’authentification classique. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).
    
Ressources clés :
  
- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La consolidation de base de données, Project Server 2010 vers 2013 migration en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Étape 2 : migrer vers Project Server 2016

Après avoir effectué une migration vers Project Server 2013 et vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2016.
  
Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016, consultez la rubrique [Upgrade to Project server 2016](https://docs.microsoft.com/Project/upgrade-to-project-server-2016).
  
Ressources clés :
  
|||
|:-----|:-----|
|[Vue d'ensemble du processus de mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.  <br/> |
|[Planifier la mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2013 vers Project Server 2016.  <br/> |
   
Les [éléments que vous devez connaître à propos de la mise à niveau de Project Server 2016](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) vous indiquent des modifications importantes pour la mise à niveau vers cette version, notamment : 
  
- Lorsque vous créez votre environnement Project Server 2016 vers lequel vous allez migrer vos données Project Server 2013, Notez que les fichiers d’installation de Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, consultez la rubrique [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Les plans de ressources sont déconseillés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers les engagements de ressources dans Project Server 2016 et dans Project online. Pour plus d’informations, voir [vue d’ensemble : engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Étape 3 : migrer vers Project Server 2019

Après avoir effectué une migration vers Project Server 2016 et vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2019.
  
Pour une compréhension complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2016 vers Project Server 2019, consultez la rubrique [Upgrade to Project server 2019](https://docs.microsoft.com/Project/upgrade-to-project-server-2016).
  
Ressources clés :
  
|||
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.  <br/> |
|[Planifier la mise à niveau vers Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Examinez les considérations de planification que vous devez prendre lors de la mise à niveau de Project Server 2016 vers Project Server 2019.  <br/> |
   
Les [éléments que vous devez connaître à propos de la mise à niveau de Project Server 2019](https://go.microsoft.com/fwlink/p/?linkid=841827) vous indiquent des modifications importantes pour la mise à niveau vers cette version, notamment : 
  
- Le processus de mise à niveau consiste à migrer vos données de votre base de données Project Server 2016 vers la base de données de contenu SharePoint Server 2019.  Project Server 2019 ne créera plus sa propre base de données Project Server dans la batterie de serveurs SharePoint Server.

- Après la mise à niveau, vous devez tenir compte de plusieurs modifications apportées dans Project Web App.  Pour obtenir une description de ces éléments, voir [what’s New in Project Server 2019](https://docs.microsoft.com/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

  
Autres ressources :
  
- [Descriptions du service Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): voir les fonctionnalités de gestion de portefeuille incluses dans project Server 2016 et Project Online Premium.
    
- [Guide de migration de Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](./downloads/Office2010Windows7EndOfSupport.pdf).

[![Image de l’affiche de la fin de la prise en charge pour les clients et serveurs Office 2010 et Windows 7](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](./downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche d’une page est un moyen rapide pour connaître les différents chemins que vous pouvez prendre pour empêcher les produits client et serveur Office 2010 et Windows 7 d’arriver à la fin de la prise en charge, avec les chemins d’accès et la prise en charge des options préférés dans Microsoft 365 Entreprise mis en surbrillance.

Vous pouvez également [télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).
   
## <a name="related-topics"></a>Voir aussi

[Mise à jour à jour de SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Mettre à niveau des serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md)
  

