---
title: Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2017
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
description: 'Résumé : Découvrez les posters informatique qui décrivent les modèles d’architecturales, déploiement et options de plateforme pour SharePoint, Exchange, Skype pour les entreprises et Lync.'
ms.openlocfilehash: 79831116df486e1a0ae87c07c01070a5ecd1c4b0
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync

 **Résumé :** Obtenez les affiches informatiques qui décrivent les modèles d’architecturales, déploiement et options de plateforme pour SharePoint, Exchange, Skype pour les entreprises et Lync.
  
Ces affiches décrivent les modèles architecturaux et les options de déploiement de SharePoint, Exchange, Skype Entreprise et Lync, et fournissent des informations de conception pour le déploiement de SharePoint dans Microsoft Azure.
  
Avec Office 365, vous pouvez fournir les services de collaboration et de communication que vos utilisateurs connaissent comme un service en nuage. À quelques exceptions près, l’expérience utilisateur reste la même si vous gérer un déploiement sur site ou à l’aide d’Office 365. Cette expérience utilisateur unifiée simplifie la moins à décider de l’emplacement de chaque charge de travail et soulève des questions telles que :
  
- Comment déterminer l’option de plateforme à utiliser pour les charges de travail individuelles ?
    
- Est-il judicieux de conserver tous les services en local ?
    
- Dans quel scénario un déploiement hybride est-il approprié ?
    
- Comment Microsoft Azure ne tient pas dans l’image ?
    
- Quelles sont les configurations prises en charge pour les charges de travail d’Office Server dans Azure ?
    
> [!TIP]
> La plupart des affiches sur cette page sont disponibles dans plusieurs langues, notamment en chinois, anglais, français, allemand, italien, japonais, coréen, portugais, russe et espagnol. Pour télécharger une affiche dans l'une de ces langues, cliquez sur le lien **Plus de langues** correspondant à cette affiche.
  
