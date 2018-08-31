---
title: Abonnements, licences et comptes d’utilisateur de Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Résumé : Comprendre la structure des abonnements de cloud de Contoso, licences, des comptes d’utilisateurs et des clients.'
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915509"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Abonnements, licences et comptes d’utilisateur de Contoso Corporation

 **Résumé :** Comprendre la structure des abonnements de cloud de Contoso, licences, des comptes d’utilisateurs et des clients.
  
Pour une utilisation cohérente des identités et de la facturation au sein de ses offres cloud, Microsoft fournit une hiérarchie d’organisation/d’abonnements/de licences/de comptes d’utilisateur :
  
- Organisation
    
    Entité commerciale qui utilise les offres cloud de Microsoft et qui est généralement identifiée par un nom de domaine DNS public, par exemple contoso.com.
    
- Abonnements
    
    SaaS Microsoft cloud offres (Office 365, Intune/EMS et Dynamics 365), un abonnement est un produit spécifique et un ensemble acheté des licences utilisateur. Pour Azure, un abonnement permet de facturation des services en nuage consommés à l’organisation.
    
- Licences
    
    Pour les offres de cloud Microsoft SaaS, une licence permet à un compte d’utilisateur spécifique à utiliser les services en nuage. Pour Azure, les licences logicielles sont créées dans le service de tarification, mais dans certains cas, que vous devez acquérir des licences logicielles supplémentaires.
    
- Comptes d’utilisateur
    
    Les comptes d’utilisateur sont stockés dans un client Azure AD et peuvent être synchronisés à partir d’un fournisseur d’identités local, tel que Windows Server AD.
    
## <a name="contosos-structure"></a>Structure de Contoso

Contoso a établi la structure d’organisation, d’abonnements, de licences, de comptes et de clients suivante :
  
**Figure 1 : organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso**

![Organisation, abonnements, licences, comptes d’utilisateur et clients de Contoso](media/Contoso-Poster/Subscriptions.png)
  
La Figure 1 montre comment l’organisation Contoso inclut plusieurs abonnements et est liée à un client Azure AD commun qui contient les comptes d’utilisateurs synchronisés à partir de la forêt Windows Server AD contoso.com.
  
- **Organisation** La société Contoso est identifiée par son nom de domaine de public contoso.com.
    
  - **Abonnements et licences** La société Contoso utilise les éléments suivants :
    
  - Le produit Office 365 entreprise E3 avec 5 000 licences
    
  - Produit Office 365 Entreprise E5 avec 200 licences
    
  - Le produit EMS avec 5 000 licences
    
  - Produit Dynamic 365 avec 100 licences

    
  - Abonnements Azure multiples en fonction des régions
    
  - **Comptes d’utilisateurs** Un client Azure AD common contient la liste des comptes d’utilisateurs et les groupes utilisés par tous les abonnements de Contoso, à l’exception de développement/test abonnements Azure.
    
Pour les clients de Contoso :
  
- Dans le cadre des offres cloud SaaS, le client désigne l’emplacement régional qui héberge les serveurs fournissant des services cloud. Contoso a choisi la région Europe pour héberger ses clients Office 365, EMS et Dynamics 365.
  
    
- Services PaaS Azure et les applications et les charges de travail informatique IaaS peuvent avoir location dans les centres de données Azure dans le monde entier. Un client Azure AD est une instance spécifique d’Azure Active Directory contenant les comptes et groupes.
    
- Le client Azure AD courants qui contient les comptes synchronisés pour la forêt Contoso Windows Server AD assure IDaaS entre les offres de cloud de Microsoft.
    
Pour plus d’informations, voir [abonnements, licences et des comptes et clients pour les offres de cloud de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
  
## <a name="contosos-azure-subscriptions"></a>Abonnements Azure de Contoso

La Figure 2 présente la structure hiérarchique des abonnements Azure de Contoso : 



  
**Figure 2 : structure des abonnements Azure de Contoso**

![Structure des abonnements Azure de Contoso](media/Contoso-Poster/Subscriptions-Nested.png)
  
- Contoso est prioritaire, conformément à l’Accord Entreprise conclu avec Microsoft.
    
- Il existe un ensemble de comptes correspondant aux différentes régions de la société Contoso dans le monde, basée sur les domaines de la forêt de Windows Server AD de Contoso.
    
- Dans chaque région, il existe un ou plusieurs des abonnements en fonction des besoins de déploiement de développement, de test et de production de cette région.
    
Chaque abonnement Azure peut être associé à un même client Azure AD possédant des comptes et groupes d’utilisateurs pour l’authentification aux services Azure et les droits qui leur sont associés. Les abonnements de production utilisent le client Azure AD commun de Contoso.
  
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)





