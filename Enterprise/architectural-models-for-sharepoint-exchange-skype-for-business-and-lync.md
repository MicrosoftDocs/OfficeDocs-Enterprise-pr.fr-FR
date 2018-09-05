---
title: Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: 'Résumé : Obtenez les affiches IT qui décrivent les modèles architecturaux, le déploiement et les options de plateforme de SharePoint, Exchange, Skype Entreprise et Lync.'
ms.openlocfilehash: 0965a4389ef61c981e30aeec8dd3b3dcff90d20e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915539"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync

 **Résumé :** Obtenez les affiches qui décrivent les modèles d’architecte, le déploiement et les options de plateforme de SharePoint, Exchange, Skype Entreprise et Lync.
  
Ces affiches décrivent les modèles architecturaux et les options de déploiement de SharePoint, Exchange, Skype Entreprise et Lync, et fournissent des informations de conception pour le déploiement de SharePoint dans Microsoft Azure.
  
Avec Office 365, vous pouvez fournir aux utilisateurs les services de collaboration et de communication qu’ils connaissent sous forme de services cloud. À quelques exceptions près, l’expérience utilisateur reste la même, que vous gériez un déploiement en local ou que vous utilisiez Office 365. Cette expérience utilisateur unifiée complique quelque peu le choix d’emplacement de chaque charge de travail et soulève des questions telles que :
  
- Comment déterminer l’option de plateforme à utiliser pour les charges de travail individuelles ?
    
- Est-il judicieux de conserver tous les services en local ?
    
- Dans quel scénario un déploiement hybride est-il approprié ?
    
- Comment Microsoft Azure s’intègre-t-il ?
    
- Quelles sont les configurations prises en charge pour les charges de travail d’Office Server dans Azure ?
    
> [!TIP]
> La plupart des affiches sur cette page sont disponibles dans plusieurs langues, notamment en chinois, anglais, français, allemand, italien, japonais, coréen, portugais, russe et espagnol. Pour télécharger une affiche dans l’une de ces langues, cliquez sur le lien **Plus de langues** correspondant à cette affiche.
  
