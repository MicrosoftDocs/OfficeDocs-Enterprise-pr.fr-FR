---
title: Identité de Contoso Corporation
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
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: 'Résumé : Découvrez comment Contoso tire parti des IDaaS distribué géographiquement et fournit l’authentification redondante pour ses utilisateurs.'
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915439"
---
# <a name="identity-for-the-contoso-corporation"></a>Identité de Contoso Corporation

 **Résumé :** Comprendre comment Contoso tire parti des IDaaS distribué géographiquement et fournit l’authentification redondante pour ses utilisateurs.
  
Microsoft propose une identité en tant que Service (IDaaS) parmi les offres de cloud. Pour adopter une infrastructure cloud-inclus, la solution de IDaaS de Contoso doit tirer parti de leur fournisseur d’identité locale et inclure l’authentification fédérée avec leurs fournisseurs d’identité tiers approuvé existant.
  
## <a name="contosos-windows-server-ad-forest"></a>Forêt de Windows Server AD de Contoso

Contoso utilise une seule forêt Windows Server Active Directory (AD) pour contoso.com et sept domaines (un par région). Le siège social, les centres régionaux et les succursales disposent de contrôleurs de domaine pour l’authentification locale et l’autorisation.

  
**Figure 1 : forêt et domaines de Contoso dans le monde**

![Domaines et forêt Windows Server AD dans le monde entier de Contoso](media/Contoso-Poster/Contoso-WW-ID.png)
  
La Figure 1 présente la forêt et les domaines régionaux de Contoso dans les régions du monde où se trouvent des centres régionaux.
  
Contoso souhaite utiliser les comptes et les groupes de la forêt contoso.com pour faciliter l’authentification et l’autorisation de ses applications et de ses charges de travail dans le cloud.
  
## <a name="contosos-federated-authentication-infrastructure"></a>Infrastructure d’authentification fédéré de Contoso

Contoso autorise les éléments suivants :
 



  
- Les clients ont le droit d’utiliser leurs comptes Microsoft, Facebook ou Google Mail pour se connecter à leur site web public.
    
- Les fournisseurs et les partenaires peuvent utiliser leurs comptes LinkedIn, Salesforce ou Google Mail pour se connecter à l’extranet des partenaires.
    
**Figure 2 : prise en charge de l’authentification fédérée par Contoso pour ses clients et ses partenaires**

![Infrastructure existante de Contoso pour prendre en charge l’authentification fédérée des clients et partenaires](media/Contoso-Poster/Federated-ID.png)
  
La Figure 2 montre que le DMZ de Contoso comprend un site web public, un partenaire extranet et des serveurs AD FS. Le DMZ est connecté à Internet, qui contient des clients, des partenaires et des services Internet.
  
Les serveurs AD FS du DMZ utilisent leurs informations d’identification client pour se connecter au site web public et leurs informations d’identification partenaire pour accéder à l’extranet des partenaires.
  
Lorsque Contoso passe son site web public à un Azure Web App et les partenaires extranet à Dynamics 365, qu’ils souhaitent continuer à utiliser ces fournisseurs d’identité tiers pour les clients et les partenaires. Il sera effectué en configurant la fédération entre clients Contoso Azure AD et ces fournisseurs d’identité tiers.
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Synchronisation d’annuaires pour la forêt de Windows Server AD de Contoso

Contoso a déployé l’outil Azure AD se connecter sur un cluster de serveurs dans son centre de données Paris. Azure AD Connect synchronise les modifications apportées à la forêt Windows Server AD contoso.com avec le client Azure AD partagé par Office 365, EMS, Dynamics 365 et Azure abonnements de Contoso. Pour plus d’informations sur les abonnements, licences, les comptes d’utilisateurs et les clients, voir [abonnements, les licences et les comptes d’utilisateurs pour la société Contoso](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).
  
**Figure 3 : infrastructure de synchronisation d’annuaires de Contoso**

![Infrastructure de synchronisation d’annuaires de Contoso](media/Contoso-Poster/DirSync.png)
  
La Figure 3 montre un cluster de serveurs exécutant Azure AD Connect qui synchronise la forêt Windows Server AD de Contoso avec le client Azure AD.
  
Contoso a configuré l’authentification fédérée, qui fournit de l’authentification unique pour les travailleurs de Contoso. Lorsqu’un utilisateur qui a déjà connecté à la forêt Windows Server AD contoso.com accède à une ressource de cloud Microsoft SaaS ou PaaS, ils ne demandera un mot de passe.
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Répartition géographique du trafic d’authentification de Contoso

