---
title: Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007
ms.author: deniseb
author: denisebmsft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
description: PerformancePoint Server 2007, ProClarity et SharePoint Server 2007 ont atteint la fin de la prise en charge. Lisez cet article pour planifier la mise à niveau de votre solution décisionnel.
ms.openlocfilehash: 517d420eff35cde2862d7879e3b5557cbe6087ca
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746247"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007

*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 entreprise.*

Les applications et les serveurs Office 2007 ont atteint leur fin de prise en charge, y compris les serveurs et les applications que vous pouvez utiliser dans le cadre de vos solutions d’aide à la décision. Le tableau suivant répertorie les applications BI qui sont affectées :
  
|**Applications Microsoft BI**|**Date de fin de prise en charge**|
|:-----|:-----|
|ProClarity Analytics Server 6,3 Service Pack 3  <br/> ProClarity Desktop professionnel 6,3  <br/> Visionneuse SharePoint de ProClarity 6,3  <br/> |11 juillet 2017  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |10 octobre 2017  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |9 janvier 2018  <br/> |
   
Pour plus d’informations, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la fin de la prise en charge ?

Les produits Microsoft, tels que PerformancePoint Server 2007 SP3, le logiciel de ProClarity et SharePoint Server 2007 SP3, ont tous bénéficié d’un cycle de vie de la prise en charge au cours duquel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Le cycle de vie d’un produit dure généralement 10 ans à compter de la date de publication initiale du produit, et la fin de ce cycle de vie est connue sous le nom de la fin du support du produit. Lorsque ProClarity, PerformancePoint Server et SharePoint Server 2007 ont atteint leur fin de prise en charge, Microsoft ne fournit plus :
  
- Support technique pour les problèmes pouvant se produire
    
- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation des serveurs
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre les serveurs ou les applications vulnérables aux failles de sécurité
    
- Mises à jour de fuseau horaire
    
Votre installation de ProClarity, de SharePoint Server 2007 SP3 et de PerformancePoint Server 2007 SP3 continuera de s’exécuter même si le support technique est terminé. Toutefois, nous vous recommandons vivement de migrer à partir de ces applications dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Ces applications DÉCISIONNELles atteignant la fin de la prise en charge, il s’agit d’un excellent moment pour explorer vos options et préparer un plan de mise à niveau. De nombreuses modifications ont été apportées aux applications Microsoft BI depuis 2007, et vous avez plusieurs options à prendre en compte, comme résumé dans le tableau suivant :
  
