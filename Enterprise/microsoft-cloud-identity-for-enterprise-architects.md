---
title: "Identité cloud Microsoft pour les architectes d'entreprise"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Résumé : Concevez votre solution d'identité pour plateformes et services cloud Microsoft."
ms.openlocfilehash: f581711345b043d61de503360d101fbcc09de82e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="c624d-103">Identité cloud Microsoft pour les architectes d'entreprise</span><span class="sxs-lookup"><span data-stu-id="c624d-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="c624d-104">**Résumé :** Concevez votre solution d'identité pour plateformes et services cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c624d-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="c624d-p101">Cet article explique ce que les architectes informatiques doivent savoir sur la conception d'identité pour les organisations utilisant des plateformes et des services cloud Microsoft. Vous pouvez également afficher le contenu de cet article sous forme d'affiche à 5 pages et l'imprimer au format tabloïd (également appelé format comptable, 11 x 17 ou A3).</span><span class="sxs-lookup"><span data-stu-id="c624d-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="c624d-107">[![Image du curseur de défilement pour le modèle d’identité de Microsoft cloud](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="c624d-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="c624d-108">![Fichier PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Fichier Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Affichage d'une page contenant des versions dans d'autres langues](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Plus de langues](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="c624d-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="c624d-109">Vous pouvez également voir tous les modèles dans les [ressources d’architecture de Cloud de Microsoft IT](microsoft-cloud-it-architecture-resources.md) et faites par l’intermédiaire de [programme de nuage de Microsoft Enterprise : ressources pour les décideurs informatiques](https://aka.ms/cloudarchitecture).</span><span class="sxs-lookup"><span data-stu-id="c624d-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c624d-p102">Cet article indique la version de janvier 2016 de l’affiche de **l’identité de cloud Microsoft pour enterprise architects** . Il ne contient-elle pas les modifications pour le 2016 avril ou des versions ultérieures de l’affiche.</span><span class="sxs-lookup"><span data-stu-id="c624d-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="c624d-112">Conception d'identité pour le cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c624d-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="c624d-p103">L'intégration de vos identités avec le cloud Microsoft fournit un accès à un large éventail d'options de plateforme et de services cloud. Il existe deux options principales :</span><span class="sxs-lookup"><span data-stu-id="c624d-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="c624d-p104">Vous pouvez réaliser une intégration avec Microsoft Azure Active Directory (AD). Cette opération implique de synchroniser vos comptes locaux avec Azure Active Directory, le fournisseur d'identité pour le cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c624d-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="c624d-117">Vous pouvez étendre votre environnement de services de domaine Active Directory (AD DS) local vers des machines virtuelles exécutées dans les services d'infrastructure de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Options de création de vos identités dans le cloud](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="c624d-119">**Figure 1 : Options pour la création d'identités dans le cloud**</span><span class="sxs-lookup"><span data-stu-id="c624d-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="c624d-120">La figure 1 montre bien qu'Azure AD est le fournisseur d'identité pour les services Saas (Software as a Service - logiciel en tant que service) de Microsoft et les applications PaaS (Platform as a Service - plateforme en tant que service) et la façon dont les applications métier peuvent utiliser les services AD DS.</span><span class="sxs-lookup"><span data-stu-id="c624d-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="c624d-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c624d-121">Azure Active Directory</span></span>

