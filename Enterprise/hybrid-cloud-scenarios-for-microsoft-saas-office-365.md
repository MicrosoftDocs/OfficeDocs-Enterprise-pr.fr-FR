---
title: "Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Résumé : Comprendre les scénarios et l’architecture de hybride pour Microsoft de base SaaS (Office 365) les offres en nuage."
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)

 **Résumé :** Comprendre les scénarios et l’architecture de hybride pour Microsoft de base SaaS (Office 365) les offres en nuage.
  
Combinez des déploiements locaux d’Exchange, de SharePoint ou de Skype Entreprise à leur équivalent dans Office 365 dans le cadre d’une migration cloud ou d’une stratégie d’intégration à long terme.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Architecture de scénario hybride pour les services SaaS Microsoft

La figure 1 présente l’architecture des scénarios hybrides SaaS de Microsoft pour Office 365.
  
**Figure 1 : Scénarios de hybride SaaS Microsoft pour Office 365**

![Scénarios hybrides Microsoft SaaS pour Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
Pour chaque couche de l’architecture :
  
- Applications et scénarios
    
    Il existe plusieurs scénarios hybrides SaaS au niveau des produits serveur Office et de leur équivalent dans Office 365 :
    
  - Exchange Server combiné à Exchange Online (Exchange Server hybride)
    
  - Skype Entreprise Server combiné à Skype Entreprise Online et aux nouveaux scénarios PBX cloud et édition Cloud Connector
    
  - SharePoint Server 2016 ou SharePoint Server 2013 combiné à SharePoint Online (plusieurs scénarios)
    
    Vous pouvez également mettre en place Exchange Online avec Skype Entreprise Server en local (scénario hybride de produit croisé).
    
- Identity
    
    Peut inclure la synchronisation d’annuaires avec votre Windows Server AD local. Enfin, vous pouvez configurer Azure AD pour la fédération avec un fournisseur d’identité tiers.
    
- Réseau
    
    Se compose de votre canal Internet existant ou d’une connexion ExpressRoute avec homologation Microsoft pour Office 365 ou Dynamics 365.
    
- Sur site
    
    Peut être composé de serveurs existants pour Exchange, SharePoint et Skype Entreprise, qui doivent être mis à jour vers la dernière version disponible. Vous pouvez les combiner à leurs équivalents Office 365 pour des scénarios hybrides.
    
Configurer votre propre [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
## <a name="skype-for-business-2015-hybrid"></a>Skype Entreprise 2015 hybride

Skype pour entreprise 2015 hybride vous permet de combiner un déploiement sur site existant avec Skype pour l’activité en ligne. Certains utilisateurs sont hébergées sur site et certains utilisateurs sont hébergées en ligne, mais les utilisateurs partagent le même domaine de Session Initiation Protocol (SIP), par exemple, contoso.com. Cette configuration hybride permet de migrer sur site vers Office 365 au fil du temps, selon la planification. Skype pour entreprise 2015 peut également être intégré avec Exchange Online.
  
**Figure 2 : Le Skype pour la configuration de Business 2015 hybride**

![Configuration hybride Skype Entreprise 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
La figure 2 illustre la Skype pour configuration hybride de Business 2015, consistant en un Skype sur site pour le pool de front-end d’entreprise 2015 et edge server communique avec Skype pour Business Online dans Office 365.
  
Pour plus d’informations, voir :
  
- [Planification de la connectivité d’hybride entre Skype pour Business Server et Skype pour professionnels en ligne](https://technet.microsoft.com/library/jj205403.aspx)
    
- [Configurations prises en charge hybride Skype pour Business Server 2015](https://technet.microsoft.com/library/jj945633.aspx)
    
- [Skype pour entreprise hybride](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>PBX cloud avec Skype Entreprise Server

PBX cloud avec Skype Entreprise Server vous permet de convertir un déploiement local de Skype Entreprise Server en une topologie avec une connectivité RTC (réseau téléphonique commuté) locale.  
  
**Figure 3 : Nuage PBX avec Skype pour Business Server**

![PBX cloud avec Skype Entreprise Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
La figure 3 illustre le PBX nuage avec Skype pour la configuration de serveur d’entreprise, consistant en un local PBX existant ou passerelle de télécommunications, un Skype pour Business Server et le RTPC connecté au PBX de nuage de Microsoft dans Office 365, notamment Skype pour les entreprises En ligne.
  
Les utilisateurs au sein de l’organisation qui sont hébergés dans le cloud peuvent recevoir des services PBX (Private Branch Exchange) du cloud Microsoft qui incluent la signalisation et la messagerie vocale, mais la connectivité RTC (tonalité) est fournie via la fonctionnalité Voix Entreprise de votre déploiement Skype Entreprise Server local.
  
Il s’agit d’un bon exemple de configuration hybride qui vous permet de migrer progressivement vers un service informatique. Vous pouvez conserver les fonctionnalités vocales de vos utilisateurs lorsque vous commencez à les déplacer vers Skype Entreprise Online. Vous pouvez déplacer vos utilisateurs comme vous le souhaitez, sachant que leurs fonctionnalités vocales continueront, indépendamment de l’endroit où elles sont hébergées.  
  
Pour plus d’informations, reportez-vous à la section [planification de la connectivité d’hybride entre Skype pour Business Server et Skype pour Business Online ou Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).
  
Si vous n’avez pas encore mis en place un déploiement Lync Server ou Skype Entreprise Server, vous pouvez utiliser l’édition Cloud Connector de Skype Entreprise. Il s’agit d’un ensemble complet d’ordinateurs virtuels qui implémentent une connectivité RTC locale avec la fonctionnalité PBX cloud.
  
Pour plus d’informations, reportez-vous à la section [planifier Skype pour connecteur de Cloud Business Edition](https://technet.microsoft.com/library/mt605227.aspx).
  
## <a name="sharepoint-hybrid"></a>Environnement hybride SharePoint

SharePoint hybride combine SharePoint Online dans Office 365 à votre batterie SharePoint locale. Vous pouvez ainsi profiter des avantages des deux environnements au travers d’une expérience connectée.
  
**Figure 4 : Configuration hybride de SharePoint**

![Configuration hybride SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
La figure 4 illustre la configuration hybride de SharePoint, consistant en une batterie de serveurs SharePoint locaux communiquent avec SharePoint Online dans Office 365.
  
Scénarios SharePoint hybrides
  
- [OneDrive hybride pour entreprise](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [Sites d’équipe hybride](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [B2B d’Extranet hybride](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [Recherche de hybride](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [Profils de hybride](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [Sélecteur de hybride](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    La mise en œuvre de scénarios hybrides est un jeu d’enfant à l’aide des Assistants, car ils permettent d’automatiser la configuration hybride. Ces derniers sont disponibles dans le Centre d’administration SharePoint Online dans Office 365.
    
- [Lanceur d’applications hybrides extensible](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    Cette fonctionnalité permet aux utilisateurs d’afficher et d’utiliser les applications Office 365 Video et Delve ainsi que des expériences dans les pages de leur batterie SharePoint locale.
    
Tous ces scénarios SharePoint hybrides, à l’exception du lanceur d’applications hybride extensible, sont disponibles pour les utilisateurs de SharePoint 2016 et SharePoint 2013.
  
Pour plus d’informations, consultez [Hybride de SharePoint](http://hybrid.office.com/sharepoint/).
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 hybride

Avec Exchange Server 2016 hybride, vous pouvez tirer parti du potentiel d’Exchange Online dans Office 365 pour les utilisateurs en ligne tandis que les utilisateurs locaux continueront à utiliser l’infrastructure Exchange Server existante.  
  
**Figure 5 : Configuration Exchange 2016 hybride**

![Configuration hybride Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
La figure 5 illustre la configuration Exchange 2016 hybride, qui se compose de serveurs de boîtes aux lettres Exchange local communique avec Exchange Online Protection et boîtes aux lettres dans Office 365.
  
Certains utilisateurs ont recours à un serveur de messagerie local tandis que d’autres utilisent Exchange Online, mais ils partagent tous le même espace d’adressage de messagerie.  
  
Cette configuration hybride :
  
- Tire parti de votre infrastructure Exchange Server pendant la migration vers Exchange Online dans le temps, sur vos prévisions.
    
- vous permet de prendre en charge les sites distants sans investir dans une infrastructure de succursale ;
    
- vous permet d’acheminer le courrier électronique Internet entrant via Exchange Online Protection dans Office 365 ;
    
- répond aux besoins des sociétés multinationales possédant des filiales qui exigent que les données soient hébergées sur site.
    
Vous pouvez également intégrer cette configuration hybride à d’autres applications Microsoft Office 365, notamment Skype Entreprise Online et SharePoint Online.
  
Pour plus d’informations, consultez [Déploiement d’Exchange Server hybride](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) et [Exchange hybride](http://hybrid.office.com/exchange/).
  
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d'entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)



