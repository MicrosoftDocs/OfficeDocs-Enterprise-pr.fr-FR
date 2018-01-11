---
title: "Présentation de la société Contoso Corporation"
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
description: "Résumé : Comprendre la société Contoso sous la forme d’une entreprise et la structure à plusieurs niveaux de ses bureaux dans le monde entier."
ms.openlocfilehash: c00e7fd75f580b82f8f920b9f74551a5e5e1b328
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Présentation de la société Contoso Corporation

 **Résumé :** Comprendre la société Contoso sous la forme d’une entreprise et la structure à plusieurs niveaux de ses bureaux dans le monde entier.
  
Contoso Corporation est une entreprise internationale dont le siège social se situe à Paris. La société Contoso Corporation est un conglomérat spécialisé dans la production, la vente et le support technique, qui propose plus de 100 000 produits.  
  
## <a name="the-contoso-corporation"></a>Société Contoso

Organisation de partout dans le monde de Contoso possède des bureaux dans les emplacements suivants :
  
**Figure 1 : Les bureaux de Contoso dans le monde**

![Bureaux de la société Contoso dans le monde entier](images/Contoso_Poster/Contoso_WW_Org.png)

  
Dans la Figure 1, le siège social de l’entreprise se situe à Paris, tandis que ses centres régionaux et ses succursales sont répartis sur plusieurs continents.
  
Les bureaux de Contoso dans le monde suivent un modèle à trois niveaux.
  
- Siège social
    
    Le siège social de Contoso Corporation est un site d’entreprise de grande taille sur les outskirts de Paris avec des dizaines de bâtiments pour les installations d’administration, d’ingénierie et de fabrication. Tous les centres de données de Contoso et sa présence sur Internet sont placés dans le siège social de Paris.
    
    Le siège social compte 15 000 collaborateurs.
    
- Centres régionaux
    
    Les centres régionaux sont implantés dans différentes régions du monde et possèdent 60 % des équipes des ventes et du support technique. Chaque centre régional est relié au siège social grâce à une connexion WAN haut débit.  
    
    Chaque centre régional compte en moyenne 2 000 collaborateurs.
    
- Succursales
    
    Bureaux satellites contenir 80 % des ventes et personnel de support technique et fournit une présence physique et sur site pour les clients de Contoso dans les principales villes ou sous-secteurs. Chaque bureau satellite est connecté à un concentrateur régionaux avec une liaison de réseau étendu à bande passante élevée.
    
    Chaque succursale compte en moyenne 250 collaborateurs.
    
25 % de la main de œuvre de Contoso est mobile uniquement, avec un pourcentage plus élevé des travailleurs mobiles uniquement dans les concentrateurs régionaux et les bureaux satellites. Fournir une meilleure assistance pour les travailleurs mobiles uniquement est un objectif important pour Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Éléments de mise en oeuvre de Contoso de Microsoft cloud

Contoso architectes informatiques ont identifié les éléments suivants lors de la planification pour l’adoption des offres en nuage de Microsoft.
  
- Réseau
    
    Mise en réseau inclut la connectivité à bande passante suffisante pour être performant dans les charges de pointe et les offres en nuage de Microsoft. Une connectivité sera via des connexions Internet locales et d’autres au sein de l’infrastructure de réseau privé de Contoso.
    
    Pour plus d’informations, consultez l’affiche [Microsoft Cloud Networking pour Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identité
    
    Contoso utilise une forêt Active Directory de Windows Server pour son fournisseur d’identité interne et également se fédère avec des fournisseurs tiers pour les clients et partenaires. Contoso doit exploiter l’ensemble interne des comptes pour les offres en nuage de Microsoft. Accès aux applications basées sur le cloud pour les clients et les partenaires doivent tirer parti de fournisseurs d’identité tiers ainsi.
    
    Pour plus d’informations, reportez-vous à l’affiche de [l’Identité de Cloud Microsoft pour Enterprise Architects](microsoft-cloud-identity-for-enterprise-architects.md) .
    
- Sécurité
    
    La sécurité des identités et des données dans le cloud doit inclure la protection des données, la gestion des privilèges administratifs, la sensibilisation aux menaces et l’implémentation de stratégies de gouvernance et de sécurité des données.
    
    Pour plus d’informations, reportez-vous à l’affiche de la [Sécurité de Cloud Microsoft pour Enterprise Architects](http://aka.ms/cloudarchsecurity) .
    
- Gestion
    
    La gestion des applications et des charges de travail SaaS dans le cloud doit inclure la mise à jour des paramètres, des données, des comptes, des stratégies et des autorisations et la surveillance continue des performances et de l’intégrité du serveur. Les outils de gestion de serveur existants servent à gérer les machines virtuelles dans Azure IaaS.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)
 