<span data-ttu-id="c624d-p105">Microsoft Azure Active Directory est le service de gestion de l'accès et de l'identité hébergé sur le cloud de Microsoft. Il s'agit d'un outil central pour les plateformes et les services cloud de Microsoft. L'intégration à Azure Active Directory permet d'accéder à tous les services SaaS de Microsoft à l'aide de votre ensemble actuel de comptes et de mots de passe. Cette intégration fournit également une identité basée sur le cloud pour les applications PaaS Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="c624d-126">Même avec Azure AD, les services de domaine Active Directory en local restent nécessaires pour les entreprises ou les machines virtuelles utilisant Windows et exécutées dans l'IaaS (Infrastructure as a Service - infrastructure en tant que Service) Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="c624d-127">Il existe trois éditions d'Azure Active Directory : gratuite, de base et Premium.</span><span class="sxs-lookup"><span data-stu-id="c624d-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="c624d-128">**Gratuite**</span><span class="sxs-lookup"><span data-stu-id="c624d-128">**Free**</span></span> <br/> |<span data-ttu-id="c624d-129">**Basique**</span><span class="sxs-lookup"><span data-stu-id="c624d-129">**Basic**</span></span> <br/> |<span data-ttu-id="c624d-130">**Premium**</span><span class="sxs-lookup"><span data-stu-id="c624d-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="c624d-131">Gestion de comptes d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c624d-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="c624d-132">Synchronisation avec des répertoires locaux</span><span class="sxs-lookup"><span data-stu-id="c624d-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="c624d-133">Authentification unique pour Azure, Office 365 et des milliers d'autres applications SaaS populaires, telles que Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox et bien d'autres</span><span class="sxs-lookup"><span data-stu-id="c624d-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="c624d-134">Comprend toutes les fonctionnalités de l'édition gratuite, plus :</span><span class="sxs-lookup"><span data-stu-id="c624d-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="c624d-135">Insertion de la marque de votre entreprise</span><span class="sxs-lookup"><span data-stu-id="c624d-135">Company branding</span></span> <br/>  <span data-ttu-id="c624d-136">Accès aux applications par groupes</span><span class="sxs-lookup"><span data-stu-id="c624d-136">Group-based application access</span></span> <br/>  <span data-ttu-id="c624d-137">Réinitialisation du mot de passe en libre-service</span><span class="sxs-lookup"><span data-stu-id="c624d-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="c624d-138">Contrat de niveau de service entreprise de 99,9 %</span><span class="sxs-lookup"><span data-stu-id="c624d-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="c624d-139">Inclut toutes les fonctionnalités des éditions gratuite et de base, plus :</span><span class="sxs-lookup"><span data-stu-id="c624d-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="c624d-140">Gestion des groupes en libre-service</span><span class="sxs-lookup"><span data-stu-id="c624d-140">Self-service group management</span></span> <br/>  <span data-ttu-id="c624d-141">Alertes et rapports de sécurité avancés</span><span class="sxs-lookup"><span data-stu-id="c624d-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="c624d-142">Authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c624d-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="c624d-143">Réinitialisation du mot de passe avec écriture conditionnelle vers l'instance AD DS locale</span><span class="sxs-lookup"><span data-stu-id="c624d-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="c624d-144">Synchronisation bidirectionnelle avec l'outil Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="c624d-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="c624d-145">Proxy d'application Azure AD</span><span class="sxs-lookup"><span data-stu-id="c624d-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="c624d-146">Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="c624d-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="c624d-147">Pour plus d'informations sur les versions, voir [Éditions d'Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="c624d-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="c624d-148">Option 1 : intégration à Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c624d-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="c624d-p106">La plupart des organisations synchronisent un ensemble standard d'objets et d'attributs avec leur client Azure Active Directory. L'outil Azure AD Connect synchronise vos comptes entre votre instance AD DS locale et un client Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c624d-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Intégration à Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="c624d-152">**Figure 2 : Intégration à Azure AD**</span><span class="sxs-lookup"><span data-stu-id="c624d-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="c624d-p107">La figure 2 montre comment l'outil Azure AD Connect obtient les modifications apportées dans AD DS et les envoie à votre client Azure Active Directory. Dans ce cas, votre client Azure AD est une copie hébergée dans le cloud du contenu d'un répertoire local essentiel.</span><span class="sxs-lookup"><span data-stu-id="c624d-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="c624d-p108">De nombreuses organisations utilisent les services AD DS comme fournisseur d'identité local. Vous pouvez utiliser un autre type de fournisseur d'identité local (par exemple, avec le protocole LDAP) et effectuer une synchronisation vers Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c624d-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="c624d-157">Option 2 : extension des services AD DS à Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="c624d-p109">L'extension des services AD DS à des machines virtuelles exécutée dans les services d'infrastructure Azure prend en charge un ensemble de solutions et d'applications différent de la synchronisation avec Azure Active Directory. En voici deux :</span><span class="sxs-lookup"><span data-stu-id="c624d-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="c624d-160">Prend en charge des solutions cloud qui requièrent l'authentification Kerberos ou NTLM, ou des machines virtuelles jointes à un domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="c624d-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="c624d-161">Offre un plus grand potentiel d'intégration pour les applications et les services cloud sur les plateformes et services cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c624d-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Extension de AD DS à Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="c624d-163">**Figure 3 : Extension d'AD DS à Azure**</span><span class="sxs-lookup"><span data-stu-id="c624d-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="c624d-p110">La figure 3 présente un contrôleur de domaine AD DS connecté à un réseau virtuel Azure via un périphérique VPN local et une passerelle VPN Azure. Le réseau virtuel Azure contient des serveurs dédiés à une application métier, ainsi que son propre jeu de contrôleurs de domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="c624d-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="c624d-166">Plus d'informations</span><span class="sxs-lookup"><span data-stu-id="c624d-166">More Information</span></span>

