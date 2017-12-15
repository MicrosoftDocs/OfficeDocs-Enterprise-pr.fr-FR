---
title: "Évolution de votre réseau pour la connectivité au cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Résumé : Comprendre comment l'adoption cloud nécessite une nouvelle approche des investissements relatifs à l'infrastructure réseau."
ms.openlocfilehash: 810640ab3b870759424af2f88392bbaf0b0e11c7
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Évolution de votre réseau pour la connectivité au cloud

 **Résumé :** Comprendre comment l'adoption cloud nécessite une nouvelle approche des investissements relatifs à l'infrastructure réseau.
  
La migration vers le cloud modifie le volume et la nature des flux de trafic internes et externes à un réseau d'entreprise. Elle a également une incidence sur les approches permettant de réduire les risques de sécurité.
  
- Avant le cloud
    
    La plupart des investissements concernant les infrastructures réseau visaient à garantir la disponibilité, la fiabilité et les performances de la connectivité pour les centres de données locaux. Pour de nombreuses organisations, la connectivité Internet n'était pas essentielle pour les opérations d'entreprise internes. Les limites de réseau constituaient la principale défense contre les violations de sécurité.
    
- Après le cloud
    
    Avec la migration de la nouvelle productivité et les charges de travail informatiques exécutées dans le cloud, les investissements concernant les infrastructures ont délaissé les centres de données locaux au profit de la connectivité Internet, qui est désormais essentielle pour les opérations d'entreprise internes. La connectivité fédérée oriente la stratégie de sécurité sur la protection des identités et des données lors de leur circulation sur le réseau et sur les points de connectivité aux services cloud de Microsoft.
    
Investissements concernant les infrastructures réseau commencent par la connectivité. Les investissements supplémentaires dépendent de la catégorie du service cloud.
  
- **Software as a Service (SaaS)** les services SaaS de Microsoft incluent Office 365, Microsoft Intune et Microsoft Dynamics 365. L'adoption réussie des services SaaS par les utilisateurs dépend de la haute disponibilité et des performances de la connectivité à Internet ou directement aux services cloud de Microsoft.
    
    L'architecture réseau se concentre sur une connectivité fiable et redondante, ainsi que sur une bande passante suffisante. Les investissements en cours incluent la surveillance et l'optimisation des performances.
    
- **Azure Platform as a Service (PaaS)**: en plus des investissements pour les services SaaS de Microsoft, les applications PaaS pour plusieurs sites ou réparties géographiquement peuvent nécessiter la création d'un système Azure Traffic Manager pour distribuer le trafic client. Les investissements en cours incluent la surveillance des performances et de la distribution du trafic, ainsi que le test de basculement.
    
- **Azure Infrastructure as a Service (IaaS)**: en plus des investissements pour les services SaaS et PaaS de Microsoft, l'exécution de charges de travail informatiques dans IaaS nécessite la création et la configuration de réseaux virtuels Azure hébergeant des machines virtuelles, la connectivité sécurisée des applications exécutées sur ces dernières, le routage, l'adressage IP, le DNS et l'équilibrage de charge. Les investissements en cours incluent la surveillance et le dépannage des performances et de la sécurité.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Domaines d'investissement concernant les réseaux pour la réussite du cloud

Les entreprises tirent parti d'une approche méthodique pour optimiser le débit du réseau sur votre intranet et sur Internet. Vous pouvez également tirer avantage d'une connexion ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Optimisation de la connectivité intranet à votre réseau de périmètre

Au fil des ans, de nombreuses organisations ont optimisé la connectivité intranet et les performances pour les applications exécutées dans des centres de données locaux. Grâce à la productivité et à l'exécution de charges de travail informatiques dans le cloud de Microsoft, des investissements supplémentaires doivent garantir une haute disponibilité de la connectivité et des performances de trafic optimales entre votre réseau de périmètre et vos utilisateurs intranet.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Optimisation du débit au niveau de votre réseau de périmètre

La plupart de votre trafic de productivité quotidien empruntant le cloud, vous devez examiner attentivement l'ensemble des systèmes au niveau de votre réseau de périmètre afin de vous assurer qu'ils sont à jour, fournissent une disponibilité élevée et ont une capacité suffisante pour répondre aux charges de pointe.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Pour un SLA élevé sur Azure, Office 365 et Dynamics 365, utiliser ExpressRoute

Bien que vous puissiez utiliser votre connexion Internet actuelle à partir de votre réseau de périmètre, le trafic vers et à partir des services cloud de Microsoft doit partager le canal avec d'autres trafics intranet accédant à Internet. En outre, le trafic vers les services cloud de Microsoft est soumis à la congestion du trafic Internet.
  
Pour un SLA élevé et des performances optimales, utilisez ExpressRoute, une connexion WAN dédiée entre votre réseau et Azure, Office 365, Dynamics 365 ou tous les trois. 
  
ExpressRoute peut tirer profit de votre fournisseur de réseau existant pour une connexion dédiée. Les ressources connectées par ExpressRoute apparaissent comme si elles se trouvaient sur votre réseau étendu, même pour les organisations dispersées géographiquement.
  
Pour plus d'informations, voir [ExpressRoute pour la connectivité au cloud de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Étendue des investissements concernant le réseau

L'étendue des investissements concernant le réseau dépend de la catégorie du service cloud. Investir dans le cloud de Microsoft optimise les investissements des équipes réseau. Par exemple, les investissements pour les services IaaS s'appliquent à tous les domaines d'investissement.
  
|||||
|:-----|:-----|:-----|:-----|
|Domaine d'investissement.  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Concevoir une connectivité Internet fiable et redondante avec une bande passante large  <br/> |S'applique  <br/> |S'applique  <br/> |S'applique  <br/> |
|Surveiller et régler le débit Internet pour les performances  <br/> |S'applique  <br/> |S'applique  <br/> |S'applique  <br/> |
|Résoudre les problèmes de connectivité et de débit Internet  <br/> |S'applique  <br/> |S'applique  <br/> |S'applique  <br/> |
|Concevoir un système Azure Traffic Manager pour équilibrer la charge du trafic sur différents points de terminaison  <br/> ||S'applique  <br/> |S'applique  <br/> |
|Concevoir une connectivité fiable, redondante et performante aux réseaux virtuels Azure  <br/> |||S'applique  <br/> |
|Créer une connectivité sécurisée aux machines virtuelles Azure  <br/> |||S'applique  <br/> |
|Concevoir et implémenter le routage entre les emplacements locaux et les réseaux virtuels  <br/> |||S'applique  <br/> |
|Concevoir et implémenter l'équilibrage de charge pour les charges de travail informatiques internes et accessibles sur Internet  <br/> |||S'applique  <br/> |
|Résoudre les problèmes de connectivité et de débit des machines virtuelles  <br/> |||S'applique  <br/> |
   
## <a name="see-also"></a>See Also

[Mise en réseau cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-networking-for-enterprise-architects.md)
  
[ExpressRoute pour la connectivité au cloud de Microsoft](expressroute-for-microsoft-cloud-connectivity.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route de Microsoft Enterprise Cloud : Ressources pour les décideurs en matière d'informatique](https://sway.com/FJ2xsyWtkJc2taRD)



