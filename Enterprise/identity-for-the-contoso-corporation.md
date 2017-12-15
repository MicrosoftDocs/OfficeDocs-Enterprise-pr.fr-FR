---
title: "Identité de Contoso Corporation"
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
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Résumé : Comprendre comment Contoso tire parti des IDaaS distribué géographiquement et fournit l’authentification redondante pour ses utilisateurs."
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a>Identité de Contoso Corporation

 **Résumé :** Comprendre comment Contoso tire parti des IDaaS distribué géographiquement et fournit l’authentification redondante pour ses utilisateurs.
  
Microsoft fournit une identité en tant que Service (IDaaS) dans ses offres en nuage. Pour adopter une infrastructure cloud-inclus, solution de IDaaS de Contoso doit tirer parti de leur fournisseur d’identité sur site et inclure l’authentification fédérée avec leurs fournisseurs d’identité tiers approuvé existant.
  
## <a name="contosos-windows-server-ad-forest"></a>Forêt de Windows Server, Active Directory de Contoso

Contoso utilise une seule forêt de Windows Server Active Directory (AD) pour contoso.com avec sept domaines, un pour chaque région du monde. Le siège social, bureaux régionaux centralisés et bureaux satellites contiennent des contrôleurs de domaine pour l’authentification locale et d’autorisation.
  
**Figure 1 : De Contoso forêt et les domaines dans le monde entier**

![Domaines et forêt Windows Server AD dans le monde entier de Contoso](images/Contoso_Poster/Contoso_WW_ID.png)
  
La Figure 1 présente la forêt et les domaines régionaux de Contoso dans les régions du monde où se trouvent des centres régionaux.
  
Contoso souhaite utiliser les comptes et les groupes de la forêt contoso.com pour faciliter l’authentification et l’autorisation de ses applications et de ses charges de travail dans le cloud.
  
## <a name="contosos-federated-authentication-infrastructure"></a>Infrastructure d’authentification fédérée de Contoso

Contoso permet de :
  
- Les clients ont le droit d’utiliser leurs comptes Microsoft, Facebook ou Google Mail pour se connecter à leur site web public.
    
- Les fournisseurs et les partenaires peuvent utiliser leurs comptes LinkedIn, Salesforce ou Google Mail pour se connecter à l’extranet des partenaires.
    
**Figure 2 : L’authentification pour les clients et les partenaires fédérée prise en charge de Contoso**

![Infrastructure existante de Contoso pour prendre en charge l’authentification fédérée des clients et partenaires](images/Contoso_Poster/Federated_ID.png)
  
La Figure 2 montre que le DMZ de Contoso comprend un site web public, un partenaire extranet et des serveurs AD FS. Le DMZ est connecté à Internet, qui contient des clients, des partenaires et des services Internet.
  
Les serveurs AD FS du DMZ utilisent leurs informations d’identification client pour se connecter au site web public et leurs informations d’identification partenaire pour accéder à l’extranet des partenaires.
  
Lorsque Contoso passe son site web public pour un Azure Web App et les partenaires extranet à Dynamics 365, ils veulent continuer à utiliser ces fournisseurs d’identité tiers pour leurs clients et leurs partenaires. Cela sera effectué en configurant la fédération entre les locataires Contoso AD Azure et ces fournisseurs d’identité tiers.
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Synchronisation d’annuaire de la forêt de Windows Server, Active Directory de Contoso

Contoso a déployé l’outil Azure Connect de publicité sur un cluster de serveurs dans son centre de données de Paris. Azure Connect de publicité synchronise les modifications apportées à la forêt Active Directory de Windows Server de contoso.com avec le locataire AD Azure partagé par Office 365, EMS, Dynamics 365 et abonnements Azure de Contoso. Pour plus d’informations sur les abonnements, les licences, les comptes d’utilisateurs et les locataires, consultez [abonnements, des licences et des comptes d’utilisateurs pour la société Contoso](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).
  
**Figure 3 : Infrastructure de synchronisation d’annuaire de Contoso**

![Infrastructure de synchronisation d’annuaires de Contoso](images/Contoso_Poster/DirSync.png)
  
La Figure 3 montre un cluster de serveurs exécutant Azure AD Connect qui synchronise la forêt Windows Server AD de Contoso avec le client Azure AD.
  
Contoso a configuré l’authentification fédérée, qui offre une ouverture de session unique pour les employés de Contoso. Lorsqu’un utilisateur est déjà connecté à la forêt Active Directory de Windows Server de contoso.com accède à une ressource de cloud Microsoft SaaS ou PaaS, ils ne demandera un mot de passe.
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Répartition géographique du trafic d’authentification de Contoso