- [<span data-ttu-id="c624d-167">Synchronizing your directory with Office 365 is easy</span><span class="sxs-lookup"><span data-stu-id="c624d-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="c624d-168">Infographie : Gestion des identités et des accès dans le cloud</span><span class="sxs-lookup"><span data-stu-id="c624d-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="c624d-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c624d-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="c624d-170">Intégrer vos comptes AD DS avec Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c624d-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="c624d-171">En synchronisant vos comptes AD DS locaux avec Azure Active Directory, vos utilisateurs peuvent les utiliser pour accéder à :</span><span class="sxs-lookup"><span data-stu-id="c624d-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="c624d-172">L'ensemble des services Saas Microsoft (Office 365, Microsoft Intune et Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="c624d-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="c624d-173">Vos applications exécutées dans la PaaS Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="c624d-174">Il existe deux façons de configurer cette intégration :</span><span class="sxs-lookup"><span data-stu-id="c624d-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="c624d-175">Synchronisation d'annuaire et de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c624d-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="c624d-176">Fédération et authentification unique</span><span class="sxs-lookup"><span data-stu-id="c624d-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="c624d-p111">Commencez par l'option la plus simple qui répond à vos besoins. Vous pouvez changer, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c624d-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c624d-179">L'utilisation de comptes exclusivement dédiés au cloud (qui ne s'intègrent pas avec votre instance AD DS locale) n'est pas recommandée pour les grandes organisations.</span><span class="sxs-lookup"><span data-stu-id="c624d-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="c624d-180">Synchronisation d'annuaire et de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c624d-180">Directory and password synchronization</span></span>