|**Si vous utilisez ce...**|**Explorez ces options...**|**Et gardez cela à l’esprit...**|
|:-----|:-----|:-----|
| Fonctionnalités d’analyse de &amp; PerformancePoint Server 2007, notamment :  <br/><br/>  PerformancePoint Monitoring Server  <br/><br/>  PerformancePoint Dashboard Designer  <br/><br/>  Dashboard Viewer for SharePoint Services (utilisé pour le rendu des tableaux de bord, des cartes de performance et des rapports PerformancePoint)  <br/> |**Excel avec Excel dans un navigateur** (dans le Cloud ou sur site). Pour obtenir une vue d’ensemble, consultez les fonctionnalités d’aide [à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **Power bi** (dans le Cloud ou en local). Pour obtenir une vue d’ensemble, voir [qu’est-ce que Power bi ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (en local). Pour obtenir une vue d’ensemble, reportez-vous à [SQL Server Reporting Services (SSRS) : créer, déployer et gérer des rapports mobiles et paginés](https://go.microsoft.com/fwlink/?linkid=841342) <br/><br/> **PerformancePoint Services** (en local). Pour obtenir une vue d’ensemble, voir [what’s New for PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343) <br/> |Excel est disponible sous forme de solution en ligne (en nuage) ou sur site. De nombreux besoins en matière de création de rapports et de tableaux de bord peuvent être satisfaits avec les fonctionnalités d’Excel.  <br/><br/> Power BI est disponible sous forme de solution en ligne ou sur site. Power BI n’est pas inclus dans Office 365, mais vous pouvez commencer à utiliser Power BI gratuitement, puis, en fonction de vos données et des besoins de votre entreprise, effectuez la mise à niveau vers Power BI Pro. <br/> <br/> Reporting Services et PerformancePoint Services sont tous deux des solutions locales.  <br/><br/> PerformancePoint Services est disponible dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016. <br/> <br/> Certaines fonctionnalités et certains types de rapports disponibles dans PerformancePoint Server 2007 ne sont pas disponibles dans Excel, Power BI, Reporting Services ou PerformancePoint Services. Vous pouvez passer en revue les fonctionnalités disponibles afin de déterminer la meilleure solution pour vos besoins professionnels.  <br/> |
| Logiciel de ProClarity, y compris : <br/> <br/>  ProClarity Desktop Professional  <br/> <br/> ProClarity Analytics Server  <br/> <br/> Visionneuse SharePoint ProClarity  <br/> |**Collaborez avec un partenaire Microsoft** pour identifier une solution qui répond le mieux à vos besoins. Visiter le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) <br/><br/> Vous pouvez également envisager d’utiliser Excel avec Excel dans un navigateur, Power BI, SQL Server Reporting Services ou PerformancePoint Services.  <br/> |Plusieurs fonctionnalités et fonctionnalités disponibles dans le logiciel de ProClarity sont disponibles dans d’autres offres Microsoft, notamment Excel, Power BI, Reporting Services et PerformancePoint Services.  <br/> |
|Indicateurs de performance clés SharePoint Server 2007 (également appelés indicateurs de performance clés MOSS)  <br/> |**Excel avec Excel Services**. Pour obtenir une vue d’ensemble, consultez l’aide à la décision [dans Excel et Excel Services (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |Les indicateurs de performance clés MOSS créés à l’aide de SharePoint Server 2007 peuvent être utilisés dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016 ; Toutefois, il n’est pas possible de créer de nouveaux indicateurs de performance clés MOSS.  <br/> |
|Excel 2007  <br/> |**Excel** (dans le Cloud ou sur site). Pour obtenir une vue d’ensemble, consultez les fonctionnalités d’aide [à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **Power bi** (dans le Cloud ou en local). Pour obtenir une vue d’ensemble, voir [qu’est-ce que Power bi ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Excel et Power BI offrent à votre organisation des solutions en nuage et sur site, avec la prise en charge d’une grande variété de sources de données.  <br/> |
   
### <a name="what-if-i-need-help-selecting-a-solution"></a>Qu’en est-il si j’ai besoin d’aide pour sélectionner une solution ?

Avec autant de choix de BI disponibles, il peut sembler surchargé de déterminer l’option la plus appropriée. Un guide en ligne est disponible pour vous aider. Consultez la rubrique [choix des outils d’aide à la décision Microsoft pour l’analyse et la création de rapports](https://go.microsoft.com/fwlink/?linkid=839877).
  
### <a name="what-happens-if-i-dont-upgrade-now"></a>Que se passe-t-il si je n’effectue pas de mise à niveau ?

Vous pouvez choisir de ne pas effectuer la mise à niveau pour le moment. Vos serveurs et applications existants continueront à s’exécuter. Toutefois, vous ne recevrez pas d’autres mises à jour, y compris les mises à jour de sécurité, après la fin de la prise en charge. En cas de problème avec vos applications serveur, vous ne serez pas en mesure d’obtenir de l’aide auprès du support technique de Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>Comment puis-je planifier ma mise à niveau ?

Une fois que vous avez exploré vos options de mise à niveau, l’étape suivante consiste à préparer un plan de mise à niveau. Les sections suivantes contiennent des informations et des liens vers des ressources supplémentaires pour vous aider à planifier votre solution. En ce qui concerne les applications BI de Microsoft, vous disposez de quatre options principales, y compris celles qui fonctionnent à la fois dans le Cloud ou sur site, et dans les deux solutions locales uniquement :
  
|**Option**|**Dans le Cloud ou sur site ?**|
|:-----|:-----|
|[Excel](#excel-with-sharepoint-server-on-premises) <br/> |Les deux  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or on-premises) <br/> |Les deux  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |Local uniquement  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |Local uniquement  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Utiliser Excel (dans le Cloud ou sur site)

Avec Excel, également appelé Excel Services dans SharePoint Server, les utilisateurs peuvent afficher et utiliser des classeurs dans une fenêtre de navigateur, même si Excel n’est pas installé sur leur ordinateur. Vous pouvez utiliser Excel pour créer des rapports, des cartes de performance et des tableaux de bord, puis partager vos classeurs avec d’autres personnes à l’aide d’Excel dans un navigateur, que vous utilisiez SharePoint Online dans le cadre d’Office 365 ou SharePoint Server en local. De plus, vous pouvez utiliser des données stockées sur site ou dans le Cloud, ce qui vous permet d’utiliser une large variété de sources de données.
  
Le tableau suivant compare les principaux avantages de l’utilisation d’Excel avec Office 365 à l’aide d’Excel avec SharePoint Server, avec des informations supplémentaires ci-dessous.
  
|**[Excel avec Office 365 (dans le Cloud)](#excel-with-office-365-in-the-cloud)**|**[Excel avec SharePoint Server (en local)](#excel-with-sharepoint-server-on-premises)**|
|:-----|:-----|
|**Vous obtenez la dernière version d’Excel**. Avec Office 365, vous disposez de la dernière version d’Excel, qui inclut de nouveaux types de graphiques puissants, la possibilité de créer des graphiques et des tableaux rapidement et facilement, et de prendre en charge davantage de sources de données. <br/> <br/> La **configuration est plus simple**. Excel étant inclus dans Office 365 pour les entreprises, il n’y a pas de levage important sur votre composant. Inscrivez-vous et connectez-vous, et vous serez opérationnel plus rapidement et plus efficacement que la mise à niveau de vos serveurs locaux. <br/> <br/> **Les utilisateurs ont accès à leur classeur partout**. Les utilisateurs peuvent afficher les classeurs en toute sécurité, où qu’ils soient, à l’aide de leur ordinateur, de leur téléphone intelligent et de leur tablette. <br/> <br/> **Il y a plus**! Voir [fonctionnalités d’aide à la décision dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/> |**Vous pouvez gérer vos paramètres globaux**. En tant qu’administrateur SharePoint, vous pouvez spécifier des paramètres globaux, tels que la sécurité, l’équilibrage de charge, la gestion de session, la mise en cache de classeurs et les connexions de données externes. <br/> <br/> **Vous pouvez utiliser Excel Services avec PerformancePoint Services**. Vous pouvez configurer Excel Services et PerformancePoint Services dans le cadre de votre installation SharePoint Server, et inclure des rapports Excel Services dans vos tableaux de bord PerformancePoint. <br/> <br/> **Il y a plus**! Voir aide à la décision [dans Excel et Excel Services (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-office-365-in-the-cloud"></a>Excel avec Office 365 (dans le Cloud)

Si vous passez à Office 365, vous disposez des services et applications les plus à jour, y compris Excel 2016. PerformancePoint Services n’est pas disponible dans Office 365, c’est pourquoi vous allez remplacer le contenu de votre tableau de bord PerformancePoint par des classeurs Excel ou d’autres rapports. La bonne nouvelle est que Excel 2016 comporte beaucoup de nouveaux types de graphiques et que la création d’un tableau de bord dans Excel est plus facile que jamais. De plus, de nouvelles fonctionnalités sont ajoutées régulièrement. Pour en savoir plus, consultez [la rubrique What’s New in Excel 2016 for Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx).
  
Lorsque vous achetez 50 sièges ou plus d’Office 365, l’équipe FastTrack de Microsoft peut vous aider à configurer. Pour en savoir plus, visitez le site [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365/office-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel avec SharePoint Server (en local)

Si vous effectuez une mise à niveau vers une version plus récente de SharePoint, vous pouvez utiliser Excel avec Excel Services ou dans un navigateur, comme suit :
  
- Excel Services dans SharePoint Server 2010
    
- Excel Services dans SharePoint Server 2013
    
- Excel, qui fait partie d’Office Online Server, installé séparément de SharePoint Server 2016
    
Vous pouvez également configurer PerformancePoint Services dans votre nouvelle version de SharePoint Server et l’utiliser conjointement avec Excel.
  
Pour en savoir plus sur les options de mise à niveau de SharePoint, voir la feuille [de route de prise en charge de SharePoint Server 2007](sharepoint-2007-end-of-support.md).
  
Pour en savoir plus sur Excel Services, reportez-vous à la rubrique [Excel Services Overview (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841362).
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Utiliser Power BI (dans le Cloud ou en local)

Power BI est une suite d’outils d’analyse commerciale permettant d’analyser les données et de partager des informations. Avec Power BI, vous pouvez créer des rapports et des tableaux de bord interactifs à l’aide de sources de données locales ou en ligne. Les utilisateurs peuvent afficher et utiliser vos rapports et tableaux de bord à l’aide de leur ordinateur ou de leurs appareils mobiles.
  
Power BI n’est pas inclus dans Office 365 ou SharePoint Server, mais il s’agit d’une offre distincte qui inclut Power BI Desktop, Power BI Gateways et le service Power BI. Power BI s’intègre également à SharePoint Online. Vous pouvez commencer à utiliser Power BI gratuitement et en fonction de vos besoins en matière d’utilisation des données et d’entreprise, mettre à niveau vers Power BI Pro. Pour en savoir plus, consultez la rubrique [qu’est-ce que Power bi ?](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>Utiliser Reporting Services (en local)

SQL Server Reporting Services offre une solution de création de rapports robuste, ainsi que la possibilité d’installer et de configurer Reporting Services en mode natif ou en mode intégré SharePoint. Vous pouvez créer des rapports à l’aide de plusieurs outils, dont le concepteur de rapports, le générateur de rapports et Power View. Avec la dernière version de SQL Server, vous pouvez également utiliser l’éditeur de rapports SQL Server Mobile pour livrer des rapports qui s’ajustent à n’importe quelle taille d’écran, ce qui permet à votre organisation de consommer des rapports sur leurs appareils mobiles. Pour plus d’informations, reportez-vous à [SQL Server Reporting Services (SSRS) : créer, déployer et gérer des rapports mobiles et paginés](https://go.microsoft.com/fwlink/?linkid=841342).
  
### <a name="use-performancepoint-services-on-premises"></a>Utiliser PerformancePoint Services (en local)

Comme vous le sachiez, PerformancePoint Server 2007 a été acheté séparément de SharePoint Server 2007. À partir de SharePoint Server 2010, PerformancePoint Services est une application de service dans SharePoint Server. Cela signifie que vous n’avez pas besoin d’acheter des licences serveur ou du matériel séparé afin d’utiliser PerformancePoint Services.
  
Pour passer de PerformancePoint Server 2007 à PerformancePoint Services, vous devez passer à une version plus récente de SharePoint Server et configurer PerformancePoint Services. La version de SharePoint Server vers laquelle vous effectuez le transfert détermine si vous pouvez importer votre contenu de tableau de bord existant à partir de PerformancePoint Server 2007 vers PerformancePoint Services.
  
- Si vous effectuez une mise à niveau vers SharePoint Server 2010, vous pouvez importer le contenu de votre tableau de bord PerformancePoint à partir de PerformancePoint Server 2007 vers PerformancePoint Services dans SharePoint Server 2010. Pour en savoir plus sur le fonctionnement, reportez-vous à l' [Assistant importation : contenu PerformancePoint server 2007 vers SharePoint server 2010](https://go.microsoft.com/fwlink/?linkid=838873).
    
- Si vous passez à SharePoint Server 2013 ou à SharePoint Server 2016, vous aurez probablement besoin de créer du contenu de tableau de bord (sources de données, rapports, cartes de performance et pages de tableau de bord).
    
Pour commencer à utiliser votre plan de mise à niveau de PerformancePoint Services, consultez les ressources suivantes :
  
1. [Feuille de route de prise en charge de SharePoint Server 2007](sharepoint-2007-end-of-support.md)
    
2. Lorsque vous savez quelle version de SharePoint vous déplacez, consultez l’article correspondant pour PerformancePoint Services :
    
  - [Planifier PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841363)
    
  - [Vue d’ensemble de PerformancePoint Services dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=841551)
    
  - [Vue d’ensemble de PerformancePoint Services dans SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=874704)
    
Lorsque vous effectuez une mise à niveau vers PerformancePoint Services, vous bénéficierez de nouvelles fonctionnalités et d’améliorations. PerformancePoint Services offre des cartes de performance améliorées, de nouvelles visualisations, telles que l’arborescence hiérarchique, un rapport détaillé des indicateurs de performance clés, ainsi que d’autres types de graphiques, des capacités de filtrage de l’intelligence temporelle et une meilleure conformité de l’accessibilité. Pour plus d’informations, reportez-vous à [la rubrique what’s New for PerformancePoint Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343).
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>Où puis-je obtenir de l’aide sur ma mise à niveau ?

Qu’il s’agisse d’une mise à niveau locale ou d’une migration vers Office 365, nous vous recommandons de travailler avec un partenaire Microsoft. Un partenaire qualifié peut vous aider à identifier la solution qui répond le mieux aux besoins de votre entreprise et à vous aider dans votre déploiement. Visitez le [Centre partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249)et utilisez les filtres de recherche pour trouver un fournisseur de solutions.
  
## <a name="related-topics"></a>Sujets associés

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Groupe de retraite Office (Communauté Microsoft Tech)](https://go.microsoft.com/fwlink/?linkid=842065)


  

