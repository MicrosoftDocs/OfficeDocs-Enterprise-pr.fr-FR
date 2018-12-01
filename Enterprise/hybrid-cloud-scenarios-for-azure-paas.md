---
title: Scénarios de cloud hybride pour les services PaaS Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Résumé : Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure."
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123331"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Scénarios de cloud hybride pour les services PaaS Azure

 **Résumé :** Comprendre l'architecture hybride et les scénarios pour les offres cloud PaaS de Microsoft dans Azure.
  
Combinez des données locales ou des ressources de calcul à des applications nouvelles ou converties exécutées dans les services PaaS Azure. Vous pouvez ainsi tirer parti des performances, de la fiabilité et de la dimension du cloud tout en offrant une prise en charge optimale aux utilisateurs mobiles. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Architecture de scénario hybride pour les services PaaS Azure

La Figure 1 présente l’architecture des scénarios hybrides PaaS de Microsoft dans Azure.
  
**Figure 1 : Scénarios hybrides Microsoft PaaS dans Azure**

![Scénarios hybrides Microsoft PaaS dans Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Pour chaque couche de l’architecture :
  
- Applications et scénarios
    
    Une application PaaS hybride est exécutée dans Azure et utilise les ressources de calcul ou de stockage locales.
    
- Identity
    
    Se compose de la synchronisation d’annuaires ou de la fédération avec un fournisseur d’identité tiers.
    
- Réseau
    
    Se compose de votre canal Internet existant ou d'une connexion ExpressRoute avec homologation publique pour Azure PaaS. Vous devez inclure un moyen pour l'application Azure PaaS d'accéder à la ressource de calcul ou de stockage locale.
    
- Sur site
    
    Se compose d’une infrastructure d’identité et de sécurité et d’applications métier ou de serveurs de bases de données existants auxquels une application Azure PaaS peut accéder en toute sécurité.
    
## <a name="azure-paas-hybrid-application"></a>Application hybride Azure PaaS

La Figure 2 illustre la configuration d’une application hybride exécutée dans Azure.
  
**Figure 2 : Application hybride Azure PaaS**

![Application hybride Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
Dans la Figure 2, un réseau local héberge le stockage ou des applications sur des serveurs et une zone DMZ contenant un serveur proxy. Il est connecté à des services Azure PaaS via Internet ou avec une connexion ExpressRoute.
  
Une organisation peut mettre ses ressources de calcul ou de stockage à disposition de l’application Azure PaaS hybride :
  
- en hébergeant les ressources sur des serveurs dans la zone DMZ ;
    
- en hébergeant un serveur proxy inverse dans la zone DMZ, ce qui permet d’envoyer des requêtes HTTPS entrantes et authentifiées à la ressource locale.
    
L’application Azure peut utiliser les informations d’identification des sources suivantes :
  
- Azure AD. Elles peuvent alors être synchronisées avec votre fournisseur d’identité local, tel que Windows Server AD.
    
- Fournisseur d’identité tiers.
    
### <a name="example-azure-paas-hybrid-application"></a>Exemple d’application Azure PaaS hybride

La Figure 3 illustre un exemple d’application hybride exécutée dans Azure.
  
**Figure 3 : Exemple d'application hybride Azure PaaS**

![Exemple d’application hybride Azure PaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
Dans la Figure 3, un réseau local héberge une application métier. Azure PaaS héberge une application mobile personnalisée. Un smartphone sur Internet accède à l'application mobile personnalisée dans Azure, qui envoie des demandes de données à l'application métier locale.
  
Cet exemple d'application Azure PaaS hybride est une application mobile personnalisée qui propose des informations de contact à jour concernant les employés. Le scénario hybride de bout en bout se compose de :
  
- Un application pour smartphone qui, pour fonctionner, nécessite des informations d’identification locales et validées.
    
- Une application mobile personnalisée exécutée dans les services PaaS Azure, qui demande des informations concernant des employés spécifiques en fonction de requêtes envoyées par l'application pour smartphone d'un utilisateur.
    
- Un serveur proxy inverse dans la zone DMZ qui valide l’application mobile personnalisée et transfère la requête.
    
- Une batterie de serveurs d'applications métier qui gère la requête de contact. Elle est soumise aux autorisations du compte de l'utilisateur.
    
Étant donné que le fournisseur d'identité local a été synchronisé avec Azure AD, l'application mobile personnalisée et l'application métier peuvent valider le nom du compte de l'utilisateur qui envoie la requête.
  
## <a name="see-also"></a>Voir aussi

[Cloud hybride Microsoft pour les architectes d'entreprise](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

