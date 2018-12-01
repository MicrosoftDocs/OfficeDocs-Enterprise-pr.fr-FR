---
title: Scénarios de cloud hybride pour les services SaaS Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Résumé : Découvrez les scénarios et l’architecture hybride pour Microsoft basée sur SaaS (Office 365) les offres de cloud.'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123411"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Scénarios de cloud hybride pour Microsoft SaaS (Office 365)

 **Résumé :** Comprendre les scénarios et l’architecture hybride pour Microsoft basée sur SaaS (Office 365) les offres de cloud.
  
Combinez des déploiements locaux d’Exchange, de SharePoint ou de Skype Entreprise à leur équivalent dans Office 365 dans le cadre d’une migration cloud ou d’une stratégie d’intégration à long terme.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Architecture de scénario hybride pour les services SaaS Microsoft

La figure 1 présente l’architecture des scénarios hybrides SaaS de Microsoft pour Office 365.
  
**Figure 1 : Scénarios hybrides Microsoft SaaS pour Office 365**

![Scénarios hybrides Microsoft SaaS pour Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Pour chaque couche de l’architecture :
  
- Applications et scénarios
    
    Il existe plusieurs scénarios hybrides SaaS au niveau des produits serveur Office et de leur équivalent dans Office 365 :
    
  - Exchange Server combiné à Exchange Online (Exchange Server hybride)
    
  - Skype Entreprise Server combiné à Skype Entreprise Online et aux nouveaux scénarios PBX cloud et édition Cloud Connector
    
  - SharePoint Server 2013, SharePoint Server 2016 ou SharePoint Server 2019 combinées avec SharePoint Online (plusieurs scénarios)
    
    Vous pouvez également mettre en place Exchange Online avec Skype Entreprise Server en local (scénario hybride de produit croisé).
    
- Identity
    
    Peut inclure la synchronisation d’annuaires avec votre Windows Server AD local. Enfin, vous pouvez configurer Azure AD pour la fédération avec un fournisseur d’identité tiers.
    
- Réseau
    
    Se compose de votre canal Internet existant ou d’une connexion ExpressRoute avec homologation Microsoft pour Office 365 ou Dynamics 365.
    
- Sur site
    
    Peut être composé de serveurs existants pour Exchange, SharePoint et Skype Entreprise, qui doivent être mis à jour vers la dernière version disponible. Vous pouvez les combiner à leurs équivalents Office 365 pour des scénarios hybrides.
    
Configurer votre propre environnement de développement/test Office 365, voir les [Guides de laboratoire de Test d’Office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype pour Business hybride

Skype pour Business hybride vous permet de combiner un déploiement local existant avec Skype pour Business Online. Certains utilisateurs sont hébergés sur un système local et certains utilisateurs sont hébergés en ligne, mais les utilisateurs partagent le même domaine de protocole SIP (Session Initiation), par exemple, contoso.com. Vous pouvez utiliser cette configuration hybride pour migrer à partir de locaux vers Office 365 au fil du temps, votre calendrier. Skype pour les entreprises peut également être intégré avec [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**La figure 2 : Skype pour la configuration hybride d’entreprise**

![Le Skype pour la configuration hybride d’entreprise](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
La figure 2 illustre la Skype pour la configuration hybride d’entreprise, comprenant un Skype locale pour Business le pool frontal et edge server communique avec Skype pour Business Online dans Office 365.
  
Pour plus d’informations, voir [planification de la connectivité hybride entre Skype pour Business Server et Skype pour Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>PBX cloud avec Skype Entreprise Server

Nuage PBX avec Skype pour Business Server vous permet de passer un Skype pour le déploiement local de Business Server à une topologie existante avec une connectivité sur site Public réseau de téléphonique commuté (RTC). 
  
**Figure 3 : PBX cloud avec Skype Entreprise Server**

![PBX cloud avec Skype Entreprise Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
La figure 3 montre le système PBX sur le nuage avec Skype pour la configuration de Business Server, constitué d’une locale PBX existant ou passerelle télécommunications, un Skype pour Business Server et le réseau RTC connecté au PBX Microsoft Cloud dans Office 365, qui comprend Skype pour les entreprises En ligne.
  
Les utilisateurs au sein de l’organisation qui sont hébergés dans le cloud peuvent recevoir des services PBX (Private Branch Exchange) du cloud Microsoft qui incluent la signalisation et la messagerie vocale, mais la connectivité RTC (tonalité) est fournie via la fonctionnalité Voix Entreprise de votre déploiement Skype Entreprise Server local.
  
Il s’agit d’un bon exemple de configuration hybride qui vous permet de migrer graduellement à un service en nuage. Vous pouvez conserver les fonctionnalités vocales de vos utilisateurs lorsque vous commencez à déplacer vers Skype pour Business Online. Vous pouvez déplacer vos utilisateurs à votre rythme, sachant que leurs fonctionnalités vocales continuera no question où ils sont hébergés. 
  
Pour plus d’informations, voir [planification de la connectivité hybride entre Skype pour Business Server et Skype pour Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Si vous n’avez pas encore mis en place un déploiement Lync Server ou Skype Entreprise Server, vous pouvez utiliser l’édition Cloud Connector de Skype Entreprise. Il s’agit d’un ensemble complet d’ordinateurs virtuels qui implémentent une connectivité RTC locale avec la fonctionnalité PBX cloud.
  
Pour plus d’informations, voir [planifier Skype pour l’édition de connecteur Business Cloud](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Environnement hybride SharePoint

SharePoint hybride combine SharePoint Online dans Office 365 à votre batterie SharePoint locale. Vous pouvez ainsi profiter des avantages des deux environnements au travers d’une expérience connectée.
  
**Figure 4 : Configuration hybride SharePoint**

![Configuration hybride SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
La figure 4 illustre la configuration hybride SharePoint, constitué d’une batterie de serveurs SharePoint locale communiquer avec SharePoint Online dans Office 365.
  
Scénarios SharePoint hybrides
  
- [OneDrive Entreprise hybride](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Hybride Extranet B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Recherche hybride](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Profils hybrides](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Sélecteur de hybride](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    La mise en œuvre de scénarios hybrides est un jeu d’enfant à l’aide des Assistants, car ils permettent d’automatiser la configuration hybride. Ces derniers sont disponibles dans le Centre d’administration SharePoint Online dans Office 365.
    
- [Lanceur d'applications hybride extensible](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Cette fonctionnalité permet aux utilisateurs d’afficher et d’utiliser les applications Office 365 Video et Delve ainsi que des expériences dans les pages de leur batterie SharePoint locale.
    
Tous ces scénarios SharePoint hybrides, à l’exception du lanceur d’applications hybride extensible, sont disponibles pour les utilisateurs de SharePoint 2016 et SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 hybride

Avec Exchange Server 2016 hybride, vous pouvez tirer parti du potentiel d’Exchange Online dans Office 365 pour les utilisateurs en ligne tandis que les utilisateurs locaux continueront à utiliser l’infrastructure Exchange Server existante.  
  
**Figure 5 : Configuration hybride Exchange 2016**

![Configuration hybride Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
La figure 5 illustre la configuration hybride d’Exchange 2016, constituée de serveurs de boîtes aux lettres Exchange locale communiquant avec Exchange Online Protection et de boîtes aux lettres dans Office 365.
  
Certains utilisateurs ont recours à un serveur de messagerie local tandis que d’autres utilisent Exchange Online, mais ils partagent tous le même espace d’adressage de messagerie.  
  
Cette configuration hybride :
  
- tire parti de votre infrastructure Exchange Server existante pendant que vous effectuez une migration progressive vers Exchange Online en respectant votre planning ;



    
- vous permet de prendre en charge les sites distants sans investir dans une infrastructure de succursale ;
    
- vous permet d’acheminer le courrier électronique Internet entrant via Exchange Online Protection dans Office 365 ;
    
- répond aux besoins des sociétés multinationales possédant des filiales qui exigent que les données soient hébergées sur site.
    
Vous pouvez également intégrer cette configuration hybride à d’autres applications Microsoft Office 365, notamment Skype Entreprise Online et SharePoint Online.
  
Pour plus d’informations, voir [Déploiements hybrides Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d'entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

