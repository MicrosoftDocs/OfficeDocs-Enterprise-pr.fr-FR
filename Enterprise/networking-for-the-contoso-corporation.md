---
title: Mise en réseau de Contoso Corporation
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 'Résumé : Découvrez l’infrastructure du réseau Contoso et comment il peut utiliser ExpressRoute pour un accès optimisé pour les offres de cloud de Microsoft.'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915219"
---
# <a name="networking-for-the-contoso-corporation"></a>Mise en réseau de Contoso Corporation

 **Résumé :** Comprendre l’infrastructure du réseau Contoso et comment il peut utiliser ExpressRoute pour un accès optimisé pour les offres de cloud de Microsoft.
  
Pour adopter une infrastructure cloud-inclus, les ingénieurs réseau de Contoso réalisé le changement fondamental dans la façon dont le trafic réseau vers le déplacement des services en nuage. Au lieu d’optimisation uniquement le trafic vers les serveurs locaux et des centres de données, égale veiller à optimiser le trafic sur le bord Internet et sur Internet.
  
## <a name="contosos-networking-infrastructure"></a>Infrastructure du réseau de Contoso

Contoso possède l’infrastructure réseau illustrée dans la Figure 1.
  
**Figure 1 : infrastructure WAN de Contoso**

![Infrastructure WAN de Contoso faisant la liaison avec les sièges sociaux, les centres régionaux et les succursales](media/Contoso-Poster/Contoso-WW-Net.png)
  
La Figure 1 présente les bureaux internationaux de Contoso et les connexions WAN qui relient les centres régionaux et les succursales.
  
Le réseau de Contoso comprend les éléments suivants :
  
- Réseau local
    
    Liaisons WAN connectent le siège social Paris à des bureaux régionaux et les bureaux régionaux aux filiales dans une configuration spoke and hub. Dans chaque bureau, routeurs acheminer du trafic vers les hôtes ou les points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.
    
- Connexion à Internet
    
    Chaque bureau a sa propre connectivité Internet via un serveur proxy. Cela est généralement implémenté comme un réseau étendu un lien vers un fournisseur d’accès local qui fournit également des adresses IP publiques pour le serveur proxy.
    
- Présence sur Internet
    
    Contoso possède le nom de domaine public contoso.com. Le site web public de Contoso pour le classement des produits est un ensemble de serveurs dans un centre de données connectés à Internet dans le campus Paris. Contoso utilise un /24 plage d’adresses IP publique sur Internet.
    
## <a name="contosos-app-infrastructure"></a>Infrastructure d’application de Contoso

Contoso a conçu son infrastructure d’applications et serveur pour les éléments suivants :




  
**Figure 2 : infrastructure des applications internes de Contoso**

![Infrastructure des applications internes de Contoso](media/Contoso-Poster/App-Infra.png)
  
- Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.
    
- 
Les centres régionaux utilisent les serveurs d’applications régionaux pour les bureaux régionaux et les succursales. Ces serveurs se synchronisent avec les serveurs du siège social parisien.
    
- Le site de Paris comporte les centres de données contenant les serveurs d’applications centralisés qui servent l’organisation entière.
    
Pour les utilisateurs des centres régionaux et des succursales, 60 % des ressources requises par les collaborateurs peuvent être prises en charge par les serveurs de ces sites. Les 40 % des demandes de ressources restantes doivent accéder au siège social parisien par le biais d’une connexion WAN.
  
## <a name="contosos-network-analysis"></a>Analyse du réseau de Contoso

Voici les résultats d’analyse de Contoso des modifications nécessaires sur leur réseau pour prendre en charge les différentes catégories d’offres de cloud de Microsoft :
  
|**Offres de cloud SaaS : Office 365, EMS et Dynamics 365**|**PaaS Azure : Applications mobiles**|**Azure IaaS : Charges de travail sur le serveur**|
|:-----|:-----|:-----|
|L’adoption réussie des services SaaS par les utilisateurs dépend de la haute disponibilité et des performances de la connectivité à Internet ou directement aux services cloud de Microsoft.
  <br/> L’accès Internet actuel est censé être satisfaisant pour les utilisateurs mobiles.
  <br/> Pour les utilisateurs sur l’intranet de Contoso, chaque bureau doit être analysé et optimisé pour le débit à Internet et au centre de données pour l’Europe de Microsoft qui héberge les clients Office 365, EMS et Dynamics 365 des boucles.  <br/> |Pour mieux accompagner les collaborateurs mobiles, des applications héritées et certains sites de partage de fichiers sont repensés et déployés en tant qu’applications Azure PaaS. Pour optimiser ses performances, Contoso prévoit de déployer de nouvelles applications dans le monde entier à partir de différents centres de données Azure. Azure Traffic Manager permet d’envoyer des demandes d’application cliente, qu’elles proviennent d’un utilisateur mobile ou d’un ordinateur situé dans un bureau, vers le centre de données Azure le plus proche hébergeant l’application.  <br/>   

