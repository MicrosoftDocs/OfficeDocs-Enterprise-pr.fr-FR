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
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="b8a05-103">Identité de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="b8a05-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="b8a05-104">**Résumé :** Comprendre comment Contoso tire parti des IDaaS distribué géographiquement et fournit l’authentification redondante pour ses utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b8a05-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="b8a05-p101">Microsoft propose une identité en tant que Service (IDaaS) parmi les offres de cloud. Pour adopter une infrastructure cloud-inclus, la solution de IDaaS de Contoso doit tirer parti de leur fournisseur d’identité locale et inclure l’authentification fédérée avec leurs fournisseurs d’identité tiers approuvé existant.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="b8a05-107">Forêt de Windows Server AD de Contoso</span><span class="sxs-lookup"><span data-stu-id="b8a05-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b8a05-p102">Contoso utilise une seule forêt Windows Server Active Directory (AD) pour contoso.com et sept domaines (un par région). Le siège social, les centres régionaux et les succursales disposent de contrôleurs de domaine pour l’authentification locale et l’autorisation.
</span><span class="sxs-lookup"><span data-stu-id="b8a05-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="b8a05-110">**Figure 1 : forêt et domaines de Contoso dans le monde**</span><span class="sxs-lookup"><span data-stu-id="b8a05-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Domaines et forêt Windows Server AD dans le monde entier de Contoso](media/Contoso-Poster/Contoso-WW-ID.png)
  
<span data-ttu-id="b8a05-112">La Figure 1 présente la forêt et les domaines régionaux de Contoso dans les régions du monde où se trouvent des centres régionaux.</span><span class="sxs-lookup"><span data-stu-id="b8a05-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="b8a05-113">Contoso souhaite utiliser les comptes et les groupes de la forêt contoso.com pour faciliter l’authentification et l’autorisation de ses applications et de ses charges de travail dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="b8a05-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="b8a05-114">Infrastructure d’authentification fédéré de Contoso</span><span class="sxs-lookup"><span data-stu-id="b8a05-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="b8a05-115">Contoso autorise les éléments suivants :
 


</span><span class="sxs-lookup"><span data-stu-id="b8a05-115">Contoso allows:</span></span>
  
- <span data-ttu-id="b8a05-116">Les clients ont le droit d’utiliser leurs comptes Microsoft, Facebook ou Google Mail pour se connecter à leur site web public.</span><span class="sxs-lookup"><span data-stu-id="b8a05-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="b8a05-117">Les fournisseurs et les partenaires peuvent utiliser leurs comptes LinkedIn, Salesforce ou Google Mail pour se connecter à l’extranet des partenaires.</span><span class="sxs-lookup"><span data-stu-id="b8a05-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="b8a05-118">**Figure 2 : prise en charge de l’authentification fédérée par Contoso pour ses clients et ses partenaires**</span><span class="sxs-lookup"><span data-stu-id="b8a05-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Infrastructure existante de Contoso pour prendre en charge l’authentification fédérée des clients et partenaires](media/Contoso-Poster/Federated-ID.png)
  
