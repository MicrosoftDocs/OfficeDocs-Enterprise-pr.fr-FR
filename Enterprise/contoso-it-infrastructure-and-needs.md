---
title: Infrastructure et besoins informatiques de Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Résumé : Comprendre la structure de base de l'infrastructure informatique locale de Contoso et les besoins pouvant être satisfaits par les offres cloud de Microsoft."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a>Infrastructure et besoins informatiques de Contoso

 **Résumé :** Comprendre la structure de base de l'infrastructure informatique locale de Contoso et les besoins pouvant être satisfaits par les offres cloud de Microsoft.
  
Contoso passe actuellement d'une infrastructure informatique centralisée locale à une infrastructure cloud incluant des charges de travail de productivité et des applications basées sur le cloud, ainsi que des scénarios hybrides.
  
## <a name="contosos-existing-it-infrastructure"></a>Infrastructure informatique existante de Contoso

Contoso utilise une infrastructure informatique locale centralisée avec des centres de données situés au siège social parisien.
  
**Figure 1 : infrastructure informatique existante de Contoso**

![Infrastructure informatique existante de Contoso](images/Contoso_Poster/Existing_IT.png)
  
La Figure 1 présente le siège social avec les centres de données d'applications, un DMZ et Internet.
  
Dans le DMZ de Contoso, les différents groupes de serveurs fournissent les éléments suivants :
  
- Accès à distance à l'intranet et au proxy web de Contoso pour les collaborateurs présents au siège social parisien.
    
- Hébergement du site web public de Contoso à partir duquel les clients peuvent commander des produits, des composants ou des fournitures.
    
- Hébergement de l'extranet des partenaires de Contoso pour la collaboration et la communication avec les partenaires.
    
## <a name="contosos-business-needs"></a>Besoins de Contoso

Voici les besoins de Contoso par ordre de priorité :
  
1. Respecter les exigences réglementaires locales
    
    Pour éviter les amendes et entretenir de bonnes relations avec les autorités locales, Contoso doit respecter les réglementations en matière de stockage et de chiffrement des données.
    
2. Améliorer la gestion des partenaires et des fournisseurs
    
    L'extranet des partenaires est obsolescent et coûteux à mettre à jour. Contoso souhaite le remplacer par une solution cloud qui utilise l'authentification fédérée.
    
3. Améliorer la productivité des collaborateurs mobiles, la gestion et les accès des appareils
    
    Étant donné le nombre croissant de collaborateurs mobiles chez Contoso, une stratégie efficace de gestion des périphériques doit être mise en œuvre pour garantir la protection de la propriété intellectuelle et un meilleur accès aux ressources.
    
4. Réduire l'infrastructure d'accès distant
    
    En plaçant dans le cloud les ressources couramment utilisées par les collaborateurs distants, Contoso réalisera des économies sur les coûts destinés à la maintenance et l'assistance de leur solution d'accès distant.
    
5. Réduire la taille des centres de données locaux
    
    Les centres de données Contoso possèdent des centaines de serveurs, certains d'entre eux exécutent des fonctions héritées ou d'archivage qui empêchent le service informatique de gérer des charges de travail à haute valeur ajoutée.
    
6. Augmenter les ressources de calcul et de stockage pour le traitement de fin de trimestre
    
    La comptabilité financière et le traitement des projections de fin de trimestre ainsi que la gestion des stocks nécessitent une augmentation ponctuelle des charges de stockage et des charges serveur.
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Mappage des besoins commerciaux de Contoso aux offres cloud de Microsoft

Après analyse des offres cloud de Microsoft, le service informatique de Contoso a établi le mappage suivant :
  
|**Software as a Service (SaaS)**|**Platform as a Service (Azure PaaS )**|**Infrastructure as a Service (Azure IaaS )**|
|:-----|:-----|:-----|
|**Office 365 :** Applications principales de productivité personnelle et de groupe dans le cloud. <br/> Besoins commerciaux : 1 3 5  <br/> |Héberger les documents des services des ventes et du support technique ainsi que les systèmes d'informations à l'aide d'applications cloud.  <br/> Besoin commercial : 3  <br/> |Déplacer les systèmes d'archivage et hérités vers les serveurs cloud.  <br/> Besoin commercial : 5  <br/> |
|**Dynamics 365 :** Utiliser la gestion des clients et des fournisseurs sur le cloud. Supprimer un partenaire extranet dans DMZ.<br/> Besoin commercial : 2  <br/> |Les applications mobiles sont dans le cloud, et pas dans le centre de données parisien.  <br/> Besoins commerciaux : 3 4  <br/> |Migrer les applications et les données peu utilisées en dehors des centres de données locaux.  <br/> Besoin commercial : 5  <br/> |
|**Intune/EMS :** Gérer les appareils iOS et Android. <br/> Besoin commercial : 3  <br/> ||Ajouter des serveurs et de l'espace de stockage temporaires pour les besoins de traitement de fin de trimestre.  <br/> Besoin commercial : 6  <br/> |
   
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)


