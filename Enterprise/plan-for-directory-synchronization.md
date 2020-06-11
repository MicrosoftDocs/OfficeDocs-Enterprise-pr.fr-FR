---
title: Identité hybride et synchronisation d’annuaires pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Décrit la synchronisation d’annuaires avec Microsoft 365, le nettoyage des services de domaine Active Directory et l’outil Azure Active Directory Connect.
ms.openlocfilehash: ef7af68a65e4799e7bffbe6edba4f2b237a4d8b4
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698961"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="c5ac8-103">Identité hybride et synchronisation d’annuaires pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c5ac8-103">Hybrid identity and directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="c5ac8-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="c5ac8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c5ac8-105">En fonction des besoins de votre entreprise et des exigences techniques, le modèle d’identité hybride et la synchronisation d’annuaires constituent le choix le plus courant pour les clients d’entreprise qui adoptent Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-105">Depending on your business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365.</span></span> <span data-ttu-id="c5ac8-106">La synchronisation d’annuaires vous permet de gérer les identités dans vos services de domaine Active Directory (AD DS) et toutes les mises à jour des comptes d’utilisateur, des groupes et des contacts sont synchronisées avec le client Azure Active Directory (Azure AD) de votre abonnement Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="c5ac8-107">Lorsque les comptes d’utilisateur AD DS sont synchronisés pour la première fois, une licence Microsoft 365 n’est pas automatiquement attribuée et ne peut pas accéder aux services Microsoft 365, tels que la messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Microsoft 365 license and cannot access Microsoft 365 services, such as email.</span></span> <span data-ttu-id="c5ac8-108">Vous devez d’abord leur affecter un emplacement d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-108">You must first assign them a usage location.</span></span> <span data-ttu-id="c5ac8-109">Ensuite, attribuez une licence à ces comptes d’utilisateur, de manière individuelle ou dynamique via l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-109">Then, assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="c5ac8-110">Authentification pour l’identité hybride</span><span class="sxs-lookup"><span data-stu-id="c5ac8-110">Authentication for hybrid identity</span></span>

<span data-ttu-id="c5ac8-111">Il existe deux types d’authentification lors de l’utilisation du modèle d’identité hybride :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-111">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="c5ac8-112">Authentification gérée</span><span class="sxs-lookup"><span data-stu-id="c5ac8-112">Managed authentication</span></span>

  <span data-ttu-id="c5ac8-113">Azure AD gère le processus d’authentification à l’aide d’une version hachée stockée localement du mot de passe ou envoie les informations d’identification à un agent logiciel local pour être authentifié par le service AD DS local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-113">Azure AD handles the authentication process by using a locally-stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="c5ac8-114">Authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="c5ac8-114">Federated authentication</span></span>

  <span data-ttu-id="c5ac8-115">Azure AD redirige l’ordinateur client demandant l’authentification à un autre fournisseur d’identité.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-115">Azure AD redirects the client computer requesting authentication to another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="c5ac8-116">Authentification gérée</span><span class="sxs-lookup"><span data-stu-id="c5ac8-116">Managed authentication</span></span>

<span data-ttu-id="c5ac8-117">Il existe deux types d’authentification gérée :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-117">There are two types of managed authentication:</span></span>

- <span data-ttu-id="c5ac8-118">Synchronisation de hachage de mot de passe (hachage)</span><span class="sxs-lookup"><span data-stu-id="c5ac8-118">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="c5ac8-119">Azure AD effectue l’authentification proprement dite.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-119">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="c5ac8-120">Authentification directe (PTA)</span><span class="sxs-lookup"><span data-stu-id="c5ac8-120">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="c5ac8-121">Les services AD DS d’Azure AD effectuent l’authentification.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-121">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization-phs"></a><span data-ttu-id="c5ac8-122">Synchronisation de hachage de mot de passe (hachage)</span><span class="sxs-lookup"><span data-stu-id="c5ac8-122">Password hash synchronization (PHS)</span></span>

