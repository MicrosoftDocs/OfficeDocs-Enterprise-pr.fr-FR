---
title: "Conception de réseau pour Microsoft Azure PaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/10/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "Résumé : Comprenez comment optimiser votre réseau pour accéder à Microsoft Azure PaaS."
---

# Conception de réseau pour Microsoft Azure PaaS

 **Résumé :** Comprenez comment optimiser votre réseau pour accéder à Microsoft Azure PaaS.
  
L'optimisation du réseau pour les applications Azure PaaS requiert une bande passante Internet appropriée et peut nécessiter la distribution du trafic réseau sur plusieurs sites ou applications.
  
## Étapes de planification pour l'hébergement des applications PaaS d'entreprise dans Azure

Insérez le corps de la section ici.
  
1. Consultez les **étapes de préparation de votre réseau pour services de cloud computing Microsoft** fournies dans[Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Optimisez votre bande passante Internet en suivant les étapes 2 à 4 de la **procédure de préparation de votre réseau pour les services Microsoft SaaS** fournie dans[Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md).
    
3. Déterminez si vous avez besoin d'une connexion ExpressRoute à Azure.
    
4. Pour les charges de travail basées sur Internet, déterminez si vous avez besoin d'Azure Application Gateway.
    
5. Pour distribuer le trafic sur différents points de terminaison dans divers centres de données, déterminez si vous avez besoin d'Azure Traffic Manager.
    
## Bande passante Internet pour les applications PaaS d'entreprise

Les applications d'entreprise hébergées dans Azure PaaS nécessitent une bande passante Internet pour les utilisateurs de l'intranet. Il existe deux options :
  
- **Option 1 :** utilisez votre canal existant, optimisé pour le trafic Internet avec la capacité à gérer les charges de pointe. Voir[Conception de réseaux pour Microsoft SaaS](designing-networking-for-microsoft-saas.md) pour le périmètre Internet, l'utilisation client et les considérations relatives aux opérations informatiques.
    
- **Option 2 :** pour une bande passante élevée ou des besoins de latence faible, utilisez une connexion ExpressRoute à Azure.
    
**Figure 1 : Options de connexion pour les services Azure PaaS**

![Figure 1 : options de connexion pour les services PaaS Azure](images/fe802311-8687-44a7-ad58-bdf55d901d8b.png)
  
La figure 1 montre une connexion du réseau local aux services Azure PaaS via un canal Internet ou ExpressRoute.
  
## Azure Application Gateway

Routage au niveau des applications et services d'équilibrage de charge vous permettant de générer un site web frontal évolutif et hautement disponible dans Azure pour les applications web, les services cloud et les machines virtuelles. 
  
**Figure 2 : Azure Application Gateway**

![Figure 2 : service Application Gateway d'Azure](images/69b3ce25-f1f1-46c8-8c02-4726d7a7b81c.png)
  
La figure 2 présente Azure Application Gateway et indique comment les demandes utilisateur provenant d'Internet peuvent être acheminées vers les applications web Azure, les services cloud ou les machines virtuelles.
  
Application Gateway prend actuellement en charge la remise d'application de couche 7 pour les éléments suivants :
  
- Équilibrage de charge HTTP
    
- Affinité de session basée sur les cookies
    
- Déchargement SSL
    
Pour plus d'informations, voir [Vue d'ensemble d'Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).
  
## Azure Traffic Manager

Distribution du trafic sur différents points de terminaison qui peuvent inclure des services cloud ou des applications web Azure situés dans différents centres de données ou points de terminaison externes.
  
Traffic Manager utilise les méthodes de routage suivantes :
  
- **Basculement :** les points de terminaison sont dans un ou plusieurs centres de données Azure et vous souhaitez utiliser un point de terminaison principal pour tout le trafic, mais vous fournissez des sauvegardes au cas où les points de terminaison de sauvegarde ou principal ne sont pas disponibles.
    
- **Tourniquet (round robin) :** vous souhaitez répartir la charge sur un ensemble de points de terminaison dans le même centre de données ou entre différents centres de données.
    
- **Performances :** vous avez des points de terminaison dans différentes zones géographiques et vous souhaitez demander aux clients d'utiliser le point de terminaison « le plus proche » pour la latence la plus faible.
    
Voici un exemple de trois applications web dispersées géographiquement.
  
**Figure 3 : Azure Traffic Manager**

![Figure 3 : Azure Traffic Manager](images/c8c6164b-670b-4638-be06-7be27c3e1997.png)
  
La figure 3 indique le processus simple utilisé par Traffic Manager pour acheminer les requêtes vers trois applications web Azure différentes aux États-Unis, en Europe et en Asie. Dans l'exemple :
  
1. Une requête DNS utilisateur pour une URL de site web est dirigée vers Azure Traffic Manager, qui renvoie le nom d'une application web régionale, selon la méthode de routage de performances.
    
2. L'utilisateur lance le trafic avec l'application web régionale en Europe.
    
Pour plus d'informations, voir [Vue d'ensemble de Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)
  
## See Also

#### 

[Mise en réseau cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Feuille de route Enterprise Cloud de Microsoft relative aux ressources pour les décideurs en matière d'informatique](https://sway.com/FJ2xsyWtkJc2taRD)

