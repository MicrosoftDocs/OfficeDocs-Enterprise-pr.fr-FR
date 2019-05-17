---
title: Identité hybride et synchronisation d’annuaires pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Décrit la synchronisation d’annuaires avec Office 365, le nettoyage des services de domaine Active Directory et l’outil Azure Active Directory Connect.
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102489"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="46172-103">Identité hybride et synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="46172-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="46172-104">En fonction des besoins de l’entreprise et des exigences techniques, le modèle d’identité hybride et la synchronisation d’annuaires constituent le choix le plus courant pour les clients d’entreprise qui adoptent Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-104">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="46172-105">La synchronisation d’annuaires vous permet de gérer les identités dans vos services de domaine Active Directory (AD DS) et toutes les mises à jour des comptes d’utilisateur, des groupes et des contacts sont synchronisées avec le client Azure Active Directory (Azure AD) de votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-105">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>


>[!Note]
><span data-ttu-id="46172-106">Lorsque les comptes d’utilisateur AD DS sont synchronisés pour la première fois, une licence Office 365 n’est pas automatiquement attribuée et ne peut pas accéder aux services 365 Office, tels que le courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="46172-106">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="46172-107">Vous devez attribuer une licence à ces comptes d’utilisateur, de manière individuelle ou dynamique via l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="46172-107">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="46172-108">Authentification pour l’identité hybride</span><span class="sxs-lookup"><span data-stu-id="46172-108">Authentication for hybrid identity</span></span>

<span data-ttu-id="46172-109">Il existe deux types d’authentification lors de l’utilisation du modèle d’identité hybride:</span><span class="sxs-lookup"><span data-stu-id="46172-109">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="46172-110">Authentification gérée</span><span class="sxs-lookup"><span data-stu-id="46172-110">Managed authentication</span></span>

  <span data-ttu-id="46172-111">Azure AD gère le processus d’authentification à l’aide d’une version hachée stockée localement du mot de passe ou envoie les informations d’identification à un agent logiciel local pour qu’il soit authentifié par le service AD DS local.</span><span class="sxs-lookup"><span data-stu-id="46172-111">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="46172-112">Authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="46172-112">Federated authentication</span></span>

  <span data-ttu-id="46172-113">Azure AD redirige l’ordinateur client demandant l’authentification pour contacter un autre fournisseur d’identité.</span><span class="sxs-lookup"><span data-stu-id="46172-113">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="46172-114">Authentification gérée</span><span class="sxs-lookup"><span data-stu-id="46172-114">Managed authentication</span></span>

<span data-ttu-id="46172-115">Il existe deux types d’authentification gérée:</span><span class="sxs-lookup"><span data-stu-id="46172-115">There are two types of managed authentication:</span></span>

- <span data-ttu-id="46172-116">Synchronisation de hachage de mot de passe (hachage)</span><span class="sxs-lookup"><span data-stu-id="46172-116">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="46172-117">Azure AD effectue l’authentification proprement dite.</span><span class="sxs-lookup"><span data-stu-id="46172-117">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="46172-118">Authentification directe (PTA)</span><span class="sxs-lookup"><span data-stu-id="46172-118">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="46172-119">Les services AD DS d’Azure AD effectuent l’authentification.</span><span class="sxs-lookup"><span data-stu-id="46172-119">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="46172-120">Synchronisation de hachage de mot de passe</span><span class="sxs-lookup"><span data-stu-id="46172-120">Password hash synchronization</span></span>