<span data-ttu-id="b8a05-p103">La Figure 2 montre que le DMZ de Contoso comprend un site web public, un partenaire extranet et des serveurs AD FS. Le DMZ est connecté à Internet, qui contient des clients, des partenaires et des services Internet.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="b8a05-122">Les serveurs AD FS du DMZ utilisent leurs informations d’identification client pour se connecter au site web public et leurs informations d’identification partenaire pour accéder à l’extranet des partenaires.</span><span class="sxs-lookup"><span data-stu-id="b8a05-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="b8a05-p104">Lorsque Contoso passe son site web public à un Azure Web App et les partenaires extranet à Dynamics 365, qu’ils souhaitent continuer à utiliser ces fournisseurs d’identité tiers pour les clients et les partenaires. Il sera effectué en configurant la fédération entre clients Contoso Azure AD et ces fournisseurs d’identité tiers.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="b8a05-125">Synchronisation d’annuaires pour la forêt de Windows Server AD de Contoso</span><span class="sxs-lookup"><span data-stu-id="b8a05-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b8a05-p105">Contoso a déployé l’outil Azure AD se connecter sur un cluster de serveurs dans son centre de données Paris. Azure AD Connect synchronise les modifications apportées à la forêt Windows Server AD contoso.com avec le client Azure AD partagé par Office 365, EMS, Dynamics 365 et Azure abonnements de Contoso. Pour plus d’informations sur les abonnements, licences, les comptes d’utilisateurs et les clients, voir [abonnements, les licences et les comptes d’utilisateurs pour la société Contoso](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span><span class="sxs-lookup"><span data-stu-id="b8a05-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="b8a05-129">**Figure 3 : infrastructure de synchronisation d’annuaires de Contoso**</span><span class="sxs-lookup"><span data-stu-id="b8a05-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Infrastructure de synchronisation d’annuaires de Contoso](media/Contoso-Poster/DirSync.png)
  
<span data-ttu-id="b8a05-131">La Figure 3 montre un cluster de serveurs exécutant Azure AD Connect qui synchronise la forêt Windows Server AD de Contoso avec le client Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b8a05-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="b8a05-p106">Contoso a configuré l’authentification fédérée, qui fournit de l’authentification unique pour les travailleurs de Contoso. Lorsqu’un utilisateur qui a déjà connecté à la forêt Windows Server AD contoso.com accède à une ressource de cloud Microsoft SaaS ou PaaS, ils ne demandera un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="b8a05-134">Répartition géographique du trafic d’authentification de Contoso</span><span class="sxs-lookup"><span data-stu-id="b8a05-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="b8a05-p107">Pour mieux accompagner ses collaborateurs mobiles et distants, Contoso a déployé des serveurs d’authentification dans ses bureaux régionaux. Cette infrastructure répartit la charge et fournit une redondance et de meilleures performances lors de l’authentification des informations d’identification utilisateur pour accéder aux offres cloud de Microsoft utilisant le locataire Azure AD commun.
</span><span class="sxs-lookup"><span data-stu-id="b8a05-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="b8a05-137">Pour répartir la charge des demandes d’authentification, Contoso a configuré Azure Traffic Manager avec un profil qui utilise la méthode de routage des performances qui fait référence aux clients qui s’authentifient auprès de l’ensemble de serveurs régionaux le plus proche. </span><span class="sxs-lookup"><span data-stu-id="b8a05-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="b8a05-138">**Figure 4 : répartition géographique du trafic d’authentification des bureaux régionaux**</span><span class="sxs-lookup"><span data-stu-id="b8a05-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Répartition géographique du trafic d’authentification des bureaux régionaux de Contoso](media/Contoso-Poster/Auth-GeoDist.png)
  
<span data-ttu-id="b8a05-p108">La Figure 4 illustre les couches des ordinateurs clients et d’Azure Traffic Manager et des serveurs d’authentification des succursales. Chaque succursale utilise des proxys web et des serveurs AD FS pour authentifier les informations d’identification des utilisateurs avec les contrôleurs de domaine Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="b8a05-142">Exemple de processus d’authentification :</span><span class="sxs-lookup"><span data-stu-id="b8a05-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="b8a05-143">L’ordinateur client établit une communication avec une page web du client Office 365 en Europe (par exemple, sharepoint.contoso.com).


</span><span class="sxs-lookup"><span data-stu-id="b8a05-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="b8a05-p109">Office 365 renvoie une demande de preuve d’authentification. La requête contient l’URL à contacter pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="b8a05-146">L’ordinateur client tente d’associer le nom DNS de l’URL à une adresse IP existante.</span><span class="sxs-lookup"><span data-stu-id="b8a05-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="b8a05-147">Azure Traffic Manager reçoit la requête DNS et répond à l’ordinateur client avec l’adresse IP d’un serveur proxy d’applications web dans la succursale la plus proche de l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b8a05-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="b8a05-148"> L’ordinateur client envoie une demande d’authentification à un serveur proxy d’applications web qui transfère les demandes à un serveur AD FS.