Le service informatique doit ajouter des performances d’application PaaS et la répartition du trafic à sa solution de contrôle d’intégrité du réseau. <br/> |Pour migrer les serveurs existants et les serveurs d’archivage hors des centres de données du siège social parisien et ajouter des serveurs selon les besoins en fin de trimestre, Contoso prévoit d’utiliser des machines virtuelles s’exécutant dans les services d’infrastructure Azure. 

  <br/> Les réseaux virtuels Azure qui contiennent ces serveurs doivent être conçus pour des espaces d’adresse, un routage et une structure DNS intégrée non superposés.

  <br/> Le service informatique doit inclure ces nouveaux serveurs dans son système de gestion et de surveillance réseau.  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Utilisation de Contoso de ExpressRoute

ExpressRoute est une connexion WAN dédiée à partir de votre emplacement vers un emplacement homologation Microsoft qui connecte votre réseau pour le réseau de cloud Microsoft. Connexions ExpressRoute fournissent des performances prévisibles et un SLA de disponibilité de 99,9 %. .
  
Avec une connexion ExpressRoute, vous êtes connecté au réseau Microsoft dans le nuage et à tous les emplacements de centre de données de Microsoft dans le même continent. Le trafic entre l’emplacement homologation cloud et le centre de données Microsoft destination est transmise via le réseau de cloud Microsoft
  
**Figure 3 : réseau cloud mondial de Microsoft**

![Réseau cloud mondial de Microsoft](media/Contoso-Poster/MS-WW-Cloud.png)
  
La Figure 3 montre le réseau cloud interconnecté de Microsoft pour les différentes régions du monde.
  
Avec ExpressRoute Premium, vous pouvez atteindre tous les centres de données Microsoft sur tous les continents à partir de n’importe quel emplacement d’homologation Microsoft situé sur un des continents. Le trafic entre les continents est réalisé sur le réseau cloud de Microsoft.
  
En fonction de l’analyse du trafic actuel et futur d’offres de cloud de Microsoft, Contoso a effectué une évaluation du réseau et implémenté une connexion ExpressRoute (basés sur MPLS) pour tout pour accéder aux ressources Azure, avec peering privée et publique relations, à partir du siège social Paris à l’emplacement homologation Microsoft en Europe.
  
Cette connexion apportera au service informatique de Contoso :
  
- Des performances cohérentes pour l’administration des applications Azure PaaS réparties
    
    Tous les développeurs d’applications et d’infrastructure principaux de Contoso administrateurs sont dans le campus Paris. Avec les applications Azure PaaS distribuées à différents centres de données Azure dans le monde entier, Contoso doit des performances homogènes à partir du campus Paris pour gérer les applications et leurs ressources de stockage, qui sont composés de To de documents.
    
- Des performances cohérentes pour l’administration des serveurs dans Azure IaaS
    
    Les administrateurs du centre de données de Contoso se trouvent dans le campus Paris et les serveurs à être déployés dans Azure sont une extension du centre de données Paris. Contoso doit des performances homogènes à ces nouveaux serveurs pour l’accès aux applications héritées et d’archivage et de traitement de la fin du trimestre.
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Chemin d’accès de Contoso cloud préparation mise en réseau

Contoso a établi la procédure suivante pour préparer son réseau au cloud de Microsoft :
  
1. Optimiser les ordinateurs des collaborateurs pour accéder à Internet

    
    Les ordinateurs individuels sont vérifiés pour assurer que les ressources les plus récentes (pile TCP/IP, navigateur, pilotes de carte réseau, mises à jour de sécurité et du système d’exploitation) sont bien installées.
    
2. Analyser l’utilisation de la connexion Internet dans chaque bureau et apporter des ressources supplémentaires selon les besoins
    
    
Une analyse de l’utilisation d’Internet est réalisée dans chaque bureau et la bande passante de la connexion WAN est renforcée si son utilisation est supérieure ou égale à 70 %.
    
3. Analyser les systèmes du DMZ de chaque bureau pour obtenir des performances optimales

    
    Une analyse des pare-feu, IDS et autres systèmes connectés à Internet a lieu pour garantir des performances optimales. Les serveurs proxy sont mis à jour ou à niveau selon les besoins.
    
4. Ajouter ExpressRoute au site parisien
    
    Offre un accès cohérent aux ressources Azure pour administrer les charges de travail Azure PaaS et IaaS.
    
5. Créer et tester un profil Azure Traffic Manager pour les applications Azure PaaS
    
    Tester un profil Azure Traffic Manager utilisant la méthode de routage des performances afin d’expérimenter la répartition du trafic Internet vers les sites régionaux.
    
6. Réserver l’espace d’adressage privé pour les réseaux virtuels Azure

    
    Se baser sur les chiffres des serveurs à court terme et long terme planifiés dans Azure IaaS pour réserver l’espace d’adressage privé aux réseaux virtuels Azure et à leurs sous-réseaux.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)




