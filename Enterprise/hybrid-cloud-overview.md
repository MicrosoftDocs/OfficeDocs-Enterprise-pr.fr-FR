---
title: "Présentation du cloud hybride"
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
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: "Résumé : Comprendre la définition et les éléments du cloud hybride Microsoft."
ms.openlocfilehash: 3cf828b8411605a9d0bdd338c3b6c16a5892f6b7
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-overview"></a>Présentation du cloud hybride

 **Résumé :** Comprendre la définition et les éléments du cloud hybride Microsoft.
  
Le cloud hybride utilise des ressources de calcul ou de stockage sur votre réseau local et dans le cloud. Vous pouvez utiliser le cloud hybride pour migrer votre entreprise et ses besoins en ressources informatiques vers le cloud, ou intégrer des services et plateformes cloud à votre infrastructure locale existante dans le cadre de la mise en œuvre de votre stratégie informatique globale.
  
## <a name="microsoft-hybrid-cloud"></a>Cloud hybride Microsoft

Le cloud hybride Microsoft représente un ensemble de scénarios professionnels qui combinent une plateforme cloud Microsoft à un composant local, par exemple : 
  
- Obtention de résultats de recherche pour du contenu stocké dans une batterie SharePoint locale et dans SharePoint Online dans Office 365.
    
- Application mobile exécutée dans Azure qui interroge un magasin de données local.
    
- Charge de travail informatique sur un intranet exécutée sur des ordinateurs virtuels Azure.
    
**Figure 1 : Composants du cloud hybride Microsoft**

![Composants du cloud hybride Microsoft](images/Hybrid_Poster/MS_Hybrid_Cloud.png)
  
La figure 1 présente les composants du cloud hybride Microsoft, d’un réseau local à l’ensemble des services Office 365, Paas Azure et IaaS Azure disponibles sur Internet ou une connexion ExpressRoute.
  
Étant donné que Microsoft propose l’une des solutions cloud les plus complètes sur le marché (Software as a Service (SaaS), Platform as a Service (PaaS) et Infrastructure as a Service (IaaS), vous pouvez :
  
- tirer parti des investissements que vous avez effectués dans votre environnement local lorsque vous migrez des charges de travail et des applications vers le cloud ;
    
- incorporer des scénarios de cloud hybride dans votre planification informatique à long terme, par exemple, lorsque des réglementations ou des politiques vous empêchent de déplacer des données ou des charges de travail spécifiques vers le cloud ;
    
- créer des scénarios hybrides supplémentaires qui incluent plusieurs services et plateformes cloud de Microsoft.
    
Les scénarios de cloud hybride utilisant les services cloud Microsoft dépendent de la plateforme utilisée.
  
- SaaS
    
    Les services SaaS de Microsoft incluent Office 365, Microsoft Intune et Microsoft Dynamics 365. Les scénarios de cloud hybride avec les services SaaS de Microsoft combinent ces services aux applications ou services locaux. Par exemple, Exchange Online exécuté dans Office 365 peut être intégré à Skype Entreprise 2015 qui est déployé en local.
    
- Azure PaaS
    
    Les services PaaS de Microsoft Azure permettent de créer des applications basées sur le cloud. Les scénarios de cloud hybride avec les services PaaS Azure combinent une application PaaS Azure aux applications ou ressources locales. Par exemple, une application PaaS Azure peut interroger en toute sécurité une banque de données locale afin d'obtenir les informations nécessaires à afficher pour les utilisateurs de l'application mobile.
    
- Azure IaaS
    
    Les services IaaS Azure permettent de créer et d'exécuter des charges de travail informatiques basées sur serveur dans le cloud, et non dans votre centre de données local. Les scénarios de cloud hybride avec les services IaaS Azure sont généralement constitués d'une charge de travail informatique qui s'exécute sur des ordinateurs virtuels et qui est connectée en toute transparence à votre réseau local. Les utilisateurs locaux ne verront pas la différence.
    
## <a name="elements-of-hybrid-cloud"></a>Éléments du cloud hybride

Vous devez tenir compte des éléments suivants lorsque vous planifiez et implémentez des scénarios de cloud hybride utilisant des plateformes et services cloud Microsoft.
  
- Réseau
    
    Dans le cadre de scénarios de cloud hybride, la mise en réseau inclut la connectivité aux plateformes et services cloud de Microsoft et suffisamment de bande passante pour conserver les performances en cas de pic au niveau des charges. Pour plus d'informations, voir [Mise en réseau cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identity
    
    Dans le cadre de scénarios hybrides SaaS et PaaS Azure, l'identité peut inclure Azure AD en tant que fournisseur d'identité commun, qui peut alors être synchronisé avec Windows Server AD en local, ou fédéré avec Windows Server AD ou d'autres fournisseurs d'identité. Vous pouvez également étendre votre infrastructure d'identité locale pour IaaS Azure. Pour plus d'informations, voir [Identité cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-identity-for-enterprise-architects.md).
    
- Sécurité
    
    Dans le cadre de scénarios cloud hybrides, la sécurité inclut la protection et la gestion de vos identités, la protection des données, la gestion des privilèges d'administrateur, la sensibilisation aux menaces et l'implémentation de stratégies de gouvernance et de sécurité. Pour plus d'informations, voir [Sécurité cloud Microsoft pour les architectes d'entreprise](https://technet.microsoft.com/library/dn919927.aspx#security).
    
- Gestion
    
    Dans le cadre de scénarios cloud hybrides, la gestion inclut la capacité à assurer l'entretien des paramètres, données, comptes, stratégies et autorisations, ainsi qu'à assurer la surveillance continue de l'état d'intégrité des éléments du scénario et de ses performances. Vous pouvez également utiliser le même ensemble d'outils, tels que Systems Management Server, pour la gestion des ordinateurs virtuels dans IaaS Azure.
    
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d'entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)
 


