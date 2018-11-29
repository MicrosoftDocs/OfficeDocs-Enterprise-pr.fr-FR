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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872265"
---
# <a name="designing-networking-for-microsoft-saas"></a>Conception de réseaux pour Microsoft SaaS

 **Résumé :** Comprendre comment optimiser votre réseau pour accéder aux services SaaS de Microsoft, notamment Office 365, Microsoft Intune et Dynamics 365.
  
Optimisation de votre réseau pour les services Microsoft SaaS requiert la configuration d’interne et les routeurs pour acheminer les différentes catégories de trafic aux services Microsoft SaaS.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Étapes pour préparer votre réseau aux services SaaS de Microsoft

Procédez comme suit pour optimiser votre réseau pour les services SaaS de Microsoft :
  
1. Consultez les **étapes de préparation de votre réseau pour services de cloud Microsoft** fournies dans la section [Éléments communs de la connectivité au cloud Microsoft](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Ajouter une connexion Internet à chacun de vos sites.
    
3. Vérifiez que le fournisseur de services pour toutes les connexions Internet utilisez un serveur DNS avec une adresse IP locale.
    
4. Examinez votre épingles à cheveux du réseau, les destinations intermédiaires tels que les services de sécurité en nuage et les éliminer la mesure du possible.
    
5. Configurer vos périphériques edge pour contourner le traitement de l’optimiser et autoriser des catégories de trafic SaaS Microsoft.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimisation du trafic aux SaaS services de Microsoft    

Il existe trois catégories de trafic SaaS Microsoft :

- Optimiser

  Requis pour la connectivité à tous les services Microsoft SaaS et représentent plus de 75 % de la bande passante Microsoft SaaS, des connexions et le volume de données.

- Autoriser

  Requis pour la connectivité au spécifique SaaS Microsoft services et fonctionnalités mais ne sont pas soumis à des performances du réseau et la latence en tant que ceux de la catégorie d’optimisation.

- Par défaut

  Représentent SaaS Microsoft services et les dépendances qui ne nécessitent pas de n’importe quel optimisation. Vous pouvez traiter le trafic de catégorie par défaut comme le trafic Internet normal.


**La figure 1 : Configuration recommandée pour le trafic de tous les bureaux Microsoft SaaS**

![La figure 1 : Configuration recommandée pour le trafic de tous les bureaux Microsoft SaaS](media/Network-Poster/SaaS1.png)

La figure 1 illustre la configuration recommandée de toutes les succursales, y compris les agences et celles qui sont locaux ou centrale, dans laquelle :

- Catégorie **par défaut** et général le trafic Internet est routé vers des bureaux qui ont des serveurs proxy et autres périphériques edge pour assurer la protection contre les risques de sécurité basé sur Internet.
- **Optimiser** et **Autoriser** le trafic de catégorie est transféré directement vers le bord de Microsoft réseau front-end plus proche de l’office contenant l’utilisateur connecté, sans passer par les serveurs proxy et autres périphériques de périphérie.

Défini par le logiciel à l’échelle (WAN SD) périphériques réseau dans les succursales séparent le trafic afin que : 

- Catégorie **par défaut** et général du trafic Internet accède à un bureau central ou régional via le réseau WAN principal. 
- **Optimiser** et **Autoriser** le trafic de catégorie atteint le fournisseur de services fournissant la connexion Internet locale.
  
Pour plus d'informations, voir :
  
- [Principes de la connectivité réseau](https://aka.ms/expressrouteoffice365)

- [Planification réseau et de migration pour Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Étape suivante

[Conception de réseau pour Microsoft Azure PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Voir aussi

[Mise en réseau cloud Microsoft pour les architectes d’entreprise](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressources relatives à l’architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

