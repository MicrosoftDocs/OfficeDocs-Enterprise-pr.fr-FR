---
title: "Mise en réseau de Contoso Corporation"
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
description: "Résumé : Comprendre la définition et les éléments du cloud hybride Microsoft."
ms.openlocfilehash: 0943864c8a9982eba00a139617ebe17d39cdde4e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="networking-for-the-contoso-corporation"></a>Mise en réseau de Contoso Corporation

 **Résumé :** Comprendre la définition et les éléments du cloud hybride Microsoft.
  
Pour adopter une infrastructure cloud-inclus, les ingénieurs réseau de Contoso réalisé le changement fondamental dans la manière dont le trafic réseau vers les voyages de services en nuage. Au lieu de n’optimiser le trafic vers les serveurs locaux et des centres de données, égale de veiller à l’optimisation du trafic vers le bord de l’Internet et via Internet.
  
## <a name="contosos-networking-infrastructure"></a>Infrastructure du réseau de Contoso

Contoso possède l’infrastructure réseau illustrée dans la Figure 1.
  
**Figure 1 : Infrastructure de réseau étendu de Contoso**

![Infrastructure WAN de Contoso faisant la liaison avec les sièges sociaux, les centres régionaux et les succursales](images/Contoso_Poster/Contoso_WW_Net.png)
  
La Figure 1 présente les bureaux internationaux de Contoso et les connexions WAN qui relient les centres régionaux et les succursales.
  
Le réseau de Contoso comprend les éléments suivants :
  
- Réseau local
    
    Liaisons WAN connectent le siège social de Paris à des filiales et bureaux régionaux vers des bureaux satellites dans une configuration spoke and hub. Dans chaque bureau, les routeurs acheminer du trafic vers les hôtes ou les points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.
    
- Connexion à Internet
    
    Chaque bureau a sa propre connexion à Internet via un serveur proxy. Cela est généralement implémenté comme un WAN lien vers un fournisseur de services Internet local qui fournit également des adresses IP publiques pour le serveur proxy.
    
- Présence sur Internet
    
    Contoso possède le nom de domaine public de contoso.com. Le site web public de Contoso pour commander des produits est un ensemble de serveurs dans un centre de données connecté à Internet dans le campus de Paris. Contoso utilise un /24 plage d’adresses IP publique sur Internet.
    
## <a name="contosos-app-infrastructure"></a>Infrastructure d’application de Contoso

Contoso a conçu son infrastructure de serveur et d’application pour les éléments suivants :
  
**Figure 2 : Infrastructure de Contoso pour applications internes**

![Infrastructure des applications internes de Contoso](images/Contoso_Poster/App_Infra.png)
  
- Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.
    
- Concentrateurs régionaux utilisent les serveurs régionaux application régional et les bureaux satellites. Ces serveurs se synchronisent avec des serveurs au siège de Paris.
    
- Le site de Paris comporte les centres de données contenant les serveurs d’applications centralisés qui servent l’organisation entière.
    
Pour les utilisateurs des centres régionaux et des succursales, 60 % des ressources requises par les collaborateurs peuvent être prises en charge par les serveurs de ces sites. Les 40 % des demandes de ressources restantes doivent accéder au siège social parisien par le biais d’une connexion WAN.
  
## <a name="contosos-network-analysis"></a>Analyse du réseau de Contoso

Voici les résultats de l’analyse de Contoso des modifications nécessaires sur leur réseau pour s’adapter à différentes catégories d’offres en nuage de Microsoft :
  
|**Les offres en nuage SaaS : Office 365, EMS et Dynamics 365**|**PaaS Azure : Les applications mobiles**|**IaaS Azure : Charges de travail serveur**|
|:-----|:-----|:-----|
|Adoption réussie de services SaaS par utilisateurs dépend hautement disponible et performante la connectivité à Internet, ou directement aux services de cloud de Microsoft.  <br/> Pour les utilisateurs mobiles, leur accès à Internet en cours est supposé pour être suffisante.  <br/> Pour les utilisateurs de l’intranet de Contoso, chaque bureau doit être analysé et optimisée pour le débit à Internet et de la durée des boucles avec le centre de données européen de Microsoft hébergeant les locataires Office 365, EMS et Dynamics 365.  <br/> |Pour mieux accompagner les collaborateurs mobiles, des applications héritées et certains sites de partage de fichiers sont repensés et déployés en tant qu’applications Azure PaaS. Pour optimiser ses performances, Contoso prévoit de déployer de nouvelles applications dans le monde entier à partir de différents centres de données Azure. Azure Traffic Manager permet d’envoyer des demandes d’application cliente, qu’elles proviennent d’un utilisateur mobile ou d’un ordinateur situé dans un bureau, vers le centre de données Azure le plus proche hébergeant l’application.  <br/>  Le service informatique doit ajouter PaaS les performances des applications et la distribution du trafic à leur solution de surveillance de la santé de réseau. <br/> |Pour déplacer certains serveurs hérités et archivage sur les centres de données campus Paris et ajouter les serveurs selon les besoins pour le traitement de fin de trimestre, Contoso veut utiliser des ordinateurs virtuels en cours d’exécution dans les services d’infrastructure Azure.  <br/> Les réseaux virtuels Azure qui contiennent ces serveurs doivent être conçus pour les espaces d’adressage non superposées, DNS et de routage intégré.  <br/> Le service informatique doit inclure ces nouveaux serveurs dans son système de gestion et de surveillance réseau.  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Utilisation de Contoso de ExpressRoute