Faites-nous savoir ce que vous en pensez ! Écrivez-nous à l’adresse [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Cette page renvoie aux affiches suivantes :
  
- **Affiches de modèles architecturaux** Vous pouvez utiliser ces ressources pour déterminer votre plate-forme et votre configuration idéales pour SharePoint 2016 et Skype Entreprise 2015.
    
  - [Modèles architecturaux Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Fonctionnalités Multi-Géo dans OneDrive et SharePoint Online dans Office 365](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [Bases de données SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modèles architecturaux Microsoft Skype Entreprise 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Affiches des options de plateforme** Vous pouvez utiliser ces ressources pour déterminer votre plate-forme et votre configuration idéales pour SharePoint 2013, Exchange 2013 et Lync 2013.
    
  - [Options de plateforme SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Options de plateforme Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Options de plateforme Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Affiches des solutions SharePoint Server 2013 dans Azure** Vous pouvez utiliser ces affiches pour déterminer la conception et la configuration des charges de travail SharePoint Server 2013 dans les services d’infrastructure Azure.
    
  - [Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Récupération d’urgence SharePoint vers Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Affiches des modèles architecturaux

Ces nouvelles affiches de systèmes informatiques pour SharePoint 2016 et Skype Entreprise 2015 permettent de comparer les différentes méthodes de déploiement dans un format facile à imprimer. Chaque affiche fournit une liste de toutes les configurations ou options de plateforme disponibles et vous donne les informations suivantes pour chaque option :
  
- **Vue d’ensemble** Bref résumé de la plateforme, accompagné d’un diagramme conceptuel.
    
- **Recommandé pour** les scénarios courants qui conviennent à la plateforme en particulier.
    
- **Licences nécessaires** Licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture** Décisions que vous devez prendre en tant qu’architecte.
    
- **Responsabilités ou tâches des professionnels de l’informatique** Les responsabilités quotidiennes que votre personnel informatique doit planifier.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Modèles architecturaux Microsoft SharePoint 2016

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature pour l’affiche des modèles architecturaux SharePoint 2016](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | Cette affiche décrit les configurations locales SharePoint Online, Microsoft Azure et SharePoint que les décideurs et les concepteurs de solutions dans les entreprises doivent connaître. <br/><br/> - **SharePoint Online (SaaS)**: vous utilisez SharePoint via un modèle d’abonnement Software as a Service (SaaS). <br/> - **SharePoint Hybride** : vous déplacez vos sites et applications SharePoint dans le cloud à votre rythme. <br/> - **SharePoint dans Azure (IaaS)**  : vous étendez votre environnement local dans Microsoft Azure et vous déployez les serveurs SharePoint 2016 à cet emplacement (recommandé pour les environnements de test/développement et de haute disponibilité/récupération d’urgence).<br/> - **SharePoint en local** : vous planifiez, déployez, gérez et personnalisez votre environnement SharePoint dans un centre de données que vous gérez. <br/> |
   
<a name="MultiGeoO365ODB"> </a>
### <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>Fonctionnalités Multi-Géo dans OneDrive et SharePoint Online dans Office 365

|**Élément**|**Description**|
|:-----|:-----|
|[![Modèle OneDrive multigéographique dans Office 365](media/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.pdf)  \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.vsdx) <br/> | Ce poster constitue une vue d’ensemble d’une page de fonctionnalités géo multiple dans OneDrive et SharePoint Online dans Office 365. Ce modèle inclut : <br/><br/> - Avantages <br/> - Étapes de déploiement <br/> - Un exemple de configuration <br/><br/>  Pour plus d’informations sur les fonctionnalités de géo multiple dans OneDrive et SharePoint Online dans Office 365, cliquez [ici](https://aka.ms/onedrivemultigeo).  <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>Bases de données SharePoint Server 2016

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature de l’affiche bases de données SharePoint Server 2016](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | Cette affiche informatique est un guide de référence rapide pour les bases de données SharePoint Server 2016. Chaque base de données comporte les informations suivantes : <br/><br/> -Taille <br/> - Conseils mise à l’échelle <br/> - Modèles d’E/S <br/> - Conditions requises : <br/><br/>  La première page contient les bases de données système SharePoint et les applications de service ayant plusieurs bases de données. La deuxième page affiche toutes les applications de service ayant des bases de données uniques. <br/><br/>  Pour plus d'informations sur les bases de données SharePoint Server 2016, voir [Types et descriptions des bases de données dans SharePoint Server 2016](https://technet.microsoft.com/fr-FR/library/cc678868%28v=office.16%29.aspx) <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modèles architecturaux Microsoft Skype Entreprise 2015

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature pour l’affiche des modèles architecturaux Skype Entreprise](media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |Cette affiche décrit les configurations Skype Entreprise Online locales, hybrides, PBX cloud et d’intégration avec Exchange et SharePoint que les décideurs et les concepteurs de solutions dans les entreprises doivent connaître. <br/><br/> Cette série d’affiches est destinée aux professionnels de l’informatique pour mieux leur faire connaître les différents modèles architecturaux fondamentaux par le biais desquels Skype Entreprise Online et Skype Entreprise en local peuvent être utilisés. <br/><br/>Commencez par définir quelle configuration correspond aux futurs plans et besoins de votre organisation. Envisagez et utilisez d’autres selon vos besoins. Par exemple, vous souhaiterez peut-être prendre en considération l’intégration avec Exchange et SharePoint ou une solution basée sur une offre PBX Microsoft Cloud.  <br/> |
   
## <a name="platform-options-posters"></a>Affiches des options de plateforme

Ces affiches pour SharePoint 2013, Exchange  2013 et Lync 2013 permettent de comparer les différentes méthodes de déploiement en un clin d’œil et en grand format. Chaque affiche fournit une liste de toutes les configurations ou options de plateforme disponibles et vous donne les informations suivantes pour chaque option :
  
- **Vue d’ensemble** Bref résumé de la plateforme, accompagné d’un diagramme conceptuel.
    
- **Recommandé pour** les scénarios courants qui conviennent à la plateforme en particulier.
    
- **Licences nécessaires** Licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture** Décisions que vous devez prendre en tant qu’architecte.
    
- **Responsabilités ou tâches des professionnels de l’informatique** Les responsabilités quotidiennes que votre personnel informatique doit planifier.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>Options de plateforme SharePoint 2013

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des options de la plateforme SharePoint 2013](media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |Pour les décideurs d’entreprise et les architectes, ce modèle décrit les options de plateforme pour SharePoint 2013 : SharePoint dans Office 365, environnement hybride sur site avec Office 365, Windows Azure et déploiements sur site uniquement. Il présente une vue d’ensemble de chaque architecture, des recommandations, les exigences de licence, et répertorie les tâches des architectes et des professionnels de l’informatique pour chaque plateforme. Plusieurs solutions SharePoint sur Windows Azure sont mises en avant.<br/><br/>Pour une version texte de ce poster, voir [diagramme accessible : Options de la plateforme Microsoft SharePoint 2013](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md).  <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Options de plateforme Exchange 2013

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des options de plateforme Exchange](media/ITPro-Other-Exchange2013PlatformOptions.jpg)   ](https://www.microsoft.com/download/details.aspx?id=42676)  <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Pour les décideurs d’entreprise (BDM) et les architectes, ce modèle décrit les options de plateforme disponibles pour Exchange 2013. Les clients peuvent choisir entre Exchange Online avec Office 365, Exchange hybride, Exchange Server local et Exchange hébergé. L’affiche inclut les détails de chaque option d’architecture, y compris les scénarios idéaux pour chacune, les exigences de licence et les responsabilités des professionnels de l’informatique.<br/><br/>Pour une version texte de ce poster, voir [diagramme accessible : Options de la plateforme Microsoft Exchange 2013](accessible-diagrammicrosoft-exchange-2013-platform-options.md).  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Options de plateforme Lync 2013

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des options de plateforme Lync](media/Lync-PlatformOptions.jpg)   ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |Pour les décideurs d’entreprise (BDM) et les architectes, ce modèle décrit les options de plateforme disponibles pour Lync 2013. Les clients peuvent choisir entre Lync Online avec Office 365, Lync hybride, Lync Server local et Lync hébergé. L’affiche inclut les détails de chaque option d’architecture, y compris les scénarios idéaux pour chacune, les exigences de licence et les responsabilités des professionnels de l’informatique.  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Affiches des solutions SharePoint dans Azure

Ces affiches présentent les solutions Azure utilisant SharePoint Server 2013 en grand format.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sites Internet dans Microsoft Azure utilisant SharePoint Server 2013

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Image de sites Internet dans Azure utilisant SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |Cette affiche décrit les activités de conception clés et les choix d’architecture recommandés pour les sites accessibles sur Internet dans Azure. Pour une version texte accessible de cette affiche, voir [diagramme accessible : sites internet dans Microsoft Azure pour SharePoint 2013](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md). <br/><br/> Pour plus d’informations, voir les articles suivants :  <br/><br/> - [Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Image d’exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |Utilisez cet exemple de conception comme point de départ pour l’architecture de votre propre site accessible sur Internet dans Azure à l’aide de SharePoint Server 2013. Pour une version texte accessible de cette affiche, voir [ diagramme accessible : Design sample: Internet sites in Microsoft Azure for SharePoint 2013](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md).  <br/><br/> Pour plus d’informations, voir les articles suivants :  <br/><br/> - [Sites Internet dans Microsoft Azure qui utilisent SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Récupération d’urgence SharePoint vers Microsoft Azure

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Procédure de récupération d’urgence SharePoint vers Azure](media/SP-DR-Azure.png) ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554) \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |Cette affiche illustre les principes d’architecture d’un environnement de récupération d’urgence dans Windows_Azure. Pour une version texte accessible de cette affiche, voir [ diagramme accessible : Récupération d’urgence SharePoint vers Microsoft Azure](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md). <br/><br/> Pour plus d’informations, voir les articles suivants :  <br/><br/> - [Récupération d’urgence SharePoint Server 2013 dans Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="see-also"></a>Voir aussi

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Solutions hybrides](hybrid-solutions.md)