Pour mieux prendre en charge ses employés mobiles et distants, Contoso a déployé des ensembles de serveurs d’authentification dans ses bureaux régionaux. Cette infrastructure distribue la charge et fournit la redondance et des performances supérieures lors de l’authentification des informations d’identification de l’utilisateur pour accéder aux offres de nuage de Microsoft qui utilisent le locataire AD Azure commun.
  
Pour répartir la charge des demandes d’authentification, Contoso a configuré Azure Traffic Manager avec un profil qui utilise la méthode de routage des performances qui fait référence aux clients qui s’authentifient auprès de l’ensemble de serveurs régionaux le plus proche.  
  
**Figure 4 : La répartition géographique du trafic d’authentification pour les bureaux régionaux**

![Répartition géographique du trafic d’authentification des bureaux régionaux de Contoso](images/Contoso_Poster/Auth_GeoDist.png)
  
La Figure 4 illustre les couches des ordinateurs clients et d’Azure Traffic Manager et des serveurs d’authentification des succursales. Chaque succursale utilise des proxys web et des serveurs AD FS pour authentifier les informations d’identification des utilisateurs avec les contrôleurs de domaine Windows Server AD.
  
Exemple de processus d’authentification :
  
1. L’ordinateur client établit une communication avec une page web dans la location d’Office 365 en Europe (par exemple, sharepoint.contoso.com).
    
2. Office 365 renvoie une demande de preuve d’authentification. La requête contient l’URL à contacter pour l’authentification.
    
3. L’ordinateur client tente d’associer le nom DNS de l’URL à une adresse IP existante.
    
4. Azure Traffic Manager reçoit la requête DNS et répond à l’ordinateur client avec l’adresse IP d’un serveur proxy d’applications web dans la succursale la plus proche de l’ordinateur client.
    
5.  L’ordinateur client envoie une demande d’authentification à un serveur proxy web application qui transmet la demande à un serveur ADFS.
    
6. Le serveur AD FS demande les informations d’identification depuis l’ordinateur client.
    
7. L’ordinateur client envoie les données d’identification de l’utilisateur sans les demander à celui-ci.
    
8. Le serveur AD FS valide les informations d’identification à l’aide d’un contrôleur de domaine Windows Server AD dans la succursale et renvoie un jeton de sécurité à l’ordinateur client.
    
9. L’ordinateur client envoie le jeton de sécurité à Office 365.
    
10. Une fois la validation réussie, Office 365 met le jeton de sécurité dans le cache et envoie à l’ordinateur client la page web demandée à l’étape 1.
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Redondance de l’infrastructure d’authentification du siège social dans Azure IaaS

Pour assurer la redondance pour les travailleurs mobiles et à distance, le siège de Paris contenant 15 000 travailleurs, Contoso a déployé un second ensemble de proxys d’applications et de serveurs AD FS dans Azure IaaS.
  
**Figure 5 : Infrastructure d’authentification redondante Azure IaaS**

![Infrastructure d’authentification redondante dans les services Azure IaaS pour le siège social de Paris](images/Contoso_Poster/Paris_Auth_Redun.png)
  
La Figure 5 montre les proxys web et les serveurs AD FS du DMZ et les autres proxys web et serveurs AD FS du réseau virtuel Azure intersites.
  
Lorsque les serveurs d’authentification principaux du DMZ du siège deviennent indisponibles, le service informatique bascule vers l’infrastructure redondante déployée dans Azure IaaS. Les demandes d’authentification suivantes envoyées depuis les ordinateurs du siège parisien utilisent l’infrastructure d’Azure IaaS jusqu’à ce que le problème de disponibilité soit résolu.
  
Pour basculer vers les serveurs de secours et revenir aux serveurs principaux, Contoso met à jour le profil Azure Traffic Manager associé au site parisien afin d’utiliser un autre ensemble d’adresses IP pour les proxys d’applications web :
  
- Lorsque les serveurs d’authentification de DMZ sont disponibles, utilisez les adresses IP des serveurs de la zone DMZ.
    
- Lorsque les serveurs d’authentification du DMZ ne sont pas disponibles, les adresses IP des serveurs dans Azure IaaS sont utilisées.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Identité de Cloud Microsoft pour Enterprise Architects](http://aka.ms/cloudarchidentity)
  
[Identité et Protection des périphériques pour Office 365](http://aka.ms/o365protect_device)
  
[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs](https://sway.com/FJ2xsyWtkJc2taRD)



