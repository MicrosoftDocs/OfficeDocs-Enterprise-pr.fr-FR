---
title: Éléments courants de connectivité du cloud Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Résumé : Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau."
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068110"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Éléments communs de la connectivité au cloud Microsoft

 **Résumé :** Comprendre les éléments communs d'infrastructure réseau et comment préparer votre réseau.
  
L’intégration de votre réseau avec le cloud Microsoft fournit un accès optimal à une large gamme de services.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Étapes pour préparer votre réseau pour les services cloud de Microsoft
<a name="steps"> </a>

Pour votre réseau local, procédez comme suit :
  
1. Analysez les ordinateurs de vos clients et optimisez le matériel réseau, les pilotes logiciels, les paramètres du protocole et les navigateurs Internet.
    
2. Analysez votre réseau local pour la latence du trafic et le routage optimal vers le périphérique du périmètre Internet.
    
3. Analysez la capacité et les performances du périphérique du périmètre Internet et optimisez les niveaux supérieurs de trafic.
    
Pour votre connexion Internet, procédez comme suit :
  
1. Analysez la latence entre le périphérique du périmètre Internet (par exemple, votre pare-feu externe) et les emplacements régionaux du service cloud de Microsoft auquel vous vous connectez.
    
2. Analysez la capacité et l’utilisation de votre connexion Internet actuelle et augmentez la capacité si nécessaire. Vous pouvez également ajouter une connexion ExpressRoute.
    
## <a name="microsoft-cloud-connectivity-options"></a>Options de connectivité au cloud de Microsoft
<a name="steps"> </a>

Utilisez votre canal Internet existant ou une connexion ExpressRoute à Office 365, Azure et Dynamics 365.
  
**Figure 1 : Options pour la connectivité cloud Microsoft**

![Figure 1 :  options pour la connectivité cloud Microsoft](media/Network-Poster/CommonElements.png)

  
La figure 1 indique la façon dont un réseau local peut être connecté aux offres de cloud de Microsoft à l’aide de son canal Internet existant ou d’ExpressRoute. Le canal Internet représente une zone DMZ et peut avoir les composants suivants :
  
- **Pare-feu interne :** Barrière entre votre réseau approuvé et un réseau non approuvé. Effectue le filtrage (en fonction des règles) et la surveillance du trafic.
    
- **Charge de travail externe :** Sites web ou autres charges de travail mis à la disposition des utilisateurs externes sur Internet.
    
- **Serveur proxy :** Demandes de services pour le contenu web au nom des utilisateurs de l'intranet. Un proxy inverse autorise les demandes entrantes non sollicitées.
    
- **Pare-feu externe :** Autorise le trafic sortant et le trafic entrant spécifié. Peut effectuer la traduction d’adresse, l’inspection de paquets, l’interruption et l’inspection de SSL, ou la protection contre la perte de données.
    
- **Connexion WAN à ISP :** Connexion basée sur un opérateur à un fournisseur de services Internet, qui est homologuée avec Internet pour la connectivité et le routage.
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>Zones de réseau communes à tous les services cloud de Microsoft
<a name="steps"> </a>

Vous devez prendre en considération ces zones de réseau lors de l’adoption des services cloud de Microsoft.
  
- **Performances intranet :** Les performances des ressources basées sur Internet seront réduites si votre intranet, y compris les ordinateurs des clients, n'est pas optimisé.
    
- **Périphériques du périmètre :** Les périphériques dans le périmètre de votre réseau sont des points de sortie et peuvent inclure des traducteurs d'adresses réseau (NAT), des serveurs proxy (y compris les proxys inverses), des pare-feux, des périphériques de détection des intrusions ou une combinaison.
    
- **Connexion à Internet :** Votre connexion WAN à votre fournisseur de services Internet et Internet doivent avoir une capacité suffisante pour gérer les charges de pointe. Vous pouvez également utiliser une connexion ExpressRoute.
    
- **Internet DNS :** A, AAAA, CNAME, MX, PTR et les autres enregistrements pour localiser le cloud de Microsoft ou les services hébergés dans le cloud. Par exemple, vous pouvez avoir besoin d’un enregistrement CNAME pour votre application hébergée dans Azure PaaS.
    

## <a name="next-step"></a>Étape suivante

[ExpressRoute pour la connectivité au cloud de Microsoft](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>Voir aussi

<a name="steps"> </a>

[Mise en réseau cloud Microsoft pour les architectes d'entreprise](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressources relatives à l’architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)


