---
title: Options de migration SharePoint 2007 à prendre en compte
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
description: SharePoint Server 2007 a atteint la fin de la prise en charge et il est temps de procéder à la mise à niveau. Utilisez cet article pour vous aider à créer votre plan.
ms.openlocfilehash: e319438e2d760c391414f699de5967738d8c6b81
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774989"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Options de migration SharePoint 2007 à prendre en compte

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Microsoft SharePoint 2007 et SharePoint Server 2007 ont atteint la fin de la prise en charge. Il est temps de mettre à niveau ! Cet article fournit des informations sur vos options de migration.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Stratégies de mise à niveau courantes pour SharePoint

Il existe plusieurs méthodes pour mettre à niveau un environnement SharePoint Server. Si vous avez une batterie de serveurs Microsoft Office SharePoint Server 2007, voici quelques exemples de méthodes de mise à niveau :
  
- liaison des bases de données.
    
- Mise à niveau côte à côte
    
- Mise à niveau sur place
    
- Mise à niveau hybride (sur place avec bases de données détachées/attachement de base de données séparée)
    
- Hybrides SharePoint (connexion en ligne à SharePoint sur site)
    
- Déplacer manuellement des données entre des collections de sites ou des bibliothèques
    
- Mise à niveau de l’Assistant FastTrack vers Microsoft 365 ([Gestionnaire de déploiement SharePoint Online](https://aka.ms/spoguidance))
    
- API de migration vers SharePoint Online (SPO) dans Microsoft 365
    
Qu’est-ce qui vous convient le mieux ?
  
La connaissance de ce que fait votre batterie de serveurs et est utilisée pour est une force tactique lorsqu’il s’agit d’une mise à niveau. La manière dont les personnes utilisent la batterie de serveurs SharePoint vous aidera à choisir parmi vos options.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 comporte également une mise à niveau progressive non abordée ici. Pour voir une liste d’articles relatifs à la mise à niveau, reportez-vous à la [fin de la feuille de route de SharePoint Server 2007](sharepoint-2007-end-of-support.md). 
  
N’oubliez pas de vérifier le [cycle de vie du produit](https://support.microsoft.com/lifecycle/search) et la configuration système requise pour la version de SharePoint vers laquelle vous effectuez la mise à niveau. Cela vous permettra de savoir quand la mise à niveau suivante sera nécessaire (par exemple, si vous vous placez sur un produit hérité comme SharePoint Server 2010 pour planifier des mises à niveau, assurez-vous de connaître la fin de la date de prise en charge) et vous assurer que votre matériel prend en charge votre plan. 
  
Si vous envisagez de passer une partie ou la totalité de vos sites SharePoint à Microsoft 365 dans le Cloud, il s’agit d’une heure pour marquer un lien vers les [descriptions de service microsoft 365 et Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library). Vous aurez besoin des descriptions de service pour en savoir plus sur les fonctionnalités de SharePoint Online et la façon dont elles peuvent différer de SharePoint Server sur site. Mettez à niveau les batteries de serveurs Microsoft Office SharePoint Server 2007 opérationnelles. Si votre installation comporte des sites qui sont rompus, corrigez-les avant la mise à niveau.
  
## <a name="a-note-about-managing-risk"></a>Remarque sur la gestion des risques

Les méthodes comme « côte à côte » sont importantes dans le schéma de logique de mise à niveau. Lorsque vous effectuez une mise à niveau côte à côte, vous conservez votre batterie de serveurs Microsoft Office SharePoint Server 2007, mais vous créez une batterie de serveurs avec la version suivante (SharePoint Server 2010) sur le nouveau matériel. Cela vous permet de trois façons :
  
1. Vous disposez d’un emplacement pour effectuer des sauvegardes de vos bases de données Microsoft Office SharePoint Server 2007 afin de les mettre à niveau séparément à l’aide de la liaison de base de données.
    
2. Si vous déterminez que seul un petit nombre de bibliothèques de documents critiques et d’autres informations sont en cours d’utilisation sur votre batterie de serveurs Microsoft Office SharePoint Server 2007, vous pouvez choisir de déplacer manuellement des données de Microsoft Office SharePoint Server 2007 vers SharePoint Server 2010, ou de ne prendre que des sites et des sites Web spécifiques à la version suivante (ce qui peut faciliter votre travail).
    
3. Moins vous faites sur la batterie de serveurs Microsoft Office SharePoint Server 2007, directement, plus la sécurité des données que contient la batterie de serveurs est mise à niveau.
    
Les méthodes telles que la mise à niveau sur place agiront directement sur votre batterie de serveurs Microsoft Office SharePoint Server 2007, ce qui vous permet d’abandonner facilement un chemin d’accès et de recommencer avec votre propre environnement. Dans la mesure du possible, créez des mesures de sécurité (telles que la prise et le test des sauvegardes de l’environnement d’origine). Par exemple, si votre batterie de serveurs Microsoft Office SharePoint Server 2007 est virtuelle et qu’elle est dupliquée pour les besoins de la sauvegarde et de la restauration, sauvegardez et restaurez les bases de données les plus récentes avant la fenêtre de votre service pour la mise à niveau. Sachant que vous avez la possibilité de restaurer des sauvegardes de base de données, vous pouvez non seulement vous offrir une solution de secours.
  
> [!TIP]
> Meilleures pratiques il existe des documents pour la mise à niveau pour [Microsoft Office SharePoint server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx), [SharePoint server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)et [SharePoint Server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx). Vous pouvez également rechercher des [partenaires Microsoft](https://partnercenter.microsoft.com/pcv/search) qui ont une expérience de mises à niveau ou de migrations Microsoft 365. 
  
## <a name="make-your-plan"></a>Créer votre plan

Si vous devez effectuer une mise à niveau, vous avez besoin d’un plan, et une seule taille ne convient pas dans ces cas. Votre plan peut être aussi simple que « créer un abonnement Microsoft 365 avec SharePoint Online, inscrire un domaine et rediriger des personnes pour enregistrer leurs fichiers ». Et ce n’est peut-être pas. Cette décision est vous-même et il s’agit de la façon dont vous et vos utilisateurs avez réellement besoin.
  
> [!NOTE]
> Il est risqué de s’exécuter sur un logiciel dont le cycle de vie est terminé. Les produits qui ne sont plus pris en charge ne sont plus patchés lorsque des problèmes sont détectés. Cela signifie également que si de nouvelles menaces de sécurité se produisent, il n’y aura pas de correctifs de sécurité ou de correctifs, car les produits de fin de cycle de vie ne sont plus pris en charge. Veuillez éviter cette situation ! 
  
### <a name="first-know-your-farm"></a>Tout d’abord, vous devez identifier votre batterie de serveurs

Lors de la mise à niveau, votre prise de décision doit être basée sur ce que fait votre batterie de serveurs pour votre organisation. Qu’est-ce qui vous satisfait ? Qu’est-ce que son rôle ? Chaque batterie de serveurs de votre entreprise peut avoir un rôle différent. Certaines de vos batteries de serveurs SharePoint sont *critiques* , d’autres peuvent être des Archives de fichiers. Si votre batterie de serveurs remplit de nombreux rôles à la fois, vous devrez peut-être savoir quelles collections de sites, sites Web ou bibliothèques de documents, toutes les personnalisations et leur importance. L’analyse de vos données à ce niveau peut sembler beaucoup de travail, mais elle permet de maîtriser votre domaine avant de procéder à la mise à niveau ou à la migration. Une fois que vous avez identifié toutes les pièces mobiles et les plus importantes, vous savez également ce que vous êtes en mesure de décroître et vous pouvez laisser derrière. Ces connaissances ne vous permettront d’aller plus loin. 
  
Qu’est-ce que les utilisateurs disent être les plus importants concernant votre batterie de serveurs SharePoint Server ?
  
- Fonctionnalités SharePoint intégrées
    
- Le corpus de données volumineux (tel qu’une archive de fichiers)
    
- Disponibilité
    
- Applications critiques, composants WebPart ou documents de la batterie de serveurs (batterie de serveurs critiques)
    
- Normes de conformité satisfaites
    
- Personnalisations
    
Si vous exécutez une tâche essentielle pour votre entreprise à partir de votre batterie de serveurs SharePoint, disons qu’elle agit comme un grand catalogue de données critiques concernant les exigences de service client, vous pouvez placer un battement à côté des « applications critiques », mais aussi de la « disponibilité », c’est-à-dire que votre entreprise serait affectée si vous n’avez pas pu utiliser SharePoint pendant un certain temps. De même, vous pouvez vérifier les « personnalisations » car les services critiques offerts par votre batterie de serveurs sont basés sur du code personnalisé, des définitions de site ou un certain nombre de personnalisations qui fonctionnent ensemble.
  
Si SharePoint répond à ces besoins sans avoir à faire quoi que ce soit à l’extérieur de l’utilisation de ce qui est intégré au logiciel, et que vous le mettez généralement à jour et que vous procédiez à une administration et une maintenance normales, vous avez peut-être choisi « intégré SharePoint »--cela peut également être dû à une version plus ancienne de SharePoint. En d’autres termes, il fait déjà ce dont il a besoin et vous n’avez pas besoin d’effectuer la mise à niveau jusqu’à présent, à la fin de la prise en charge de Microsoft Office SharePoint Server 2007.
  
Lorsque vous répertoriez ces éléments, vous créez des critères pour votre mise à niveau. En d’autres termes, toute mise à niveau doit répondre à cette barre pour être prise en compte. Cela vous permet d’éliminer les méthodes qui ne répondent pas à vos besoins.
  
### <a name="a-simple-sample-plan"></a>Exemple de plan simple

Il peut s’avérer nécessaire d’avoir un consensus plus large avec la direction et les autres administrateurs sur le chemin que votre mise à niveau SharePoint prendra. Les administrateurs de SharePoint Server collaborent souvent avec des administrateurs Microsoft SQL Server, travaillent avec des équipes de mise en réseau et de sécurité, et plus encore. Lorsqu’il y a beaucoup de parties prenantes, vous devrez peut-être créer un accord pour ou ajuster votre plan de mise à niveau et de migration. Par exemple, si vous migrez des données afin qu’une partie de votre entreprise utilise SharePoint Online dans Microsoft 365, il est probable que vous deviez effectuer un réglage des performances ou des tests au sein de votre réseau. Les équipes affectées doivent être informées à l’avance.
  
Dans mon exemple simple, j’affiche la proposition d’un administrateur SharePoint, puis je répertorie le plan que toutes les parties prenantes ont convenu. Pour plus de clarté, documentez vos accords et décisions.
  
Le plan commence après une analyse approfondie d’une batterie de serveurs et tente d’identifier le rôle de la batterie de serveurs, les points faibles et d’autres informations importantes susceptibles de limiter les options de mise à niveau. Par la suite, une proposition de mise à niveau est effectuée par l’administrateur SharePoint et les parties prenantes s’accordent sur un plan d’action.
  
Ma liste à puces la plus importante :
  
- Disponibilité, fonctionnalités intégrées à SharePoint et normes de conformité.
    
- La plupart des données se trouvent sur trois collections de sites, avec un espace de travail de réunion utilisé par une équipe de développement particulièrement important et en forte utilisation dans plusieurs fuseaux horaires dans le monde entier.
    
- Il existe dix-sept autres sites qui sont largement utilisés.
    
- Deux bibliothèques de documents (espace de travail de réunion et documents sur la collection de sites racine) sont les plus volumineuses (plus de 8000 documents chacun). Nous disposons d’un grand nombre de documents et de listes archivés avec des pièces jointes de feuilles de calcul.
    
- Il existe 14 listes de bibliothèques dont les données sensibles doivent rester en conformité.
    
- Nous devons avoir la possibilité de faire des suspensions et de procéder à la découverte électronique à tout moment.
    
- Certaines de ces données doivent rester en local, en raison des règles InfoSec.
    
 **Mes choix de mise à niveau et de migration :**
  
|||
|:-----|:-----|
|**Oui** <br/> |**Non** <br/> |
|Mettre à niveau les bases de données avec attachement de base de données  <br/> |Mise à niveau sur place  <br/> |
|Mise à niveau avec des batteries de serveurs côte à côte  <br/> |Mise à niveau hybride  <br/> |
|API de migration vers SPO dans Microsoft 365 (pour les données de site personnel)  <br/> |SharePoint hybride (inutile encore)  <br/> |
|Quelques migrations manuelles de données vers SharePoint Online pour les données critiques  <br/> |Mise à niveau de l’Assistant FastTrack vers Microsoft 365  <br/> |
   
 **Mon plan proposé :**
  
Effectuez une mise à niveau sur site, avec des versions de SharePoint côte à côte, certaines virtualisés, afin de pouvoir mettre à niveau les bases de données en premier. Passez de SharePoint 2007 à SharePoint 2010. Les administrateurs et les développeurs testent la batterie de serveurs résultante. Les utilisateurs testent la batterie de serveurs résultante. Corrigez les problèmes d’émission pendant ce temps. De nouveau, côte à côte, mettez à niveau les bases de données SharePoint 2010 vers SharePoint 2013. Test. Test utilisateur/pilote. Corrigez les problèmes d’émission pendant ce temps.
  
- Envisagez si un hybride fédéré de recherche avec SPO répond à vos besoins.
    
- Envisagez [l’assistance FastTrack](https://fasttrack.microsoft.com) si vous souhaitez effectuer une mise à niveau vers SharePoint Online à partir de ici. 
    
- Déterminez si des collections de sites peuvent être déchargées vers un abonnement Microsoft 365. (Microsoft 365 répond à de nombreuses [normes de conformité](https://technet.microsoft.com/library/office-365-compliance.aspx). Microsoft 365 dispose de la fonctionnalité [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) et peut faire des [retenues](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) dans le centre de conformité.) 
    
Dans le cas contraire, passez à une mise à niveau côte à côte vers SharePoint Server 2016.
  
> [!NOTE]
> Entre les recommandations prises par les administrateurs qui planifient la mise à niveau et le processus réel sont les conversations qui se produisent avec les autres parties prenantes sur lesquelles la mise à niveau s’appuie. Par exemple, il arrive que les administrateurs forcent les administrateurs à modifier leurs plans. Quelle que soit la décision finale, vous devez documenter le plan convenu, à l’avenir. Il peut ressembler à ceci : 
  
 **Mon plan d’action :**
  
En local, nous utilisons un environnement virtuel pour créer les versions par défaut de SharePoint Server 2010 et 2013. SharePoint Server 2016 sera basé sur le nouveau matériel qui répond à la configuration système requise pour 2016. Nous allons effectuer des attaches de base de données pour mettre à niveau les bases de données à partir de SharePoint 2007 via toutes les versions entre le service informatique et SharePoint Server 2016. Les personnalisations principales sont actuellement recréées et testées dans l’environnement SharePoint Server 2016 si les fonctionnalités natives ne répondent pas encore à nos besoins. En cas de réussite, nous disposons d’une batterie de serveurs locale sur le nouveau matériel avec des bases de données mises à niveau et moins de personnalisations. Nous allons attacher les bases de données de contenu mises à niveau à de nouvelles collections de sites dans SharePoint Server 2013, tester, tester/tester l’utilisateur, puis effectuer un basculement DNS vers le nouvel environnement 2016 SharePoint Server pour une utilisation en direct.
  
- Nous ne prenons pas en compte les hybrides fédérés entre SharePoint Server 2016 et SharePoint Online dès à présent.
    
- Une estimation de 35% de nos sites peut être transformée en nouveaux sites SPO avec des domaines personnel, ou devenir le stockage OneDrive entreprise. Recherche d’autres opportunités de conversion de sites ou d’acheminement de nouveaux sites vers SPO.
    
- Une partie de cette partie de la migration sera manuelle, par une opération glisser-déplacer sur les sites personnels OneDrive entreprise, et d’autres par l’API de migration.
    
Des étapes plus détaillées, ou un certain nombre de liens vers des instructions de mise à niveau spécifiques doivent suivre un plan. L’ordinateur MOSS 2007 ne doit pas être désactivé et les environnements virtuels doivent être conservés dans un souci de comparaison ; Toutefois, la mise à niveau est effectuée lorsque les utilisateurs sont redirigés vers SharePoint Server 2016.
  
Les facteurs les plus importants dans le choix d’une méthode sont le coût total de la mise à niveau et le coût dans le temps (vous en verrez plus à ce propos dans l’article feuille de route de migration SharePoint). Toutefois, la planification anticipée vous permettra de définir de manière significative les attentes, de choisir judicieusement et d’encadrement de la réussite de l’opération.
  
## <a name="related-links"></a>Liens associés

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Stratégie de cycle de vie de Microsoft et recherche de cycle de vie](https://support.microsoft.com/lifecycle)
  
[Rechercher des partenaires Microsoft qui peuvent vous aider à effectuer une mise à niveau ou une migration](https://partnercenter.microsoft.com/pcv/search)
  