Faites-nous savoir ce que vous en pensez ! Envoyez-nous des courriers électroniques à l’adresse [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Cette page renvoie aux affiches suivantes :
  
- **Architecture les affiches modèles** Vous pouvez utiliser les ressources suivantes pour déterminer votre solution idéale et la configuration de SharePoint 2016 et Skype pour Business 2015.
    
  - [Modèles d’architecture Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Aperçu de multi-Geo pour OneDrive dans Office 365](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [Bases de données SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Skype de Microsoft pour les modèles architecturaux Business 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Affiches options de plateforme** Vous pouvez utiliser les ressources suivantes pour déterminer votre solution idéale et la configuration de SharePoint 2013, Exchange 2013 et Lync 2013.
    
  - [Options de plateforme SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Options de plateforme Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Options de plateforme Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 dans les affiches solutions Azure** Vous pouvez utiliser ces affiches informatiques pour déterminer la conception et configuration pour des charges de travail SharePoint Server 2013 dans les services d’infrastructure Azure.
    
  - [Sites Internet dans Microsoft Azure à l’aide de SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Récupération d’urgence SharePoint Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Affiches des modèles architecturaux

Ces nouvelles affiches de systèmes informatiques pour SharePoint 2016 et Skype Entreprise 2015 permettent de comparer les différentes méthodes de déploiement dans un format facile à imprimer. Chaque affiche fournit une liste de toutes les configurations ou options de plateforme disponibles et vous donne les informations suivantes pour chaque option :
  
- **Vue d’ensemble** Un récapitulatif de la plateforme, notamment un diagramme conceptuel.
    
- **Recommandé pour** Scénarios courants qui sont parfaitement adaptées à la plateforme particulière.
    
- **Conditions de licence** Les licences que vous avez besoin pour le déploiement.
    
- **Tâches de l’architecture** Les décisions que vous devez apporter un architecte.
    
- **Professionnels de l’informatique des tâches ou des responsabilités** Les responsabilités quotidiennes votre personnel informatique doit planifier.
    
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Modèles architecturaux Microsoft SharePoint 2016
<a name="SP2016_ArchModel"> </a>

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature de l’affiche de modèles d’architecture SharePoint 2016](images/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | Cette affiche décrit les configurations locales SharePoint Online, Microsoft Azure et SharePoint que les décideurs et les concepteurs de solutions dans les entreprises doivent connaître. <br/><br/> - **SharePoint Online (SaaS)** - SharePoint de consommer via un logiciel en tant que Service (SaaS) abonnement modèle. <br/> - **Environnement hybride SharePoint** - déplacer vos sites SharePoint et les applications dans le nuage à votre rythme. <br/> - **SharePoint dans Azure (IaaS)** - étendre votre environnement local dans Microsoft Azure et de déployer des serveurs SharePoint Server 2016 il. (Il est recommandé pour les environnements de développement/test et de haute disponibilité/récupération d’urgence).<br/> - **SharePoint local** - vous planifier, déployer, gérer et personnaliser votre environnement SharePoint dans un centre de données que vous gérez. <br/> |
   
### <a name="multi-geo-preview-for-onedrive-in-office-365"></a>Aperçu de multi-Geo pour OneDrive dans Office 365
<a name="MultiGeoO365ODB"> </a>

|**Élément**|**Description**|
|:-----|:-----|
|[![Multi-Geo OneDrive dans le modèle d’Office 365](images/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.vsdx) <br/> | Ce poster présente une page de OneDrive Multi-localisés dans Office 365, qui est actuellement en mode Aperçu. Ce modèle inclut :<br/><br/> -Avantages <br/> -Étapes de déploiement <br/> -Un exemple de configuration <br/><br/>  Pour plus d’informations sur l’aperçu Multi-Geo pour OneDrive dans Office 365, cliquez [ici](https://aka.ms/onedrivemultigeo).  <br/> |
   
### <a name="sharepoint-server-2016-databases"></a>Bases de données SharePoint Server 2016
<a name="SP2016_Databases"> </a>

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature de l’affiche de bases de données SharePoint Server 2016](images/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | Cette affiche informatique est un guide de référence rapide pour les bases de données SharePoint Server 2016. Chaque base de données comporte les informations suivantes :<br/><br/> -Taille <br/> -Conseils mise à l’échelle <br/> -Modèles e/s <br/> -Configuration requise <br/><br/>  La première page contient les bases de données système SharePoint et les applications de service ayant plusieurs bases de données. La deuxième page affiche toutes les applications de service dont les bases de données uniques.<br/><br/>  Pour plus d’informations sur les bases de données SharePoint Server 2016, voir [Database types and descriptions dans SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc678868%28v=office.16%29.aspx) <br/> |
   
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modèles architecturaux Microsoft Skype Entreprise 2015
<a name="SfB2015_ArchModel"> </a>

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature de la Skype pour affiches modèles architecturaux d’entreprise](images/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |Ce poster décrit la Skype pour Business en ligne, sur site, hybride, en nuage PBX et l’intégration avec les configurations Exchange et SharePoint que les décideurs et les architectes de solutions doivent savoir à propos de. <br/><br/> Elle est destinée à l’audience professionnels de l’informatique pour sensibiliser les différents modèles d’architecturales fondamentales à travers lequel pouvant être consommés Skype pour Business Online et Skype pour les entreprises dans les locaux. <br/><br/>Démarrer avec la configuration meilleures adaptée aux besoins de votre organisation et les plans futurs. Prendre en compte et utilisez d’autres selon vos besoins. Par exemple, vous pouvez souhaiter prendre en compte l’intégration à Exchange et SharePoint ou une solution qui tire parti de l’offre de Microsoft Cloud PBX.  <br/> |
   
## <a name="platform-options-posters"></a>Affiches des options de plateforme

Ces affiches pour SharePoint 2013, Exchange  2013 et Lync 2013 permettent de comparer les différentes méthodes de déploiement en un clin d’œil et en grand format. Chaque affiche fournit une liste de toutes les configurations ou options de plateforme disponibles et vous donne les informations suivantes pour chaque option :
  
- **Vue d’ensemble** Un récapitulatif de la plateforme, notamment un diagramme conceptuel.
    
- **Recommandé pour** Scénarios courants qui sont parfaitement adaptées à la plateforme particulière.
    
- **Conditions de licence** Les licences que vous avez besoin pour le déploiement.
    
- **Tâches de l’architecture** Les décisions que vous devez apporter un architecte.
    
- **Professionnels de l’informatique des tâches ou des responsabilités** Les responsabilités quotidiennes votre personnel informatique doit planifier.
    
## <a name="sharepoint-2013-platform-options"></a>Options de plateforme SharePoint 2013
<a name="SP2013_Options"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des Options de plateforme SharePoint 2013](images/SP_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |Pour les architectes et les décideurs d’entreprise (BDM), ce modèle illustre les options de plateforme pour SharePoint 2013, SharePoint dans Office 365, hybrides locaux avec Office 365, Azure et les déploiements uniquement sur site. Il inclut une vue d’ensemble de chaque architecture, recommandations, conditions de licence et listes de tâches professionnels de l’informatique pour chaque plateforme et d’architecte. Plusieurs solutions SharePoint sur Azure sont mis en surbrillance.<br/><br/>Pour une version texte accessible de cette affiche, voir [diagramme Accessible : Options de plateforme Microsoft SharePoint 2013](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md).  <br/> |
   
## <a name="exchange-2013-platform-options"></a>Options de plateforme Exchange 2013
<a name="Exch2013_options"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des Options de plateforme Exchange](images/ITPro_Other_Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Aux décideurs et aux architectes, ce modèle décrit les options de plateforme disponible pour Exchange 2013. Les clients peuvent choisir Exchange Online avec Office 365, Exchange hybride, Exchange Server sur site et Exchange hébergé. L’affiche inclut les détails de chaque option architecturale, y compris les scénarios plus idéales pour chacun, les conditions de licence et les responsabilités professionnels de l’informatique.<br/><br/>Pour une version texte accessible de cette affiche, voir [diagramme Accessible : Options de plateforme Microsoft Exchange 2013](accessible-diagrammicrosoft-exchange-2013-platform-options.md).  <br/> |
   
## <a name="lync-2013-platform-options"></a>Options de plateforme Lync 2013
<a name="Lync2013_Options"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Miniature des Options de plateforme Lync](images/Lync_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |Pour les décideurs d’entreprise (BDM) et les architectes, ce modèle décrit les options de plateforme disponibles pour Lync 2013. Les clients peuvent choisir entre Lync Online avec Office 365, Lync hybride, Lync Server local et Lync hébergé. L’affiche inclut les détails de chaque option d’architecture, y compris les scénarios idéaux pour chacune, les exigences de licence et les responsabilités des professionnels de l’informatique.  <br/> |
   
## <a name="sharepoint-in-azure-solutions-posters"></a>Affiches des solutions SharePoint dans Azure
<a name="Lync2013_Options"> </a>

Ces affiches informatiques indiquent des solutions basées sur Azure à l’aide de SharePoint Server 2013 dans un format affiche de grandes.
  
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sites Internet dans Microsoft Azure utilisant SharePoint Server 2013
<a name="Azure_sharepoint2013"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Image de sites Internet dans Azure utilisant SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |Ce poster présente les activités de conception clé et recommandé des choix d’architecture pour les sites pour Internet dans Azure. Pour une version texte accessible de cette affiche, voir [diagramme Accessible - sites Internet dans Microsoft Azure pour SharePoint 2013](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md).<br/><br/> Pour plus d'informations, voir les articles suivants :  <br/><br/> - [Sites Internet dans Microsoft Azure à l’aide de SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013
<a name="DesignSampleInternetSites"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Image de l’exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |Utilisez ce modèle de conception comme point de départ pour votre propre site accessible sur Internet de l’architecture dans Azure à l’aide de SharePoint Server 2013. Pour obtenir une version texte accessible de cette affiche, voir [diagramme Accessible : exemple de conception : sites Internet dans Microsoft Azure pour SharePoint 2013](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md).<br/><br/> Pour plus d'informations, voir les articles suivants :  <br/><br/> - [Sites Internet dans Microsoft Azure à l’aide de SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Récupération d’urgence SharePoint vers Microsoft Azure
<a name="sharepoint_recovery_Azure"> </a>

****

|**Élément**|**Description**|
|:-----|:-----|
|[![Processus de récupération d’urgence de SharePoint pour Azure](images/SP_DR_Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> ![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| ![Affichage d’une page contenant des versions dans d’autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |Ce poster informatique illustre les principes d’architecture pour un environnement de récupération d’urgence dans Azure. Pour une version texte accessible de cette affiche, voir [diagramme Accessible : récupération d’urgence SharePoint Microsoft Azure](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md).<br/><br/> Pour plus d'informations, voir les articles suivants :  <br/><br/> - [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architectures Microsoft Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>Voir aussi

<a name="Lync2013_Options"> </a>

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Solutions hybrides](hybrid-solutions.md)




