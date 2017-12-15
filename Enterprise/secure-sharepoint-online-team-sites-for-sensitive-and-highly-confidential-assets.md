---
title: "Sécuriser les sites d'équipe SharePoint Online pour les ressources sensibles et hautement confidentielles"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/12/2017
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Résumé : Découvrez comment Contoso a mis en œuvre des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, afin de permettre une collaboration simple, mais sécurisée, entre ses centres de recherche et ses cadres."
---

# Sécuriser les sites d'équipe SharePoint Online pour les ressources sensibles et hautement confidentielles

 **Résumé :** Découvrez comment Contoso a mis en œuvre des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, afin de permettre une collaboration simple, mais sécurisée, entre ses centres de recherche et ses cadres.
  
Les cadres supérieurs de Contoso souhaitent utiliser Office 365 et stocker leurs fichiers dans un emplacement unique à des fins de collaboration, quel que soit l'endroit où ils sont susceptibles de se trouver. De même, les services de recherche de Contoso, qui comptent des départements à Paris, Moscou, New York, Beijing (Pékin) et Bengaluru (Bangalore), aimeraient faire passer leurs ressources numériques en local sur le cloud afin d'en faciliter l'accès et de permettre une collaboration plus ouverte entre les équipes.
  
Toutefois, dans les deux cas, l'accès à ces ressources doit être limité au sous-ensemble de personnes qui sont autorisées à les visualiser ou à les modifier, avec des autorisations permanentes pour le site géré par le service informatique. En outre, même si certaines ressources sont distribuées intentionnellement ou non, elles doivent être chiffrées et dotées d'autorisations pour empêcher les personnes qui ne disposent pas d'un accès de visualiser ou de modifier leur contenu.
  
Les administrateurs de la sécurité et de SharePoint au sein du service informatique de Contoso ont décidé d'utiliser des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles, comme illustré dans la figure 1.
  
**Figure 1 : Comparaison des sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles**

![Sites d'équipe SharePoint Online hautement confidentiels et avec protection des données sensibles](images/ed73bd84-47af-4a90-8b82-6adab9419b9a.png)
  
Contoso a créé des sites d'équipe SharePoint Online sécurisés pour ses cadres et ses équipes de recherche de la manière suivante :
  
1. Création d'un site d'équipe SharePoint Online sensible pour les **cadres**
    
    Le nouveau site d'équipe utilise des groupes Azure Active Directory (AD) existants pour les cadres en tant que membres avec le niveau d'autorisation Modifier SharePoint et un petit ensemble de comptes d'administrateur SharePoint en tant que propriétaires avec le niveau d'autorisation Contrôle total.
    
2. Migration des fichiers des cadres
    
    Les fichiers et dossiers des cadres existants en local sont déplacés vers le nouveau site d'équipe SharePoint Online pour les cadres.
    
3. Création d'un site d'équipe SharePoint Online hautement confidentiel pour la **recherche**
    
    Le nouveau site d'équipe utilise des groupes d'équipe de recherche Azure AD existants en tant que membres avec le niveau d'autorisation Modifier et un petit ensemble de comptes d'administrateur SharePoint en tant que propriétaires avec le niveau d'autorisation Contrôle total. Une étiquette AIP est affectée aux fichiers de recherche, ce qui permet de s'assurer qu'ils sont chiffrés et que seuls les membres d'un groupe de recherche peuvent les ouvrir.
    
4. Migration des fichiers de recherche
    
    Les fichiers et dossiers de recherche existants en local sont déplacés vers le nouveau site d'équipe SharePoint Online pour la recherche.
    
Le résultat consiste en deux sites de collaboration dont l'accès est étroitement contrôlé par les administrateurs de la sécurité et de SharePoint. Pour les fichiers dotés de l'étiquette AIP Hautement confidentiel, même s'ils sont distribués en dehors du site d'équipe pour la recherche, ils sont chiffrés et ne peuvent être ouverts que par un membre d'une équipe de recherche.
  
Pour plus d'informations, consultez l'article [Sécuriser des sites et des fichiers SharePoint Online](https://docs.microsoft.com/fr-fr/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).
  
 Pour effectuer cette configuration à des fins de démonstration, de preuve de concept ou de développement/test, consultez l'article[Sécuriser des sites SharePoint Online dans un environnement de développement et de test](https://docs.microsoft.com/fr-fr/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).
  
## See Also

#### 

[Scénarios d'entreprise pour la société Contoso](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Feuille de route de Microsoft Enterprise Cloud : Ressources pour les décideurs informatiques](https://sway.com/FJ2xsyWtkJc2taRD)

