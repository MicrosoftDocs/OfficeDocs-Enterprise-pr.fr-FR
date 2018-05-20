---
title: Présentation de la société Contoso Corporation
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
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: 'Résumé : Découvrez la société Contoso comme une entreprise et la structure à plusieurs niveaux de ses bureaux dans le monde entier.'
ms.openlocfilehash: 30a6dd23271fbbd5599053b934e6a1af9dc14d12
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Présentation de la société Contoso Corporation

 **Résumé :** Comprendre la société Contoso comme une entreprise et la structure à plusieurs niveaux de ses bureaux dans le monde entier.
  
Contoso Corporation est une entreprise internationale dont le siège social se situe à Paris. La société Contoso Corporation est un conglomérat spécialisé dans la production, la vente et le support technique, qui propose plus de 100 000 produits.  
  
## <a name="the-contoso-corporation"></a>Société Contoso

Organisation mondiale de Contoso a des bureaux dans les emplacements suivants :
  
**La figure 1 : Bureaux de Contoso**

![Bureaux de la société Contoso dans le monde entier](images/Contoso_Poster/Contoso_WW_Org.png)

  
Dans la Figure 1, le siège social de l’entreprise se situe à Paris, tandis que ses centres régionaux et ses succursales sont répartis sur plusieurs continents.
  
Bureaux de Contoso dans le monde suivez un modèle à trois niveaux.
  
- Siège social
    
    Le sièges sociaux Contoso Corporation est un site d’entreprise de grande taille sur les outskirts de Paris avec des dizaines de bâtiments pour les installations de fabrication, ingénieries et d’administration. Tous les centres de données de Contoso et sa présence sur Internet sont hébergées dans le siège social Paris.
    
    Le siège social compte 15 000 collaborateurs.
    
- Centres régionaux
    
    Les centres régionaux sont implantés dans différentes régions du monde et possèdent 60 % des équipes des ventes et du support technique. Chaque centre régional est relié au siège social grâce à une connexion WAN haut débit.  
    
    Chaque centre régional compte en moyenne 2 000 collaborateurs.
    
- Succursales
    
    Filiales contient 80 % des ventes et personnel de support technique et fournissent une présence physique et sur site pour les clients de Contoso de clé villes ou régions secondaire. Chaque bureau satellite est connecté à un concentrateur régionaux avec un lien de réseau étendu à bande passante élevée.
    
    Chaque succursale compte en moyenne 250 collaborateurs.
    
25 % des ressources de Contoso est mobile uniquement, avec un pourcentage plus élevé des travailleurs mobiles uniquement dans les bureaux régionaux. Fourniture meilleure prise en charge pour les travailleurs mobiles uniquement est un objectif important pour Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Éléments de mise en œuvre de Contoso Microsoft cloud

Contoso architectes informatiques ont identifié les éléments suivants lors de la planification de l’adoption des offres de cloud de Microsoft.
  
- Réseau
    
    Mise en réseau inclut la connectivité aux offres de cloud de Microsoft et suffisamment de bande passante pour être performant sous les charges maximales. Certains connectivité sera via des connexions Internet locales et certaines seront entre l’infrastructure de réseau privé de Contoso.
    
    Pour plus d’informations, voir le poster de [Mise en réseau de Microsoft dans le nuage pour les architectes de l’entreprise](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identité
    
    Contoso utilise une forêt Windows Server AD pour son fournisseur d’identité interne et se fédère également avec des fournisseurs tiers pour les clients et partenaires. Contoso doit tirer parti de l’ensemble des comptes pour les offres de cloud de Microsoft interne. Accès aux applications basées sur le nuage pour les clients et partenaires doivent tirer parti de fournisseurs d’identité tiers ainsi.
    
    Pour plus d’informations, voir l’affiche [Identité de nuage de Microsoft pour les architectes de l’entreprise](microsoft-cloud-it-architecture-resources.md#identity) .
    
- Sécurité
    
    La sécurité des identités et des données dans le cloud doit inclure la protection des données, la gestion des privilèges administratifs, la sensibilisation aux menaces et l’implémentation de stratégies de gouvernance et de sécurité des données.
    
    Pour plus d’informations, voir le poster de [Sécurité du Cloud Microsoft pour les architectes de l’entreprise](http://aka.ms/cloudarchsecurity) .
    
- Gestion
    
    La gestion des applications et des charges de travail SaaS dans le cloud doit inclure la mise à jour des paramètres, des données, des comptes, des stratégies et des autorisations et la surveillance continue des performances et de l’intégrité du serveur. Les outils de gestion de serveur existants servent à gérer les machines virtuelles dans Azure IaaS.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)

 


