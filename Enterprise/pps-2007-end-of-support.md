---
title: Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
description: PerformancePoint Server 2007, ProClarity et SharePoint Server 2007 ont atteint la fin de la prise en charge. Lisez cet article pour planifier votre mise à niveau de la solution BI.
ms.openlocfilehash: 03db75b38bfaa32df20eafb8ede745e403bc964f
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "26617877"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007

Les applications et les serveurs office 2007 ont atteint leur fin de prise en charge, y compris les serveurs et les applications que vous pouvez utiliser dans le cadre de vos solutions business intelligence (BI). Le tableau suivant répertorie les applications d’aide à la décision qui sont affectées :
  
|**Applications d’aide à la décision Microsoft**|**Fin de la prise en charge de la date**|
|:-----|:-----|
|Analytique proClarity Server 6.3 Service Pack 3  <br/> Professionnel bureau proClarity 6.3  <br/> Visionneuse SharePoint proClarity 6.3  <br/> |11 juillet 2017  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |10 octobre 2017  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |9 janvier 2018  <br/> |
   
Pour plus d’informations, voir les [ressources pour vous aider à mettre à niveau à partir d’Office 2007 de serveurs et de clients](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Quel ne prend fin moyenne de la prise en charge ?

Produits Microsoft, tels que PerformancePoint Server 2007 SP3, logiciel ProClarity et SharePoint Server 2007 SP3 a rencontré un cycle de vie de prise en charge au cours de laquelle Microsoft propose les nouvelles fonctionnalités, les correctifs et mises à jour de sécurité. Le cycle de vie d’un produit dure généralement dix ans à compter de la date de publication initiale du produit, et la fin de ce cycle de vie est appelée fin du produit de prise en charge. Comme ProClarity, PerformancePoint Server et SharePoint Server 2007 ont atteint leur fin du support, Microsoft ne fournira plus :
  
- Support technique pour les problèmes qui peuvent se produire
    
- Bogue résout les problèmes qui ont été identifiés et qui peut avoir un impact sur la stabilité et la facilité d’utilisation des serveurs
    
- Correctifs de sécurité pour les vulnérabilités qui sont découverts, et qui peut rendre les serveurs ou applications vulnérables aux failles de sécurité
    
- Mises à jour de fuseau horaire
    
Votre installation de PerformancePoint Server 2007 SP3, SharePoint Server 2007 SP3 et ProClarity continuera à s’exécuter même si la prise en charge s’est terminée. Toutefois, il est vivement recommandé que vous migrez de ces applications dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Avec ces applications d’aide à la décision a atteint la fin de la prise en charge, il s’agit d’un moment idéal pour découvrir les différentes options et la préparation d’un plan de mise à niveau. Il y a beaucoup de modifications apportées aux applications Microsoft BI depuis 2007 et que vous disposez de plusieurs options à prendre en compte, comme indiqué dans le tableau suivant :
  
|**Si vous utilisez ceci...**|**Explorez ces options...**|**Et n’oubliez pas ceci...**|
|:-----|:-----|:-----|
| Analyse de PerformancePoint Server 2007 &amp; fonctionnalités Analytique, y compris :  <br/><br/>  PerformancePoint Monitoring Server  <br/><br/>  PerformancePoint Dashboard Designer  <br/><br/>  Dashboard Viewer pour SharePoint Services (utilisé pour le rendu des tableaux de bord PerformancePoint, des cartes de performance et des rapports)  <br/> |**Excel avec Excel Online** (dans le nuage ou sur site). Pour une vue d’ensemble, voir [fonctionnalités d’aide à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **Power BI** (dans le nuage ou sur site). Pour une vue d’ensemble, voir [What ' s Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (local). Pour une vue d’ensemble, consultez [SQL Server Reporting Services (SSRS) : créer, déployer et gérer les rapports mobiles et paginés](https://go.microsoft.com/fwlink/?linkid=841342) <br/><br/> **PerformancePoint Services** (local). Pour une vue d’ensemble, voir [Nouveautés de PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343) <br/> |Excel et Excel Online sont disponibles sous la forme en ligne (en nuage) ou solutions sur site. Nombreux besoins en matière de création de rapports et de tableau de bord peuvent être satisfaits avec les fonctionnalités d’Excel avec Excel en ligne.  <br/><br/> Power BI est disponible en tant qu’une ligne ou une solution sur site. Power BI n’est pas inclus dans Office 365, mais vous pouvez commencer à l’aide de Power BI gratuitement, puis, en fonction de votre utilisation de données et une petite entreprise a besoin, mise à niveau vers Power BI Pro. <br/> <br/> Reporting Services et PerformancePoint Services sont locaux solutions.  <br/><br/> PerformancePoint Services est disponible dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016. <br/> <br/> Certains types de rapports qui étaient disponibles dans PerformancePoint Server 2007 et certaines fonctionnalités ne sont pas disponibles dans Excel, Power BI, Reporting Services ou PerformancePoint Services. Vous souhaiterez passer en revue les fonctionnalités disponibles pour déterminer la meilleure solution pour les besoins de votre entreprise.  <br/> |
| Logiciel proClarity, y compris : <br/> <br/>  ProClarity professionnel du bureau  <br/> <br/> ProClarity Analytics Server  <br/> <br/> Visionneuse SharePoint proClarity  <br/> |**Travail avec un partenaire Microsoft** pour identifier une solution qui le mieux à vos besoins. Visitez le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) <br/><br/> Vous pouvez également tenir compte à l’aide d’Excel avec Excel Online, Power BI, SQL Server Reporting Services ou PerformancePoint Services.  <br/> |Plusieurs, mais pas tous, fonctions et fonctionnalités qui étaient disponibles dans le logiciel ProClarity sont disponibles dans les autres offres Microsoft, y compris Excel, Power BI, Reporting Services et PerformancePoint Services.  <br/> |
|SharePoint Server 2007 indicateurs de performance clés (également appelées indicateurs de performance clés MOSS)  <br/> |**Excel avec Excel Services** (Excel Services est désormais appelé Excel Online). Pour une vue d’ensemble, reportez-vous à [la décision dans Excel et Excel Services (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |Indicateurs de performance clés MOSS qui ont été créés à l’aide de SharePoint Server 2007 peuvent être utilisés dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016 ; Toutefois, les nouveaux indicateurs de performance clés MOSS ne peut pas être créé.  <br/> |
|Excel 2007  <br/> |**Excel avec Excel Online** (dans le nuage ou sur site). Pour une vue d’ensemble, voir [fonctionnalités d’aide à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **Power BI** (dans le nuage ou sur site). Pour une vue d’ensemble, voir [What ' s Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Les deux Excel avec Excel Online et Power BI offrent à votre organisation en nuage et les solutions locales, avec prise en charge pour un large éventail de sources de données.  <br/> |
   
### <a name="what-if-i-need-help-selecting-a-solution"></a>Que se passe-t-il si j’ai besoin d’aide sélection d’une solution ?

Avec BI choix disponible, il peut sembler extrêmement pour déterminer quelle option est préférable. Nous disposons d’un guide en ligne disponible pour vous aider. Consultez [choix Microsoft Business Intelligence (BI) des outils d’analyse et de création de rapports](https://go.microsoft.com/fwlink/?linkid=839877).
  
### <a name="what-happens-if-i-dont-upgrade-now"></a>Que se passe-t-il si je ne pas mettre à niveau maintenant ?

Vous pouvez choisir de ne pas mettre à niveau pour l’instant. Vos applications et serveurs existants continueront à s’exécuter. Toutefois, vous ne recevrez des mises à jour plus - y compris les mises à jour de sécurité - fin de la prise en charge. Et, en cas de problème avec les applications de votre serveur, vous ne pourrez pas obtenir de l’aide du support technique Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>Comment planifier la mise à niveau de mon ?

Une fois que vous avez exploré vos options de mise à niveau, l’étape suivante consiste à préparer un plan de mise à niveau. Les sections suivantes contiennent des informations et des liens vers des ressources supplémentaires pour vous aider à planifier votre solution. Lorsqu’il s’agit d’applications Microsoft BI, vous disposez de quatre options principales, y compris les deux qui fonctionnent à la fois dans le nuage ou sur site et deux qui sont des solutions sur site-uniquement :
  
|**Option**|**Dans le nuage ou sur site ?**|
|:-----|:-----|
|[Excel avec Excel Online](#use-excel-with-excel-online-in-the-cloud-or-on-premises) <br/> |Les deux  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises) <br/> |Les deux  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |Local uniquement  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |Local uniquement  <br/> |
   
### <a name="use-excel-with-excel-online-in-the-cloud-or-on-premises"></a>Utiliser Excel avec Excel en ligne (dans le nuage ou sur site)

Avec Excel Online, également appelé Excel Services dans SharePoint Server — personnes peuvent afficher et utiliser les classeurs dans une fenêtre de navigateur, même si Excel n’est pas installé sur leur ordinateur. Vous pouvez utiliser Excel pour créer des rapports, des cartes de performance et des tableaux de bord et puis partager vos classeurs avec d’autres personnes à l’aide de Excel Online, si vous utilisez SharePoint Online dans le cadre d’Office 365 ou SharePoint Server locaux. Et, vous pouvez utiliser des données stockées localement ou dans le nuage, qui vous donne la possibilité d’utiliser une grande variété de sources de données.
  
Le tableau suivant compare les principaux avantages de l’utilisation d’Excel avec Office 365 à l’aide d’Excel dans SharePoint Server, avec des informations supplémentaires ci-dessous.
  
|**[Excel avec Office 365 (en nuage)](#excel-with-office-365-in-the-cloud)**|**[Excel avec SharePoint Server (on-premises)](#excel-with-sharepoint-server-on-premises)**|
|:-----|:-----|
|**Vous obtenez la version le plus récent, en plus de Microsoft Excel**. Avec Office 365, vous obtenez la dernière version d’Excel, qui inclut puissante, nouveaux types de graphiques, la capacité à créer des graphiques et des tableaux rapidement et facilement et prise en charge de plusieurs sources de données.<br/> <br/> **Le programme d’installation est beaucoup plus simple**. Excel Online étant inclus avec Office 365 pour les entreprises, il n’existe aucun composant essentiel de votre part. S’inscrire et se connecter, et vous pouvez en cours d’exécution plus rapide et plus efficace que la mise à niveau de vos serveurs sur site.<br/> <br/> **Personnes ont partout accès à leurs classeurs**. Personnes verront en toute sécurité les classeurs de partout où ils sont à l’aide de leur ordinateur, Smartphone et tablette.<br/> <br/> **Il est plus**! Voir les [fonctionnalités d’aide à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/> |**Vous gérez vos paramètres globaux**. En tant qu’un administrateur SharePoint, vous pouvez spécifier les paramètres globaux, tels que la sécurité, l’équilibrage de charge, gestion de session, la mise en cache du classeur et les connexions de données externes.<br/> <br/> **Vous pouvez utiliser Excel Services avec PerformancePoint Services**. Vous pouvez configurer Excel Services et PerformancePoint Services dans le cadre de votre installation de SharePoint Server et inclure des rapports Excel Services dans vos tableaux de bord PerformancePoint.<br/> <br/> **Il est plus**! Reportez-vous à [la décision dans Excel et Excel Services (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-office-365-in-the-cloud"></a>Excel avec Office 365 (en nuage)

Si vous déplacez vers Office 365, vous devez aussi les services et applications, y compris 2016 Excel et Excel Online plus récents. PerformancePoint Services n’est pas disponible dans Office 365, afin que vous allez remplacer votre tableau de bord PerformancePoint avec les classeurs Excel ou d’autres rapports. La bonne nouvelle est que Excel 2016 a beaucoup de nouveaux types de graphiques et de création de tableaux de bord impressionnant dans Excel est plus facile que jamais. Et nouvelles fonctionnalités sont régulièrement ajoutées. Pour plus d’informations, consultez la rubrique [What ' s New in 2016 Excel pour Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx).
  
Et, lorsque vous achetez au moins 50 sièges d’Office 365, l’équipe Microsoft FastTrack peut vous aider à mettre en place. Pour plus d’informations, visitez le site [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365/office-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel avec SharePoint Server (on-premises)

Si vous mettez à niveau vers une version plus récente de SharePoint, vous pouvez utiliser Excel avec Excel Services ou Excel Online, comme suit :
  
- Excel Services dans SharePoint Server 2010
    
- Administrer Excel Services dans SharePoint Server 2013
    
- Excel Online, qui fait partie d’Office Online Server, installé séparément à partir de SharePoint Server 2016
    
Vous pouvez configurer PerformancePoint Services dans votre nouvelle version de SharePoint Server et l’utiliser avec Excel Services ou Excel en ligne.
  
Pour en savoir que plus sur SharePoint options de mise à niveau, voir [SharePoint Server 2007 fin de prendre en charge la feuille de route](sharepoint-2007-end-of-support.md).
  
Pour plus d’informations sur Excel Services, voir [présentation d’Excel Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841362).
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Utilisez Power BI (dans le nuage ou sur site)

Power BI est une suite d’outils d’analytique business pour analyser les données et de partager des idées. Avec Power BI, vous pouvez créer des tableaux de bord à l’aide locale ou sources de données en ligne et des rapports interactifs. Personnes peuvent afficher et utiliser des rapports et des tableaux de bord à l’aide de leurs ordinateurs ou les appareils mobiles.
  
Power BI n’est pas inclus dans Office 365 ou SharePoint Server, mais un distinct offre qui inclut le service Power BI, passerelles Power BI et Power BI bureau. Power BI s’intègre également à SharePoint Online. Vous pouvez commencer à Power BI gratuitement et en fonction de vos données d’utilisation et des besoins de, mise à niveau vers Power BI Pro. Pour plus d’informations, voir [What ' s Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>Utiliser Reporting Services (local)

SQL Server Reporting Services fournit une solution de création de rapports robuste, ainsi que la possibilité d’installer et configurer Reporting Services en mode natif ou en mode intégré SharePoint. Vous pouvez créer des rapports à l’aide de plusieurs outils, y compris le Concepteur de rapports et le Générateur de rapports Power View. Avec la dernière version de SQL Server, vous pouvez également utiliser SQL Server Mobile rapport Publisher pour proposer des rapports de l’échelle à n’importe quelle taille d’écran, en donnant à votre organisation la possibilité d’utiliser des rapports sur leurs appareils mobiles. Pour plus d’informations, voir [SQL Server Reporting Services (SSRS) : créer, déployer et gérer les rapports mobiles et paginés](https://go.microsoft.com/fwlink/?linkid=841342).
  
### <a name="use-performancepoint-services-on-premises"></a>Utiliser PerformancePoint Services (local)

Comme vous le savez, PerformancePoint Server 2007 a été acheté séparément à partir de SharePoint Server 2007. À partir de SharePoint Server 2010, PerformancePoint Services est une application de service dans SharePoint Server. Cela signifie que vous n’avez pas d’achat de licences serveur distinct ou matériel afin de pouvoir pour utiliser PerformancePoint Services.
  
Pour déplacer de PerformancePoint Server 2007 vers PerformancePoint Services, vous déplacez vers une version plus récente du serveur SharePoint et configurez PerformancePoint Services. La version du serveur SharePoint que vous souhaitez déplacer vers déterminera si vous pouvez importer le contenu du tableau de bord existant à partir de PerformancePoint Server 2007 vers PerformancePoint Services.
  
- Si vous mettez à niveau vers SharePoint Server 2010, vous pouvez importer le contenu de votre tableau de bord PerformancePoint à partir de PerformancePoint Server 2007 vers PerformancePoint Services dans SharePoint Server 2010. Pour plus d’informations sur cette procédure, voir [Assistant importation : contenu PerformancePoint Server 2007 vers SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=838873).
    
- Si vous déplacez vers SharePoint Server 2013 ou SharePoint Server 2016, vous devrez probablement créer un contenu de tableau de bord (sources de données, des rapports, des cartes de performance et des pages de tableau de bord).
    
Pour démarrer votre plan de mise à niveau de PerformancePoint Services, voir les ressources suivantes :
  
1. [Fin de SharePoint Server 2007 de prise en charge de feuille de route](sharepoint-2007-end-of-support.md)
    
2. Lorsque vous savez quelle version de SharePoint que vous souhaitez déplacer vers, voir l’article correspondante pour PerformancePoint Services :
    
  - [Planifier PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841363)
    
  - [Vue d’ensemble de PerformancePoint Services dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=841551)
    
  - [Vue d’ensemble de PerformancePoint Services dans SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=874704)
    
Lorsque vous mettez à niveau vers PerformancePoint Services, vous apprécierez plusieurs nouvelles fonctionnalités et améliorations. PerformancePoint Services offre des cartes de performance améliorées, nouvelles visualisations, telles que l’arbre de décomposition et rapport de détails des indicateurs de performance clés et plusieurs types de graphiques, meilleures fonctionnalités de filtrage Time Intelligence et conformité amélioration de l’accessibilité. Pour plus d’informations, voir [What ' s new for PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343).
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>Où puis-je obtenir aide avec mon mise à niveau ?

Que vous soyez mise à niveau locale ou déplacement vers Office 365, il est recommandé de collaborer avec un partenaire Microsoft. Un partenaire complet peut vous aider à identifier la solution qui répond le mieux à vos besoins professionnels et les aider avec votre déploiement. Visitez le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249)et utiliser les filtres de recherche pour trouver un fournisseur de solution.
  
## <a name="related-topics"></a>Voir aussi

[Ressources pour vous aider à mettre à niveau à partir d’Office 2007 de serveurs et de clients](upgrade-from-office-2007-servers-and-products.md)
  
[Groupe de retraite Office (Communauté Microsoft Tech)](https://go.microsoft.com/fwlink/?linkid=842065)


  