</span><span class="sxs-lookup"><span data-stu-id="b8a05-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="b8a05-149">Le serveur AD FS demande les informations d’identification depuis l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b8a05-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="b8a05-150">L’ordinateur client envoie les données d’identification de l’utilisateur sans les demander à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b8a05-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="b8a05-151">Le serveur AD FS valide les informations d’identification à l’aide d’un contrôleur de domaine Windows Server AD dans la succursale et renvoie un jeton de sécurité à l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b8a05-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="b8a05-152">L’ordinateur client envoie le jeton de sécurité à Office 365.</span><span class="sxs-lookup"><span data-stu-id="b8a05-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="b8a05-153">Une fois la validation réussie, Office 365 met le jeton de sécurité dans le cache et envoie à l’ordinateur client la page web demandée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="b8a05-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="b8a05-154">Redondance de l’infrastructure d’authentification du siège social dans Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="b8a05-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="b8a05-155">Pour assurer la redondance des 15 000 collaborateurs distants et mobiles du siège social parisien, Contoso a déployé un second ensemble de proxys d’applications et de serveurs AD FS dans Azure IaaS.
</span><span class="sxs-lookup"><span data-stu-id="b8a05-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="b8a05-156">**Figure 5 : infrastructure d’authentification redondante dans Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="b8a05-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![Infrastructure d’authentification redondante dans les services Azure IaaS pour le siège social de Paris](media/Contoso-Poster/Paris-Auth-Redun.png)
  
<span data-ttu-id="b8a05-158">La Figure 5 montre les proxys web et les serveurs AD FS du DMZ et les autres proxys web et serveurs AD FS du réseau virtuel Azure intersites.</span><span class="sxs-lookup"><span data-stu-id="b8a05-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="b8a05-p110">Lorsque les serveurs d’authentification principaux du DMZ du siège deviennent indisponibles, le service informatique bascule vers l’infrastructure redondante déployée dans Azure IaaS. Les demandes d’authentification suivantes envoyées depuis les ordinateurs du siège parisien utilisent l’infrastructure d’Azure IaaS jusqu’à ce que le problème de disponibilité soit résolu.</span><span class="sxs-lookup"><span data-stu-id="b8a05-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="b8a05-161">Pour basculer vers les serveurs de secours et revenir aux serveurs principaux, Contoso met à jour le profil Azure Traffic Manager associé au site parisien afin d’utiliser un autre ensemble d’adresses IP pour les proxys d’applications web :</span><span class="sxs-lookup"><span data-stu-id="b8a05-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="b8a05-162">Lorsque les serveurs d’authentification du DMZ sont disponibles, les adresses IP des serveurs dans la zone du DMZ sont utilisées.
</span><span class="sxs-lookup"><span data-stu-id="b8a05-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="b8a05-163">Lorsque les serveurs d’authentification du DMZ ne sont pas disponibles, les adresses IP des serveurs dans Azure IaaS sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="b8a05-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b8a05-164">See Also</span><span class="sxs-lookup"><span data-stu-id="b8a05-164">See Also</span></span>

[<span data-ttu-id="b8a05-165">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8a05-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="b8a05-166">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b8a05-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b8a05-167">Identité cloud Microsoft pour les architectes d’entreprise</span><span class="sxs-lookup"><span data-stu-id="b8a05-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="b8a05-168">Protection des appareils et de l’identité pour Office 365</span><span class="sxs-lookup"><span data-stu-id="b8a05-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
<span data-ttu-id="b8a05-169">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)
</span><span class="sxs-lookup"><span data-stu-id="b8a05-169">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