Pour mieux accompagner ses collaborateurs mobiles et distants, Contoso a déployé des serveurs d’authentification dans ses bureaux régionaux. Cette infrastructure répartit la charge et fournit une redondance et de meilleures performances lors de l’authentification des informations d’identification utilisateur pour accéder aux offres cloud de Microsoft utilisant le locataire Azure AD commun.

  
Pour répartir la charge des demandes d’authentification, Contoso a configuré Azure Traffic Manager avec un profil qui utilise la méthode de routage des performances qui fait référence aux clients qui s’authentifient auprès de l’ensemble de serveurs régionaux le plus proche.  
  
**Figure 4 : répartition géographique du trafic d’authentification des bureaux régionaux**

![Répartition géographique du trafic d’authentification des bureaux régionaux de Contoso](media/Contoso-Poster/Auth-GeoDist.png)
  
La Figure 4 illustre les couches des ordinateurs clients et d’Azure Traffic Manager et des serveurs d’authentification des succursales. Chaque succursale utilise des proxys web et des serveurs AD FS pour authentifier les informations d’identification des utilisateurs avec les contrôleurs de domaine Windows Server AD.
  
Exemple de processus d’authentification :
  
1. L’ordinateur client établit une communication avec une page web du client Office 365 en Europe (par exemple, sharepoint.contoso.com).



    
2. Office 365 renvoie une demande de preuve d’authentification. La requête contient l’URL à contacter pour l’authentification.
    
3. L’ordinateur client tente d’associer le nom DNS de l’URL à une adresse IP existante.
    
4. Azure Traffic Manager reçoit la requête DNS et répond à l’ordinateur client avec l’adresse IP d’un serveur proxy d’applications web dans la succursale la plus proche de l’ordinateur client.
    
5.   L’ordinateur client envoie une demande d’authentification à un serveur proxy d’applications web qui transfère les demandes à un serveur AD FS.




    
6. Le serveur AD FS demande les informations d’identification depuis l’ordinateur client.
    
7. L’ordinateur client envoie les données d’identification de l’utilisateur sans les demander à celui-ci.
    
8. Le serveur AD FS valide les informations d’identification à l’aide d’un contrôleur de domaine Windows Server AD dans la succursale et renvoie un jeton de sécurité à l’ordinateur client.
    
9. L’ordinateur client envoie le jeton de sécurité à Office 365.
    
10. Une fois la validation réussie, Office 365 met le jeton de sécurité dans le cache et envoie à l’ordinateur client la page web demandée à l’étape 1.
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Redondance de l’infrastructure d’authentification du siège social dans Azure IaaS

Pour assurer la redondance des 15 000 collaborateurs distants et mobiles du siège social parisien, Contoso a déployé un second ensemble de proxys d’applications et de serveurs AD FS dans Azure IaaS.

  
**Figure 5 : infrastructure d’authentification redondante dans Azure IaaS**

![Infrastructure d’authentification redondante dans les services Azure IaaS pour le siège social de Paris](media/Contoso-Poster/Paris-Auth-Redun.png)
  
La Figure 5 montre les proxys web et les serveurs AD FS du DMZ et les autres proxys web et serveurs AD FS du réseau virtuel Azure intersites.
  
Lorsque les serveurs d’authentification principaux du DMZ du siège deviennent indisponibles, le service informatique bascule vers l’infrastructure redondante déployée dans Azure IaaS. Les demandes d’authentification suivantes envoyées depuis les ordinateurs du siège parisien utilisent l’infrastructure d’Azure IaaS jusqu’à ce que le problème de disponibilité soit résolu.
  
Pour basculer vers les serveurs de secours et revenir aux serveurs principaux, Contoso met à jour le profil Azure Traffic Manager associé au site parisien afin d’utiliser un autre ensemble d’adresses IP pour les proxys d’applications web :
  
- Lorsque les serveurs d’authentification du DMZ sont disponibles, les adresses IP des serveurs dans la zone du DMZ sont utilisées.

    
- Lorsque les serveurs d’authentification du DMZ ne sont pas disponibles, les adresses IP des serveurs dans Azure IaaS sont utilisées.
    
## <a name="see-also"></a>See Also

[Contoso dans le cloud de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Identité cloud Microsoft pour les architectes d’entreprise](http://aka.ms/cloudarchidentity)
  
[Protection des appareils et de l’identité pour Office 365](http://aka.ms/o365protect_device)
  
[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)




