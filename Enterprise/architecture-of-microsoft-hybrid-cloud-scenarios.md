---
title: "Architecture des scénarios de cloud hybride Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Résumé : Comprendre l'architecture d'offres de cloud hybride Microsoft."
ms.openlocfilehash: 0909964421cecec455ed3c45c965a330501d361c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Architecture des scénarios de cloud hybride Microsoft

 **Résumé :** Comprendre l'architecture d'offres de cloud hybride Microsoft.
  
Utilisez une approche orientée architecture pour planifier et implémenter des scénarios de cloud hybride avec des services et plateformes de Microsoft.
  
**Figure 1 : Pile du cloud hybride Microsoft**

![Pile du cloud hybride Microsoft](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
La Figure 1 présente la pile du cloud hybride Microsoft et sa couche, qui incluent les applications et scénarios d’identité, réseau et locaux et la catégorie de service de cloud (SaaS Microsoft, Azure SaaS et Azure PaaS).
  
La couche d'applications et de scénarios contient les scénarios de cloud hybride spécifiques qui sont détaillés dans les autres articles de ce modèle. Les couches locales, d'identité et réseau peuvent être communes aux catégories de service de cloud (SaaS, PaaS ou IaaS).
  
- Sur site
    
    L'infrastructure locale pour les scénarios hybrides peut inclure des serveurs pour SharePoint, Exchange, Skype Entreprise et des applications métier. Elle peut également inclure des banques de données (bases de données, listes, fichiers). Sans connexions ExpressRoute, l'accès à la banque de données stockées locale doit être autorisé via un proxy inverse ou en rendant le serveur ou les données accessibles sur votre zone DMZ ou extranet.
    
- Réseau
    
    Il existe deux options pour la connectivité aux plateformes et services cloud Microsoft : votre canal Internet existant et ExpressRoute. Utilisez une connexion ExpressRoute si des performances prévisibles sont importantes. Vous pouvez utiliser une connexion ExpressRoute pour vous connecter directement aux services SaaS de Microsoft (Office 365 et Dynamics 365), aux services PaaS Azure et aux services SaaS Azure.
    
- Identity
    
    Pour l'infrastructure d'identité de cloud, il y a deux façons de procéder, en fonction de la plateforme de cloud Microsoft. Pour SaaS et Azure PaaS, intégrez votre infrastructure d'identité locale avec Azure AD ou effectuez une fédération avec vos fournisseurs d'identité tiers ou infrastructure d'identité locale. Pour les ordinateurs virtuels exécutés dans Azure, vous pouvez étendre votre infrastructure d'identité locale, telle que Windows Server AD, aux réseaux virtuels où résident vos ordinateurs virtuels.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Scénarios de cloud hybride pour le processus d’adoption du cloud en trois phases

De nombreuses entreprises, y compris celles détenues par Microsoft, utilisent une approche à trois phases pour adopter le cloud. Les scénarios de cloud hybride peuvent jouer un rôle dans chaque phase.
  
1. Déplacement des charges de travail de productivité vers les services SaaS
    
    Pour les charges de travail de productivité qui se trouvent actuellement en local ou qui doivent y demeurer, les scénarios hybrides permettent de les intégrer à leur équivalent dans le cloud.
    
2. Développement de nouvelles applications modernes dans les services PaaS Azure
    
    Les applications hybrides PaaS Azure peuvent tirer parti en toute sécurité des ressources de serveur ou de stockage locales.
    
3. Déplacement d’applications existantes vers les services IaaS Azure
    
    Pour les scénarios de réplication dans le cloud (« lift-and-shift ») et de refonte orientée cloud (« build-in-the-cloud »), les applications serveur exécutées sur des ordinateurs virtuels Azure offrent des possibilités de configuration et de mise à l’échelle faciles à mettre en œuvre.
    
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d'entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)



