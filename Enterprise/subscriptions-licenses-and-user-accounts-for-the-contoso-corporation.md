---
title: "Abonnements, licences et comptes d’utilisateur de Contoso Corporation"
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "Résumé : Comprendre la structure des abonnements de nuage de Contoso, les licences, les comptes utilisateur et les locataires."
ms.openlocfilehash: 6bc90d7b166d5e0983eac8ed47ba16bede57426d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Abonnements, licences et comptes d’utilisateur de Contoso Corporation

 **Résumé :** Comprendre la structure des abonnements de nuage de Contoso, les licences, les comptes utilisateur et les locataires.
  
Pour une utilisation cohérente des identités et de la facturation au sein de ses offres cloud, Microsoft fournit une hiérarchie d’organisation/d’abonnements/de licences/de comptes d’utilisateur :
  
- Organisation
    
    Entité commerciale qui utilise les offres cloud de Microsoft et qui est généralement identifiée par un nom de domaine DNS public, par exemple contoso.com.
    
- Abonnements
    
    Pour Microsoft SaaS (Office 365, Intune/EMS et Dynamics 365) les offres en nuage, un abonnement est un produit spécifique et un ensemble acheté des licences utilisateur. Pour Azure, permet à un abonnement pour la facturation des services en nuage consommés à l’organisation.
    
- Licences
    
    Pour les offres de cloud Microsoft SaaS, une licence permet à un compte d’utilisateur spécifique utiliser les services en nuage. Pour Azure, licences logicielles sont intégrées dans le prix du service, mais dans certains cas, que vous devez acquérir des licences logicielles supplémentaires.
    
- Comptes d’utilisateur
    
    Les comptes d’utilisateur sont stockés dans un client Azure AD et peuvent être synchronisés à partir d’un fournisseur d’identités local, tel que Windows Server AD.
    
## <a name="contosos-structure"></a>Structure de Contoso

Contoso a établi la structure d’organisation, d’abonnements, de licences, de comptes et de clients suivante :
  
**Figure 1 : Contoso organisation, abonnements, licences, comptes d’utilisateurs et locataires**

![Organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso](images/Contoso_Poster/Subscriptions.png)
  
La Figure 1 montre comment l’organisation Contoso inclut plusieurs abonnements et est liée à un client Azure AD commun qui contient les comptes d’utilisateurs synchronisés à partir de la forêt Windows Server AD contoso.com.
  
- **Organisation** La société Contoso est identifiée par son contoso.com de nom de domaine public.
    
  - **Abonnements et licences** La société Contoso utilise les éléments suivants :
    
  - Le produit Office 365 entreprise E3 avec 5 000 licences
    
  - Produit Office 365 Entreprise E5 avec 200 licences
    
  - Le produit EMS avec 5 000 licences
    
  - Le produit de Dynamics 365 avec 100 licences
    
  - Abonnements Azure multiples en fonction des régions
    
  - **Comptes d’utilisateurs** Un locataire AD Azure commun contient la liste des comptes d’utilisateurs et les groupes utilisés par tous les abonnements de Contoso, à l’exception de développement/test abonnements Azure.
    
Pour les clients de Contoso :
  
- Pour les offres de cloud SaaS, le locataire est l’emplacement régional qui héberge les serveurs fournissant des services de cloud. Contoso a choisi de la région Europe pour héberger ses locataires Office 365, EMS et Dynamics 365. 
    
- Les services PaaS Azure et les applications et les charges de travail IaaS informatique peuvent avoir location dans n’importe quel centre de données Azure dans le monde entier. Un locataire AD Azure est une instance spécifique de publicité Azure contenant les comptes et les groupes.
    
- Le locataire AD Azure commun qui contient les comptes synchronisés pour la forêt Contoso Windows Server Active Directory fournit des IDaaS entre les offres en nuage de Microsoft.
    
Pour plus d’informations, consultez [abonnements, des licences, des comptes et des locataires pour les offres en nuage de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
  
## <a name="contosos-azure-subscriptions"></a>Abonnements Azure de Contoso

La figure 2 illustre la structure hiérarchique des abonnements d’Azure de Contoso :
  
**Figure 2 : Structure de Contoso pour les abonnements Azure**

![Structure des abonnements Azure de Contoso](images/Contoso_Poster/Subscriptions_Nested.png)
  
- Contoso est prioritaire, conformément à l’Accord Entreprise conclu avec Microsoft.
    
- Il existe un ensemble de comptes correspondant à différentes régions de la société Contoso dans le monde entier, basée sur les domaines de la forêt de Windows Server, Active Directory de Contoso.
    
- Dans chaque région, il y a un ou plusieurs abonnements en fonction des besoins de déploiement de développement, de test et de production de cette région.
    
Chaque abonnement Azure peut être associé à un même client Azure AD possédant des comptes et groupes d’utilisateurs pour l’authentification aux services Azure et les droits qui leur sont associés. Les abonnements de production utilisent le client Azure AD commun de Contoso.
  
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)