<span data-ttu-id="c624d-181">Cette option est la plus simple et requiert uniquement un serveur qui exécute l'outil Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c624d-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Configuration de la synchronisation d'annuaire et de mot de passe](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="c624d-183">**Figure 4 : Configuration de la synchronisation d'annuaire et de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="c624d-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="c624d-p112">La figure 4 présente un centre de données de cloud privé ou local avec un contrôleur de domaine AD DS. Un serveur qui exécute l'outil Azure AD Connect synchronise la liste des noms de compte avec Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c624d-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="c624d-186">Avec cette option :</span><span class="sxs-lookup"><span data-stu-id="c624d-186">With this option:</span></span>
  
- <span data-ttu-id="c624d-p113">Les comptes d'utilisateurs sont synchronisés de votre instance AD DS locale (ou d'un autre fournisseur d'identité) vers votre client Azure Active Directory. Le répertoire local reste la source de référence pour les comptes et vous gérez toutes les modifications apportées aux comptes à partir de cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="c624d-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="c624d-189">Azure AD exécute toutes les tâches d'authentification pour les services SaaS de Microsoft et les applications PaaS Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="c624d-190">Vous pouvez également configurer la synchronisation pour plusieurs forêts AD DS.</span><span class="sxs-lookup"><span data-stu-id="c624d-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="c624d-191">Avec la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c624d-191">With password synchronization:</span></span>
  
- <span data-ttu-id="c624d-192">Les utilisateurs sont invités à entrer un mot de passe lorsqu'ils accèdent aux services cloud, qui est le même mot de passe que pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="c624d-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="c624d-p114">Les mots de passe utilisateur ne sont jamais envoyés à Azure Active Directory sous forme de texte en clair. Un hachage du mot de passe est utilisé. Il est techniquement impossible de déchiffrer ou de reconstituer le hachage du mot de passe et d'obtenir ce dernier en texte clair.</span><span class="sxs-lookup"><span data-stu-id="c624d-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="c624d-196">Avec Multi-Factor Authentication (MFA) :</span><span class="sxs-lookup"><span data-stu-id="c624d-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="c624d-197">Vous pouvez utiliser les fonctionnalités MFA de base proposées par Office 365.</span><span class="sxs-lookup"><span data-stu-id="c624d-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="c624d-198">Les développeurs d'applications PaaS Azure peuvent tirer parti du service Multi-Factor Authentication Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="c624d-199">La synchronisation d'annuaire n'offre pas d'intégration avec les solutions MFA locales.</span><span class="sxs-lookup"><span data-stu-id="c624d-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="c624d-200">Fédération et authentification unique</span><span class="sxs-lookup"><span data-stu-id="c624d-200">Federation and single sign-on</span></span>

<span data-ttu-id="c624d-201">Cette option requiert une infrastructure et des serveurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c624d-201">This option requires additional servers and infrastructure.</span></span> 
  
![Serveurs requis pour l'authentification fédérée](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="c624d-203">**Figure 5 : Serveurs requis pour l'authentification fédérée**</span><span class="sxs-lookup"><span data-stu-id="c624d-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="c624d-p115">la figure 5 présente l'ensemble de composants nécessaires pour l'authentification fédérée. Azure AD contacte un proxy d'application web, qui transmet la demande d'authentification à un serveur Active Directory Federation Services (AD FS), qui transfère la demande à un contrôleur de domaine AD DS à des fins d'évaluation et de réponse. Un serveur qui exécute l'outil Azure AD Connect synchronise la liste des noms de comptes d'AD DS vers Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c624d-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="c624d-207">La fédération offre les fonctionnalités d'entreprise supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="c624d-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="c624d-208">Toutes les demandes d'authentification envoyées à Azure AD sont transférées à AD FS et soumises au fournisseur d'identité local via AD FS.</span><span class="sxs-lookup"><span data-stu-id="c624d-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="c624d-209">Fonctionne avec les fournisseurs d'identité autres que Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c624d-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="c624d-210">La synchronisation de hachage de mot de passe peut servir de sauvegarde de connexion pour la connexion fédérée (par exemple, si l'authentification fédérée échoue).</span><span class="sxs-lookup"><span data-stu-id="c624d-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="c624d-211">Utilisez la fédération dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c624d-211">Use federation if:</span></span>
  
- <span data-ttu-id="c624d-p116">L'authentification unique est requise. Avec l'authentification unique, les utilisateurs ne sont pas invités à entrer des informations d'identification (nom d'utilisateur ou mot de passe) lorsqu'ils accèdent à un service cloud.</span><span class="sxs-lookup"><span data-stu-id="c624d-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="c624d-214">AD FS est déjà déployé.</span><span class="sxs-lookup"><span data-stu-id="c624d-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="c624d-215">Vous utilisez un fournisseur d'identité tiers.</span><span class="sxs-lookup"><span data-stu-id="c624d-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="c624d-216">Vous utilisez Forefront Identity Manager 2010 R2 (ne prend pas en charge la synchronisation de hachage de mot de passe).</span><span class="sxs-lookup"><span data-stu-id="c624d-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="c624d-217">Vous disposez d'une carte à puce intégrée locale ou d'une autre solution MFA.</span><span class="sxs-lookup"><span data-stu-id="c624d-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="c624d-218">Vous devez réaliser des audits de connexion et/ou désactiver des comptes.</span><span class="sxs-lookup"><span data-stu-id="c624d-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="c624d-219">Votre organisation requiert des restrictions des connexions client par heures de travail ou emplacement réseau.</span><span class="sxs-lookup"><span data-stu-id="c624d-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="c624d-220">Vous devez vous conformer aux normes FIPS (Federal Information Processing Standards).</span><span class="sxs-lookup"><span data-stu-id="c624d-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="c624d-221">L'authentification fédérée nécessite un plus grand investissement dans l'infrastructure locale.</span><span class="sxs-lookup"><span data-stu-id="c624d-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="c624d-p117">Les serveurs locaux doivent être accessibles sur Internet via un pare-feu d'entreprise. Microsoft recommande d'utiliser des serveurs de proxy d'application web déployés dans votre réseau de périmètre.</span><span class="sxs-lookup"><span data-stu-id="c624d-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="c624d-224">Nécessite du matériel, des licences et des opérations pour les serveurs AD FS, des serveurs de proxy AD FS ou des serveurs proxy d'application web, des pare-feux et des programmes d'équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="c624d-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="c624d-225">La disponibilité et les performances sont importantes pour être sûr que les utilisateurs peuvent accéder à Office 365 et à d'autres applications cloud.</span><span class="sxs-lookup"><span data-stu-id="c624d-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="c624d-226">Plus d'informations</span><span class="sxs-lookup"><span data-stu-id="c624d-226">More Information</span></span>

- [<span data-ttu-id="c624d-227">Synchronizing your directory with Office 365 is easy</span><span class="sxs-lookup"><span data-stu-id="c624d-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="c624d-228">Préparer la mise en service des utilisateurs via la synchronisation d'annuaires vers Office 365</span><span class="sxs-lookup"><span data-stu-id="c624d-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="c624d-229">Multi-Factor Authentication pour Office 365</span><span class="sxs-lookup"><span data-stu-id="c624d-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="c624d-230">Azure Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="c624d-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="c624d-231">TechEd 2014 : Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c624d-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="c624d-232">Extension des services AD DS à Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="c624d-233">L'extension d'AD DS à Azure est la première étape pour la prise en charge d'applications métier exécutées sur des machines virtuelles dans les services d'infrastructure Azure, et fournit les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="c624d-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="c624d-234">Prise en charge des solutions cloud qui requièrent l'authentification Kerberos ou NTLM, ou des machines virtuelles jointes à un domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="c624d-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="c624d-235">Possibilités d'intégration supplémentaires pour les services et applications cloud, qui peuvent être ajoutées à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c624d-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Extension d'AD DS à un réseau virtuel Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="c624d-237">**Figure 6 : Extension d'AD DS à un réseau virtuel Azure**</span><span class="sxs-lookup"><span data-stu-id="c624d-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="c624d-p118">La figure 6 présente un centre de données de cloud privé ou local, avec AD DS connecté à un réseau virtuel Azure via une connexion ExpressRoute ou VPN de site à site. Le réseau virtuel Azure contient des serveurs dédiés à une application métier, ainsi que son propre jeu de contrôleurs de domaine AD DS. Cette configuration constitue un déploiement hybride d'AD DS en local et dans les services d'infrastructure Azure. Elle requiert :</span><span class="sxs-lookup"><span data-stu-id="c624d-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="c624d-242">Un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="c624d-243">Une connexion entre un routeur ou un périphérique de réseau privé virtuel (VPN) local et une passerelle VPN Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="c624d-244">L'utilisation d'une partie de votre espace d'adressage IP local pour les machines virtuelles du réseau virtuel.</span><span class="sxs-lookup"><span data-stu-id="c624d-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="c624d-245">Le déploiement d'un ou de plusieurs contrôleurs de domaine dans le réseau virtuel désignés comme serveurs de catalogue global (permet de réduire le trafic sortant sur la connexion VPN).</span><span class="sxs-lookup"><span data-stu-id="c624d-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="c624d-246">Cette architecture d'identité prend en charge un ensemble de solutions et d'applications différent de la synchronisation avec Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c624d-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="c624d-247">Options de connexion de l'environnement local vers Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="c624d-248">Pour connecter votre réseau local à un réseau virtuel Azure, vous pouvez utiliser les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c624d-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="c624d-249">Une connexion VPN de site à site, qui permet de connecter de 1 à 10 sites (y compris d'autres réseaux virtuels Azure) à un même réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="c624d-p119">ExpressRoute, une liaison de réseau étendu privée et sécurisée vers Azure, assurée par un fournisseur de services de réseau et de centre de données partenaire. Les connexions ExpressRoute permettent de bénéficier d'une plus grande fiabilité, d'une meilleure bande passante et de temps de latence inférieurs.</span><span class="sxs-lookup"><span data-stu-id="c624d-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="c624d-252">Plus d'informations</span><span class="sxs-lookup"><span data-stu-id="c624d-252">More Information</span></span>

- [<span data-ttu-id="c624d-253">À propos des connexions sécurisées entre locaux pour les réseaux virtuels</span><span class="sxs-lookup"><span data-stu-id="c624d-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="c624d-254">Présentation technique d'ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c624d-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="c624d-255">Recommandations en matière de déploiement de Windows Server Active Directory sur des machines virtuelles Windows Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="c624d-256">Intégration de vos applications avec des identités cloud</span><span class="sxs-lookup"><span data-stu-id="c624d-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="c624d-p120">Lorsque vous concevez et développez des applications destinées au cloud, vous devez mettre en place un processus d'authentification cohérent pour les utilisateurs, notamment concernant les informations d'identification requises. Par exemple, lorsque vous utilisez des informations d'identification Windows, que ce soit pour Azure Active Directory ou une instance AD DS étendue, veillez à ce que les utilisateurs puissent s'authentifier rapidement et se concentrer ainsi sur leurs tâches.</span><span class="sxs-lookup"><span data-stu-id="c624d-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Intégration de vos applications avec des identités cloud](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="c624d-260">**Figure 7 : Intégration des applications avec des identités cloud**</span><span class="sxs-lookup"><span data-stu-id="c624d-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="c624d-261">La figure 7 présente les trois options disponibles pour l'intégration de votre application avec des identités cloud.</span><span class="sxs-lookup"><span data-stu-id="c624d-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="c624d-262">Enregistrez vos applications hébergées dans le cloud auprès d'Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c624d-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="c624d-p121">Consultez l'article MSDN [Intégration d'applications dans Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Cette opération vous permet d'utiliser Azure Active Directory pour authentifier l'accès à votre application PaaS, ainsi que d'autoriser des utilisateurs ou des administrateurs à octroyer des droits sur votre application à d'autres utilisateurs afin que ces derniers puissent accéder à du contenu en leur nom à partir d'autres services cloud, comme, Office 365. Vous pouvez obtenir des détails supplémentaires et des exemples de code dans l'article MSDN [Scénarios d'authentification pour Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span><span class="sxs-lookup"><span data-stu-id="c624d-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="c624d-266">Les applications qui requièrent une authentification par programmation pour accéder à une application sécurisée par AD SD, AD FS sur Windows Server 2012 R2 ou Azure Active Directory peuvent utiliser les outils suivants :</span><span class="sxs-lookup"><span data-stu-id="c624d-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="c624d-267">L'[API Azure AD Graph](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="c624d-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="c624d-268">Active Directory Authentication Library (ADAL)</span><span class="sxs-lookup"><span data-stu-id="c624d-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="c624d-p122">L'API Azure AD Graph prend en charge OAuth et OpenID Connect. Elle fonctionne également avec les applications PaaS.</span><span class="sxs-lookup"><span data-stu-id="c624d-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="c624d-p123">Configurez des applications métier ou locales exécutées sur des machines virtuelles dans un réseau virtuel Azure pour utiliser l'authentification Windows (NTLM ou Kerberos) directement. Cette option est celle qui offre la meilleure expérience utilisateur et requiert la configuration minimale pour les développeurs d'applications serveur.</span><span class="sxs-lookup"><span data-stu-id="c624d-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="c624d-273">Exemple d'intégration d'applications</span><span class="sxs-lookup"><span data-stu-id="c624d-273">Application integration example</span></span>

<span data-ttu-id="c624d-p124">Une organisation crée une application ASP.NET qui expose un point de terminaison REST où d'autres applications peuvent obtenir les données de ventes les plus récentes. L'accès à ce point de terminaison REST est sécurisé avec Azure Active Directory. Pour que l'application ASP.NET envoie les données requises, les applications doivent fournir des informations d'identification qui peuvent être authentifiées par Azure AD. Les autres développeurs de l'organisation peuvent ensuite écrire des applications qui utilisent les données de ventes issues du point de terminaison REST.</span><span class="sxs-lookup"><span data-stu-id="c624d-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="c624d-p125">Pour vous authentifier auprès d'Azure Active Directory et récupérer des données, ADAL gère le processus d'authentification et transmet le jeton d'accès à l'application afin qu'il puisse être utilisé pour accéder aux données de ventes. ADAL simplifie grandement l'obtention et l'analyse des jetons, des flux OAuth et d'autres éléments. ADAL est une solution technologique qui évolue rapidement. Les développeurs doivent donc aller chercher la version la plus récente sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="c624d-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="c624d-281">Déploiement de composants d'annuaire dans Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="c624d-p126">Vous pouvez déployer des composants d'annuaire, tels que des serveurs utilisés pour la synchronisation de mot de passe ou l'authentification fédérée, dans un réseau virtuel Azure plutôt que dans un centre de données local. Cette solution a certains avantages, en particulier si vous envisagez d'étendre les services AD DS à Azure.</span><span class="sxs-lookup"><span data-stu-id="c624d-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="c624d-284">Voici les composants d'annuaire qui peuvent être mis dans un réseau virtuel Azure :</span><span class="sxs-lookup"><span data-stu-id="c624d-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="c624d-285">L'outil Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="c624d-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="c624d-286">Les composants d'authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="c624d-286">Federated authentication components</span></span>
    
- <span data-ttu-id="c624d-287">Un environnement AD DS autonome</span><span class="sxs-lookup"><span data-stu-id="c624d-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="c624d-288">L'outil AD Connect</span><span class="sxs-lookup"><span data-stu-id="c624d-288">AD Connect tool</span></span>

<span data-ttu-id="c624d-p127">L'outil Azure AD Connect peut être hébergé dans le cloud sur un réseau virtuel Azure. Le déploiement de cette charge de travail dans Azure présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="c624d-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="c624d-291">Mise en service potentiellement plus rapide et réduction des coûts des opérations</span><span class="sxs-lookup"><span data-stu-id="c624d-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="c624d-292">Disponibilité accrue</span><span class="sxs-lookup"><span data-stu-id="c624d-292">Increased availability</span></span>
    
![Outil AD Connect exécuté dans les services d'infrastructure Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="c624d-294">**Figure 8 : Exécution de l'outil AD Connect dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c624d-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="c624d-p128">La figure 8 présente l'outil AD Connect, exécuté sur une machine virtuelle dans un réseau virtuel Azure, qui effectue une demande auprès d'un contrôleur de domaine AD DS local pour obtenir les modifications apportées aux comptes, puis envoie ces modifications à Office 365. Cette solution fonctionne avec :</span><span class="sxs-lookup"><span data-stu-id="c624d-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="c624d-297">Les services Office 365.</span><span class="sxs-lookup"><span data-stu-id="c624d-297">Office 365 services.</span></span>
    
- <span data-ttu-id="c624d-298">Les applications PaaS Azure disponibles sur Internet.</span><span class="sxs-lookup"><span data-stu-id="c624d-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="c624d-299">Les applications métier d'Azure disponibles dans des environnements locaux via une connexion ExpressRoute ou VPN de site à site.</span><span class="sxs-lookup"><span data-stu-id="c624d-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="c624d-300">Pour plus d'informations, voir [Intégration de vos identités locales avec Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="c624d-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="c624d-301">Infrastructure d'authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="c624d-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="c624d-302">Si vous n'avez pas déjà déployé AD FS en local, penchez-vous sur les avantages offerts par le déploiement de cette charge de travail dans Azure :</span><span class="sxs-lookup"><span data-stu-id="c624d-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="c624d-303">Offre une autonomie pour l'authentification pour les services cloud (aucune dépendance locale)</span><span class="sxs-lookup"><span data-stu-id="c624d-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="c624d-304">Permet de réduire les serveurs et les outils hébergés en local</span><span class="sxs-lookup"><span data-stu-id="c624d-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="c624d-305">Utilise une passerelle VPN de site à site sur un cluster de basculement à deux nœuds pour se connecter à Azure (nouveau)</span><span class="sxs-lookup"><span data-stu-id="c624d-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="c624d-306">Utilise des listes de contrôle d'accès pour assurer que les serveurs de proxy d'application web puissent uniquement communiquer avec AD FS, et non avec les contrôleurs de domaine ou avec d'autres serveurs directement</span><span class="sxs-lookup"><span data-stu-id="c624d-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Déploiement de votre infrastructure d'authentification fédérée dans Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="c624d-308">**Figure 9 : Déploiement de votre infrastructure d'authentification fédérée dans Azure**</span><span class="sxs-lookup"><span data-stu-id="c624d-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="c624d-p129">La figure 9 présente un ensemble de contrôleurs de domaine locaux répliquant des informations AD DS avec un ensemble de contrôleurs de domaine situés dans un réseau virtuel Azure. L'outil Azure AD Connect exécuté sur un serveur du réseau virtuel Azure envoie une demande aux contrôleurs locaux pour obtenir les modifications, puis envoie ces modifications à Azure AD. Les demandes d'authentification auprès d'Azure AD émanant de services Saas de Microsoft, d'applications PaaS Azure et d'autres applications cloud sont transférées à un programme d'équilibrage de charge externe qui les transfère ensuite à un ensemble de serveurs Proxy d'application web. Les serveurs proxy d'application web transmettent la demande à un programme d'équilibrage de charge interne, lequel la transfère ensuite à un ensemble de serveurs AD FS. Les serveurs AD FS transfèrent alors la demande à un contrôleur de domaine pour valider les informations d'identification de d'envoi.</span><span class="sxs-lookup"><span data-stu-id="c624d-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="c624d-314">Cette solution fonctionne avec :</span><span class="sxs-lookup"><span data-stu-id="c624d-314">This solution works with:</span></span>
  
- <span data-ttu-id="c624d-315">Les applications qui nécessitent Kerberos</span><span class="sxs-lookup"><span data-stu-id="c624d-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="c624d-316">Tous les services SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="c624d-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="c624d-317">Les applications Azure qui sont accessibles sur Internet</span><span class="sxs-lookup"><span data-stu-id="c624d-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="c624d-318">Les applications IaaS ou PaaS d'Azure qui nécessitent l'authentification pour l'ensemble des comptes contenus dans l'instance AD DS de votre organisation</span><span class="sxs-lookup"><span data-stu-id="c624d-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="c624d-319">Pour plus d'informations, voir [Intégration de vos identités locales avec Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="c624d-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="c624d-320">Environnement AD DS autonome dans un réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="c624d-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="c624d-p130">Il n'est pas toujours nécessaire d'intégrer une application cloud avec votre environnement local. Par exemple, un domaine AD DS autonome placé dans un réseau virtuel Azure prend en charge les applications accessibles au public, telles que les sites Internet.</span><span class="sxs-lookup"><span data-stu-id="c624d-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Environnement AD DS autonome pour une application serveur](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="c624d-324">**Figure 10 : Environnement AD DS autonome pour une application basée sur serveur**</span><span class="sxs-lookup"><span data-stu-id="c624d-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="c624d-p131">La figure 10 présente un réseau virtuel Azure qui héberge un ensemble de serveurs AD DS, fournissant à la fois des services AD DS et DNS, et un ensemble de serveurs qui hébergent une application. Cette solution fonctionne avec :</span><span class="sxs-lookup"><span data-stu-id="c624d-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="c624d-327">Les sites web et les applications connectées à Internet</span><span class="sxs-lookup"><span data-stu-id="c624d-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="c624d-328">Les applications qui nécessitent l'authentification Kerberos ou NTLM</span><span class="sxs-lookup"><span data-stu-id="c624d-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="c624d-329">Les applications exécutées sur des serveurs Windows qui nécessitent AD DS</span><span class="sxs-lookup"><span data-stu-id="c624d-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="c624d-330">Pour plus d'informations, voir [Intégration de vos identités locales avec Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="c624d-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c624d-331">See Also</span><span class="sxs-lookup"><span data-stu-id="c624d-331">See Also</span></span>

[<span data-ttu-id="c624d-332">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="c624d-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="c624d-333">Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs</span><span class="sxs-lookup"><span data-stu-id="c624d-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



