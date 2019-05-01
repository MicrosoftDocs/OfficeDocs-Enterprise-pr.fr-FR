---
title: Conception de réseaux pour Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Résumé : Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487294"
---
# <a name="designing-networking-for-microsoft-saas"></a>Conception de réseaux pour Microsoft SaaS

 **Résumé :** Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.
  
L’optimisation de votre réseau pour les services SaaS de Microsoft requiert la configuration des équipements de périmètre et internes pour acheminer les différentes catégories de trafic vers les services SaaS de Microsoft.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Étapes pour préparer votre réseau aux services SaaS de Microsoft

Procédez comme suit pour optimiser votre réseau pour les services SaaS de Microsoft :
  
1. Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Ajoutez une connexion Internet à chacun de vos bureaux.
    
3. Assurez-vous que les fournisseurs de services Internet de toutes les connexions Internet utilisent un serveur DNS avec une adresse IP locale.
    
4. Examinez votre réseau les épingles, les destinations intermédiaires, telles que les services de sécurité en nuage, et supprimez-les si possible.
    
5. ConFigurez vos périphériques Edge pour qu'ils contournent le traitement pour les catégories Optimize et allow du trafic SaaS de Microsoft.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimisation du trafic vers les services SaaS de Microsoft    

Il existe trois catégories de trafic Microsoft SaaS:

- Optimiser

  Obligatoire pour la connectivité à chaque service SaaS de Microsoft et représente plus de 75% de la bande passante de Microsoft SaaS, des connexions et du volume de données.

- Autoriser

  Requis pour la connectivité à des services et des fonctionnalités Microsoft SaaS spécifiques, mais qui ne sont pas sensibles aux performances et à la latence du réseau comme ceux de la catégorie optimize.

- Par défaut

  Représentent les services et dépendances Microsoft SaaS qui ne nécessitent aucune optimisation. Vous pouvez traiter le trafic de catégorie par défaut comme le trafic Internet normal.


**Figure 1: configuration recommandée pour le trafic SaaS de Microsoft pour tous les bureaux**

![Figure 1: configuration recommandée pour le trafic SaaS de Microsoft pour tous les bureaux](media/Network-Poster/SaaS1.png)

La figure 1 présente la configuration recommandée de tous les bureaux, y compris les succursales, les succursales régionales ou centrales, dans lesquelles:

- La catégorie **par défaut** et le trafic Internet général sont acheminés vers les bureaux disposant de serveurs proxy et d'autres périphériques Edge pour fournir une protection contre les risques de sécurité Internet.
- **Optimiser** et **autoriser** le trafic de catégorie est transféré directement vers le serveur frontal le plus proche de l'extrémité du réseau Microsoft vers le bureau contenant l'utilisateur qui se connecte, en contournant les serveurs proxy et autres périphériques Edge.

Les périphériques SD-WAN (réseau étendu) définis par le logiciel dans les succursales séparent les éléments suivants: 

- La catégorie **par défaut** et le trafic Internet général sont acheminés vers un bureau central ou régional sur le réseau principal du réseau étendu. 
- **Optimiser** et **autoriser** le trafic de catégorie vers le fournisseur de services Internet fournissant la connexion Internet locale.
  
Pour plus d’informations, reportez-vous aux rubriques suivantes :
  
- [Principes de connectivité réseau](https://aka.ms/expressrouteoffice365)

- [Planification réseau et de migration pour Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Étape suivante

[Conception de réseau pour Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Voir aussi

[Mise en réseau cloud Microsoft pour les architectes d’entreprise](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressources relatives à l’architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