<span data-ttu-id="c5ac8-123">Avec hachage, vous synchronisez vos comptes d’utilisateur AD DS avec Microsoft 365 et vous gérez vos utilisateurs en local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-123">With PHS, you synchronize your AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> <span data-ttu-id="c5ac8-124">Les hachages des mots de passe des utilisateurs sont synchronisés entre votre AD DS et Azure AD afin que les utilisateurs aient le même mot de passe sur site et dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-124">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="c5ac8-125">Il s’agit de la méthode la plus simple pour activer l’authentification pour les identités AD DS dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-125">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![Synchronisation de hachage de mot de passe (hachage)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="c5ac8-127">Lorsque les mots de passe sont modifiés ou réinitialisés en local, les nouveaux hachages de mot de passe sont synchronisés avec Azure AD afin que les utilisateurs puissent toujours utiliser le même mot de passe pour les ressources en nuage et les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-127">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="c5ac8-128">Les mots de passe utilisateur ne sont jamais envoyés à Azure AD ou stockés dans Azure AD en texte clair.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-128">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="c5ac8-129">Certaines fonctionnalités avancées d’Azure AD, telles que la protection des identités, nécessitent hachage, quelle que soit la méthode d’authentification sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-129">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="c5ac8-130">Pour plus d’informations, consultez [la rubrique choix de la méthode d’authentification appropriée](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-130">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication-pta"></a><span data-ttu-id="c5ac8-131">Authentification directe (PTA)</span><span class="sxs-lookup"><span data-stu-id="c5ac8-131">Pass-through authentication (PTA)</span></span>

<span data-ttu-id="c5ac8-132">DIRECTE fournit une validation simple de mot de passe pour les services d’authentification Azure AD à l’aide d’un agent logiciel exécuté sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre service AD DS.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-132">PTA provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="c5ac8-133">Avec directe, vous synchronisez les comptes d’utilisateur AD DS avec Microsoft 365 et vous gérez vos utilisateurs en local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-133">With PTA, you synchronize AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> 

![Authentification directe (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="c5ac8-135">DIRECTE permet à vos utilisateurs de se connecter à des ressources et des applications locales et Microsoft 365 à l’aide de leur compte local et de leur mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-135">PTA allows your users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="c5ac8-136">Cette configuration valide les mots de passe des utilisateurs directement par rapport à votre service AD DS local sans stocker les hachages de mots de passe dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-136">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="c5ac8-137">DIRECTE est également destiné aux organisations disposant d’un impératif de sécurité pour appliquer immédiatement les États de compte d’utilisateur, les stratégies de mot de passe et les heures d’ouverture de session locaux.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-137">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="c5ac8-138">Pour plus d’informations, consultez [la rubrique choix de la méthode d’authentification appropriée](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-138">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="c5ac8-139">Authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="c5ac8-139">Federated authentication</span></span>

<span data-ttu-id="c5ac8-140">L’authentification fédérée est principalement destinée aux grandes entreprises ayant des exigences d’authentification plus complexes.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-140">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="c5ac8-141">Les identités AD DS sont synchronisées avec Microsoft 365 et les comptes d’utilisateurs sont gérés en local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-141">AD DS identities are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="c5ac8-142">Avec l’authentification fédérée, les utilisateurs ont le même mot de passe sur site et dans le Cloud et ils n’ont pas besoin de se connecter à nouveau pour utiliser Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-142">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Microsoft 365.</span></span> 

<span data-ttu-id="c5ac8-143">L’authentification fédérée peut prendre en charge des exigences d’authentification supplémentaires, telles que l’authentification par carte à puce ou une authentification multifacteur tierce et est généralement requise lorsque les organisations ont une condition d’authentification qui n’est pas prise en charge en mode natif par Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-143">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="c5ac8-144">Pour plus d’informations, consultez [la rubrique choix de la méthode d’authentification appropriée](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-144">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="c5ac8-145">Fournisseurs d’identité et d’authentification tiers</span><span class="sxs-lookup"><span data-stu-id="c5ac8-145">Third-party authentication and identity providers</span></span>

<span data-ttu-id="c5ac8-146">Les objets d’annuaire locaux peuvent être synchronisés avec Microsoft 365 et l’accès aux ressources de Cloud est principalement géré par un fournisseur d’identité tiers (IdP).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-146">On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="c5ac8-147">Si votre organisation utilise une solution de Fédération tierce, vous pouvez configurer l’authentification avec cette solution pour Microsoft 365, à condition que la solution de Fédération tierce soit compatible avec Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-147">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Microsoft 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="c5ac8-148">Pour en savoir plus, consultez la [liste de compatibilité de Fédération Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-148">See the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="c5ac8-149">Nettoyage des services de domaine Active Directory</span><span class="sxs-lookup"><span data-stu-id="c5ac8-149">AD DS Cleanup</span></span>

<span data-ttu-id="c5ac8-150">Pour garantir une transition transparente vers Microsoft 365 à l’aide de la synchronisation, vous devez préparer votre forêt AD DS avant de commencer le déploiement de la synchronisation d’annuaires Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-150">To help ensure a seamless transition to Microsoft 365 by using synchronization, you must prepare your AD DS forest before you begin your Microsoft 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="c5ac8-151">Lorsque vous [configurez la synchronisation d’annuaires](set-up-directory-synchronization.md), l’une des étapes consiste à [Télécharger et à exécuter l’outil IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-151">When you [set up directory synchronization](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="c5ac8-152">Vous pouvez utiliser l’outil IdFix pour faciliter le [nettoyage d’annuaire](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-152">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="c5ac8-153">Le nettoyage de votre annuaire doit se concentrer sur les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-153">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="c5ac8-154">Supprimez les attributs **ProxyAddress** et **userPrincipalName** en double.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-154">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="c5ac8-155">Mettre à jour les attributs **userPrincipalName** vides et non valides avec des attributs **userPrincipalName** valides.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-155">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="c5ac8-156">Supprimez les caractères non valides et douteables dans les attributs **GivenName**, Surname ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailnickname**et **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-156">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="c5ac8-157">Pour plus d’informations sur la préparation des attributs, voir [liste des attributs synchronisés par l’outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-157">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c5ac8-158">Il s’agit des mêmes attributs que ceux qui sont synchronisés avec Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-158">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="c5ac8-159">Considérations relatives au déploiement dans plusieurs forêts</span><span class="sxs-lookup"><span data-stu-id="c5ac8-159">Multi-forest deployment considerations</span></span>

<span data-ttu-id="c5ac8-160">Pour plusieurs forêts et options SSO, utilisez une [installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-160">For multiple forests and SSO options, use a [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="c5ac8-161">Si votre organisation dispose de plusieurs forêts pour l’authentification (forêts d’ouverture de session), nous vous recommandons vivement les suivants :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-161">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="c5ac8-162">**Envisagez de consolider vos forêts.**</span><span class="sxs-lookup"><span data-stu-id="c5ac8-162">**Consider consolidating your forests.**</span></span> <span data-ttu-id="c5ac8-163">En règle générale, il y a plus de charge nécessaire pour gérer plusieurs forêts.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-163">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="c5ac8-164">À moins que votre organisation n’ait des contraintes de sécurité qui dictent le besoin de forêts distinctes, envisagez de simplifier votre environnement local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-164">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="c5ac8-165">**Utilisez uniquement dans votre forêt d’ouverture de session principale.**</span><span class="sxs-lookup"><span data-stu-id="c5ac8-165">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="c5ac8-166">Envisagez de déployer Microsoft 365 uniquement dans votre forêt d’ouverture de session principale pour le déploiement initial de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-166">Consider deploying Microsoft 365 only in your primary logon forest for your initial rollout of Microsoft 365.</span></span> 

<span data-ttu-id="c5ac8-167">Si vous ne pouvez pas consolider votre déploiement AD DS à forêts multiples ou si vous utilisez d’autres services d’annuaire pour gérer les identités, vous pourrez peut-être les synchroniser avec l’aide de Microsoft ou d’un partenaire.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-167">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="c5ac8-168">Pour plus d’informations, voir [topologies pour Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) .</span><span class="sxs-lookup"><span data-stu-id="c5ac8-168">See [Topologies for Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="c5ac8-169">Fonctionnalités dépendant de la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="c5ac8-169">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="c5ac8-170">La synchronisation d’annuaires est requise pour les fonctionnalités et fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-170">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="c5ac8-171">Authentification unique transparente Azure AD (SSO)</span><span class="sxs-lookup"><span data-stu-id="c5ac8-171">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="c5ac8-172">Coexistence Skype</span><span class="sxs-lookup"><span data-stu-id="c5ac8-172">Skype coexistence</span></span>
- <span data-ttu-id="c5ac8-173">Déploiement Exchange hybride, notamment :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-173">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="c5ac8-174">Liste d’adresses globale (GAL) entièrement partagée entre votre environnement Exchange local et Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-174">Fully shared global address list (GAL) between your on-premises Exchange environment and Microsoft 365.</span></span>
  - <span data-ttu-id="c5ac8-175">Synchronisation des informations GAL provenant de différents systèmes de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-175">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="c5ac8-176">La possibilité d’ajouter et de supprimer des utilisateurs des offres de service Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-176">The ability to add users to and remove users from Microsoft 365 service offerings.</span></span> <span data-ttu-id="c5ac8-177">Cette possibilité nécessite ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c5ac8-177">This requires the following:</span></span>
  - <span data-ttu-id="c5ac8-178">La synchronisation bidirectionnelle doit être configurée lors de la configuration de la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-178">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="c5ac8-179">Par défaut, les outils de synchronisation d’annuaires écrivent des informations d’annuaire uniquement dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-179">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="c5ac8-180">Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d’écriture différée de sorte qu’un nombre limité d’attributs d’objets sont copiés à partir du Cloud, puis réécrits dans vos services AD DS locaux.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-180">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="c5ac8-181">L’écriture différée est également appelée mode hybride Exchange.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-181">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="c5ac8-182">Un déploiement Exchange hybride local</span><span class="sxs-lookup"><span data-stu-id="c5ac8-182">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="c5ac8-183">Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Microsoft 365 tout en conservant les autres boîtes aux lettres utilisateur en local.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-183">The ability to move some user mailboxes to Microsoft 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="c5ac8-184">Les expéditeurs approuvés et les expéditeurs bloqués en local sont répliqués sur Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-184">Safe senders and blocked senders on-premises are replicated to Microsoft 365.</span></span>
  - <span data-ttu-id="c5ac8-185">Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».</span><span class="sxs-lookup"><span data-stu-id="c5ac8-185">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="c5ac8-186">Vous disposez d’une solution d’authentification multifacteur ou de carte à puce sur site intégrée.</span><span class="sxs-lookup"><span data-stu-id="c5ac8-186">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="c5ac8-187">Synchronisation de photos, de miniatures, de salles de conférence et de groupes de sécurité</span><span class="sxs-lookup"><span data-stu-id="c5ac8-187">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="c5ac8-188">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="c5ac8-188">Next step</span></span>

<span data-ttu-id="c5ac8-189">Lorsque vous êtes prêt à déployer l’identité hybride, consultez la rubrique préparer la mise [en service des utilisateurs](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="c5ac8-189">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5ac8-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5ac8-190">See also</span></span>

[<span data-ttu-id="c5ac8-191">Vue d’ensemble de Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="c5ac8-191">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