ExpressRoute est une connexion WAN dédiée à partir de votre emplacement dans un emplacement d’homologation Microsoft qui connecte votre réseau pour le réseau de nuage de Microsoft. ExpressRoute les connexions offrent des performances prévisibles et une disponibilité de 99,9 % SLA. .
  
Avec une connexion ExpressRoute, vous êtes connecté au réseau Microsoft cloud et à tous les emplacements de centre de données de Microsoft dans le même continent. Le trafic entre l’emplacement d’homologation cloud et le centre de données de Microsoft de destination est exécuté sur le réseau de nuage Microsoft
  
**Figure 3 : Le nuage réseau Microsoft dans le monde entier**

![Réseau cloud mondial de Microsoft](images/Contoso_Poster/MS_WW_Cloud.png)
  
La Figure 3 montre le réseau cloud interconnecté de Microsoft pour les différentes régions du monde.
  
Avec ExpressRoute Premium, vous pouvez atteindre tous les centres de données Microsoft sur tous les continents à partir de n’importe quel emplacement d’homologation Microsoft situé sur un des continents. Le trafic entre les continents est réalisé sur le réseau cloud de Microsoft.
  
Basée sur l’analyse du trafic en cours et à venir pour les offres en nuage de Microsoft, Contoso a effectué une évaluation du réseau et mise en œuvre d’une connexion (basés sur MPLS) de ExpressRoute à tout pour accéder aux ressources d’Azure, avec l’homologation de privés et publics relations, à partir du siège social de Paris à l’emplacement d’homologation Microsoft en Europe.
  
Cette connexion apportera au service informatique de Contoso :
  
- Des performances cohérentes pour l’administration des applications Azure PaaS réparties
    
    Tous les développeurs d’applications et de l ' infrastructure informatique de Contoso administrateurs sont dans le campus de Paris. Avec les applications Azure PaaS distribuées aux différents centres de données Azure dans le monde entier, Contoso a besoin de performances cohérentes à partir du campus de Paris pour gérer les applications et leurs ressources de stockage, qui se composent de To de documents.
    
- Des performances cohérentes pour l’administration des serveurs dans Azure IaaS
    
    Les administrateurs du centre de données de Contoso se trouvent dans le campus de Paris et les serveurs pour être déployé dans Azure sont une extension du centre de données de Paris. Contoso a besoin de performances cohérentes vers ces nouveaux serveurs pour accéder aux applications héritées et le stockage d’archivage et de traitement de fin de trimestre.
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Chemin d’accès de Contoso cloud la disponibilité du réseau

Contoso a établi la procédure suivante pour préparer son réseau au cloud de Microsoft :
  
1. Optimiser les ordinateurs des employés pour l’accès Internet
    
    Les ordinateurs individuels sont vérifiés pour assurer que les ressources les plus récentes (pile TCP/IP, navigateur, pilotes de carte réseau, mises à jour de sécurité et du système d’exploitation) sont bien installées.
    
2. Analyser l’utilisation de la connexion Internet dans chaque bureau et apporter des ressources supplémentaires selon les besoins
    
    Chaque bureau est analysée pour l’utilisation d’Internet en cours et augmente la bande passante de la liaison réseau étendu si fonctionne sur 70 % ou au-dessus de l’utilisation.
    
3. Analyser les systèmes DMZ dans chaque bureau pour des performances optimales
    
    Une analyse des pare-feu, IDS et autres systèmes connectés à Internet a lieu pour garantir des performances optimales. Les serveurs proxy sont mis à jour ou à niveau selon les besoins.
    
4. Ajouter ExpressRoute au site parisien
    
    Offre un accès cohérent aux ressources Azure pour administrer les charges de travail Azure PaaS et IaaS.
    
5. Créer et tester un profil Azure Traffic Manager pour les applications Azure PaaS
    
    Tester un profil Azure Traffic Manager utilisant la méthode de routage des performances afin d’expérimenter la répartition du trafic Internet vers les sites régionaux.
    
6. Réserver de l’espace d’adresses privées pour Azure VNets
    
    Se baser sur les chiffres des serveurs à court terme et long terme planifiés dans Azure IaaS pour réserver l’espace d’adressage privé aux réseaux virtuels Azure et à leurs sous-réseaux.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)