<span data-ttu-id="46172-121">Avec la synchronisation de hachage de mot de passe (hachage), vous synchronisez vos comptes d’utilisateur AD DS avec Office 365 et vous gérez vos utilisateurs en local.</span><span class="sxs-lookup"><span data-stu-id="46172-121">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="46172-122">Les hachages des mots de passe des utilisateurs sont synchronisés entre votre AD DS et Azure AD afin que les utilisateurs aient le même mot de passe sur site et dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="46172-122">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="46172-123">Il s’agit de la méthode la plus simple pour activer l’authentification pour les identités AD DS dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="46172-123">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="46172-124">Lorsque les mots de passe sont modifiés ou réinitialisés en local, les nouveaux hachages de mot de passe sont synchronisés avec Azure AD afin que les utilisateurs puissent toujours utiliser le même mot de passe pour les ressources en nuage et les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="46172-124">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="46172-125">Les mots de passe utilisateur ne sont jamais envoyés à Azure AD ou stockés dans Azure AD en texte clair.</span><span class="sxs-lookup"><span data-stu-id="46172-125">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="46172-126">Certaines fonctionnalités avancées d’Azure AD, telles que la protection des identités, nécessitent hachage, quelle que soit la méthode d’authentification sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="46172-126">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="46172-127">Pour plus d’informations, voir [choosING hachage](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="46172-127">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="46172-128">Authentification directe</span><span class="sxs-lookup"><span data-stu-id="46172-128">Pass-through authentication</span></span>

<span data-ttu-id="46172-129">L’authentification directe (directe) fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel exécuté sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre service AD DS.</span><span class="sxs-lookup"><span data-stu-id="46172-129">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="46172-130">Avec l’authentification directe (directe), vous synchronisez les comptes d’utilisateur AD DS avec Office 365 et vous gérez vos utilisateurs en local.</span><span class="sxs-lookup"><span data-stu-id="46172-130">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="46172-131">DIRECTE permet à vos utilisateurs de se connecter à des ressources et des applications locales et Office 365 à l’aide de leur compte local et de leur mot de passe.</span><span class="sxs-lookup"><span data-stu-id="46172-131">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="46172-132">Cette configuration valide les mots de passe des utilisateurs directement par rapport à votre service AD DS local sans stocker les hachages de mots de passe dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="46172-132">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="46172-133">DIRECTE est également destiné aux organisations disposant d’un impératif de sécurité pour appliquer immédiatement les États de compte d’utilisateur, les stratégies de mot de passe et les heures d’ouverture de session locaux.</span><span class="sxs-lookup"><span data-stu-id="46172-133">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="46172-134">Pour plus d’informations, voir [choosING directe](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="46172-134">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="46172-135">Authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="46172-135">Federated authentication</span></span>

<span data-ttu-id="46172-136">L’authentification fédérée est principalement destinée aux grandes entreprises ayant des exigences d’authentification plus complexes.</span><span class="sxs-lookup"><span data-stu-id="46172-136">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="46172-137">Les identités AD DS sont synchronisées avec Office 365 et les comptes d’utilisateurs sont gérés en local.</span><span class="sxs-lookup"><span data-stu-id="46172-137">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="46172-138">Avec l’authentification fédérée, les utilisateurs ont le même mot de passe sur site et dans le Cloud et ils n’ont pas besoin de se connecter à nouveau pour utiliser Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-138">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="46172-139">L’authentification fédérée peut prendre en charge des exigences d’authentification supplémentaires, telles que l’authentification par carte à puce ou une authentification multifacteur tierce et est généralement requise lorsque les organisations ont une condition d’authentification non pris en charge en mode natif par Azure AD.</span><span class="sxs-lookup"><span data-stu-id="46172-139">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="46172-140">Voir [choix de l’authentification fédérée](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="46172-140">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="46172-141">Fournisseurs d’identité et d’authentification tiers</span><span class="sxs-lookup"><span data-stu-id="46172-141">Third-party authentication and identity providers</span></span>

<span data-ttu-id="46172-142">Les objets d’annuaire locaux peuvent être synchronisés avec Office 365 et l’accès aux ressources de Cloud est principalement géré par un fournisseur d’identité tiers (IdP).</span><span class="sxs-lookup"><span data-stu-id="46172-142">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="46172-143">Si votre organisation utilise une solution de Fédération tierce, vous pouvez configurer l’authentification avec cette solution pour Office 365 à condition que la solution de Fédération tierce soit compatible avec Azure AD.</span><span class="sxs-lookup"><span data-stu-id="46172-143">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="46172-144">Pour en savoir plus, voir [compatibilité de Fédération Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="46172-144">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="46172-145">Nettoyage des services de domaine Active Directory</span><span class="sxs-lookup"><span data-stu-id="46172-145">AD DS Cleanup</span></span>

<span data-ttu-id="46172-146">Pour garantir une transition transparente vers Office 365 à l’aide de la synchronisation, vous devez préparer votre forêt AD DS avant de commencer le déploiement de la synchronisation d’annuaires d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-146">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="46172-147">Lorsque vous configurez la [synchronisation d’annuaires dans Office 365](set-up-directory-synchronization.md), l’une des étapes consiste à [Télécharger et à exécuter l’outil IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="46172-147">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="46172-148">Vous pouvez utiliser l’outil IdFix pour faciliter le [nettoyage d’annuaire](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="46172-148">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="46172-149">Le nettoyage de votre annuaire doit se concentrer sur les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="46172-149">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="46172-150">Supprimez les attributs **ProxyAddress** et **userPrincipalName** en double.</span><span class="sxs-lookup"><span data-stu-id="46172-150">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="46172-151">Mettre à jour les attributs **userPrincipalName** vides et non valides avec des attributs **userPrincipalName** valides.</span><span class="sxs-lookup"><span data-stu-id="46172-151">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="46172-152">Supprimer les caractères non valides et douteables dans les attributs **GivenName**, Surname ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailnickname**et **userPrincipalName** ceux.</span><span class="sxs-lookup"><span data-stu-id="46172-152">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="46172-153">Pour plus d’informations sur la préparation des attributs, voir [liste des attributs synchronisés par l’outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="46172-153">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="46172-154">Il s’agit des mêmes attributs que ceux qui sont synchronisés avec Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="46172-154">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="46172-155">Considérations relatives au déploiement dans plusieurs forêts</span><span class="sxs-lookup"><span data-stu-id="46172-155">Multi-forest deployment considerations</span></span>

<span data-ttu-id="46172-156">Pour plusieurs forêts et options d’authentification unique, utilisez [l’installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="46172-156">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="46172-157">Si votre organisation dispose de plusieurs forêts pour l’authentification (forêts d’ouverture de session), nous vous recommandons vivement les suivants:</span><span class="sxs-lookup"><span data-stu-id="46172-157">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="46172-158">**Envisagez de consolider vos forêts.**</span><span class="sxs-lookup"><span data-stu-id="46172-158">**Consider consolidating your forests.**</span></span> <span data-ttu-id="46172-159">En règle générale, il y a plus de charge nécessaire pour gérer plusieurs forêts.</span><span class="sxs-lookup"><span data-stu-id="46172-159">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="46172-160">À moins que votre organisation n’ait des contraintes de sécurité qui dictent le besoin de forêts distinctes, envisagez de simplifier votre environnement local.</span><span class="sxs-lookup"><span data-stu-id="46172-160">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="46172-161">**Utilisez uniquement dans votre forêt d’ouverture de session principale.**</span><span class="sxs-lookup"><span data-stu-id="46172-161">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="46172-162">Envisagez de déployer Office 365 uniquement dans votre forêt d’ouverture de session principale pour le déploiement initial d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-162">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="46172-163">Si vous ne pouvez pas consolider votre déploiement AD DS à forêts multiples ou si vous utilisez d’autres services d’annuaire pour gérer les identités, vous pourrez peut-être les synchroniser avec l’aide de Microsoft ou d’un partenaire.</span><span class="sxs-lookup"><span data-stu-id="46172-163">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="46172-164">Pour plus d’informations, consultez la rubrique synchronisation d’annuaires de [forêts multiples avec un scénario d’authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=525321) .</span><span class="sxs-lookup"><span data-stu-id="46172-164">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="46172-165">Fonctionnalités dépendant de la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="46172-165">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="46172-166">La synchronisation d’annuaires est requise pour les fonctionnalités et fonctionnalités suivantes:</span><span class="sxs-lookup"><span data-stu-id="46172-166">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="46172-167">Authentification unique transparente Azure AD (SSO)</span><span class="sxs-lookup"><span data-stu-id="46172-167">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="46172-168">Coexistence Skype</span><span class="sxs-lookup"><span data-stu-id="46172-168">Skype coexistence</span></span>
- <span data-ttu-id="46172-169">Déploiement Exchange hybride, notamment:</span><span class="sxs-lookup"><span data-stu-id="46172-169">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="46172-170">Liste d’adresses globale (GAL) entièrement partagée entre votre environnement Exchange local et Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-170">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="46172-171">Synchronisation des informations GAL provenant de différents systèmes de messagerie.</span><span class="sxs-lookup"><span data-stu-id="46172-171">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="46172-172">Possibilité d’ajouter et de supprimer des utilisateurs des offres de services Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-172">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="46172-173">Cette possibilité nécessite ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="46172-173">This requires the following:</span></span>
  - <span data-ttu-id="46172-174">La synchronisation bidirectionnelle doit être configurée lors de la configuration de la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="46172-174">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="46172-175">Par défaut, les outils de synchronisation d’annuaires écrivent des informations d’annuaire uniquement dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="46172-175">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="46172-176">Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d’écriture différée de sorte qu’un nombre limité d’attributs d’objets sont copiés à partir du Cloud, puis réécrits dans vos services AD DS locaux.</span><span class="sxs-lookup"><span data-stu-id="46172-176">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="46172-177">L’écriture différée est également appelée mode hybride Exchange.</span><span class="sxs-lookup"><span data-stu-id="46172-177">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="46172-178">Un déploiement Exchange hybride local</span><span class="sxs-lookup"><span data-stu-id="46172-178">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="46172-179">Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Office 365 tout en conservant les autres boîtes aux lettres utilisateur en local.</span><span class="sxs-lookup"><span data-stu-id="46172-179">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="46172-180">Les expéditeurs approuvés et les expéditeurs bloqués en local sont répliqués vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="46172-180">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="46172-181">Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».</span><span class="sxs-lookup"><span data-stu-id="46172-181">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="46172-182">Vous disposez d’une solution d’authentification multifacteur ou de carte à puce sur site intégrée.</span><span class="sxs-lookup"><span data-stu-id="46172-182">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="46172-183">Synchronisation de photos, de miniatures, de salles de conférence et de groupes de sécurité</span><span class="sxs-lookup"><span data-stu-id="46172-183">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="46172-184">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="46172-184">Next step</span></span>

<span data-ttu-id="46172-185">Lorsque vous êtes prêt à déployer l’identité hybride, consultez la rubrique préparer la mise [en service des utilisateurs](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="46172-185">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  

