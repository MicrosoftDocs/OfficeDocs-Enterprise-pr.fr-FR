---
title: Sécurité de Contoso Corporation
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
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Résumé : Découvrez comment Contoso mappées leurs exigences de sécurité pour les fonctionnalités dans les offres de cloud de Microsoft et déterminez un chemin d’accès à la préparation de la sécurité en nuage.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914829"
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="46ad3-103">Sécurité de Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="46ad3-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="46ad3-104">**Résumé :** Comprendre comment Contoso mappées leurs exigences de sécurité pour les fonctionnalités dans les offres de cloud de Microsoft et déterminez un chemin d’accès à la préparation de la sécurité en nuage.</span><span class="sxs-lookup"><span data-stu-id="46ad3-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="46ad3-p101">Contoso est grave sur leur sécurité des informations et de protection. Lors de la transition de leur infrastructure informatique sur un nuage-inclus, ils assurés que leurs exigences de sécurité locale ont été pris en charge et implémentés dans les offres de cloud de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="46ad3-107">Exigences de sécurité de Contoso dans le nuage</span><span class="sxs-lookup"><span data-stu-id="46ad3-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="46ad3-108">Voici les exigences de sécurité de Contoso concernant le cloud :</span><span class="sxs-lookup"><span data-stu-id="46ad3-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="46ad3-109">Authentification forte aux ressources du cloud</span><span class="sxs-lookup"><span data-stu-id="46ad3-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="46ad3-110">L’accès aux ressources du cloud doit être authentifié, si possible, par le biais d’une authentification multifacteur.</span><span class="sxs-lookup"><span data-stu-id="46ad3-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="46ad3-111">Chiffrement du trafic sur Internet</span><span class="sxs-lookup"><span data-stu-id="46ad3-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="46ad3-p102">Les données ne doivent jamais être envoyées en clair sur Internet. Utilisez toujours les connexions HTTPS, IPsec ou toute autre méthode de chiffrement des données de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="46ad3-114">Chiffrement des données au repos dans le cloud</span><span class="sxs-lookup"><span data-stu-id="46ad3-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="46ad3-115">Toutes les données doivent être chiffrées lorsqu’elles sont stockées sur des disques ou un autre emplacement dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="46ad3-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="46ad3-116">Listes de contrôle d’accès selon le principe des privilèges minimum</span><span class="sxs-lookup"><span data-stu-id="46ad3-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="46ad3-117">Autorisations accordées aux comptes pour accéder aux ressources du cloud et limiter le nombre et l’étendue des actions conformément au principe de privilèges minimum.</span><span class="sxs-lookup"><span data-stu-id="46ad3-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="46ad3-118">Classification de sensibilité des données de Contoso</span><span class="sxs-lookup"><span data-stu-id="46ad3-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="46ad3-119">Utilisation des informations de Microsoft du [Kit de ressources de classification des données](https://msdn.microsoft.com/library/hh204743.aspx), Contoso effectué une analyse de leurs données et déterminé les niveaux suivants.</span><span class="sxs-lookup"><span data-stu-id="46ad3-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="46ad3-120">**Niveau 1 : valeur commerciale faible**</span><span class="sxs-lookup"><span data-stu-id="46ad3-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="46ad3-121">**Niveau 2 : valeur commerciale moyenne**</span><span class="sxs-lookup"><span data-stu-id="46ad3-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="46ad3-122">**Niveau 3 : valeur commerciale forte**</span><span class="sxs-lookup"><span data-stu-id="46ad3-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="46ad3-123">Les données sont chiffrées et accessibles uniquement par les utilisateurs authentifiés

</span><span class="sxs-lookup"><span data-stu-id="46ad3-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="46ad3-p103">Niveau accordé à toutes les données stockées localement et dans le cloud et aux charges de travail, telles qu’Office 365. Les données sont chiffrées lorsqu’elles se trouvent dans le service et lorsqu’elles transitent entre le service et les appareils clients.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="46ad3-126">Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique.</span><span class="sxs-lookup"><span data-stu-id="46ad3-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="46ad3-127">Niveau 1 avec une authentification et une protection renforcées contre la perte de données
</span><span class="sxs-lookup"><span data-stu-id="46ad3-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="46ad3-p104">Une authentification forte est une authentification multifacteur avec validation SMS. La protection contre la perte de données permet de s’assurer que les informations sensibles ou critiques ne circulent pas à l’extérieur du réseau local.
</span><span class="sxs-lookup"><span data-stu-id="46ad3-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="46ad3-130">Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits.</span><span class="sxs-lookup"><span data-stu-id="46ad3-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="46ad3-131">Niveau 2 avec des niveaux de chiffrement, d’authentification et d’audit plus élevés
</span><span class="sxs-lookup"><span data-stu-id="46ad3-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="46ad3-132">Niveaux de chiffrement des données au repos et dans le cloud les plus élevés, conformes aux réglementations locales, associés à une authentification multifacteur des cartes à puce et aux fonctionnalités d’audit et d’alerte ciblées.
</span><span class="sxs-lookup"><span data-stu-id="46ad3-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="46ad3-133">Les données de niveau 3 concernent, par exemple, les informations d’identification des clients et des partenaires, ainsi que les spécifications techniques de produits et les techniques de fabrication appartenant à l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="46ad3-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="46ad3-134">Mappage des fonctionnalités et des offres de cloud Microsoft aux niveaux de données de Contoso</span><span class="sxs-lookup"><span data-stu-id="46ad3-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="46ad3-135">Le tableau suivant décrit le mappage des niveaux de données de Contoso aux fonctionnalités dans les offres cloud de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="46ad3-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="46ad3-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="46ad3-136">**SaaS**</span></span>|<span data-ttu-id="46ad3-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="46ad3-137">**Azure PaaS**</span></span>|<span data-ttu-id="46ad3-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="46ad3-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="46ad3-139">Niveau 1 : valeur commerciale faible</span><span class="sxs-lookup"><span data-stu-id="46ad3-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="46ad3-140">HTTPS pour toutes les connexions
</span><span class="sxs-lookup"><span data-stu-id="46ad3-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="46ad3-141">Chiffrement des données stockées</span><span class="sxs-lookup"><span data-stu-id="46ad3-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="46ad3-142">Prise en charge des connexions HTTPS uniquement
</span><span class="sxs-lookup"><span data-stu-id="46ad3-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="46ad3-143">Chiffrement des fichiers stockés dans Azure</span><span class="sxs-lookup"><span data-stu-id="46ad3-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="46ad3-144">HTTPS ou IPsec requis pour accéder au serveur
</span><span class="sxs-lookup"><span data-stu-id="46ad3-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="46ad3-145">Azure Disk Encryption</span><span class="sxs-lookup"><span data-stu-id="46ad3-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="46ad3-146">Niveau 2 : valeur commerciale moyenne</span><span class="sxs-lookup"><span data-stu-id="46ad3-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="46ad3-147">Authentification multifacteur (MFA) Azure AD avec SMS</span><span class="sxs-lookup"><span data-stu-id="46ad3-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="46ad3-148">Utilisation d’Azure Key Vault pour les clés de chiffrement
</span><span class="sxs-lookup"><span data-stu-id="46ad3-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="46ad3-149">Azure AD MFA avec SMS</span><span class="sxs-lookup"><span data-stu-id="46ad3-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="46ad3-150">MFA avec SMS</span><span class="sxs-lookup"><span data-stu-id="46ad3-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="46ad3-151">Niveau 3 : valeur commerciale forte</span><span class="sxs-lookup"><span data-stu-id="46ad3-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="46ad3-152">Azure Rights Management System (RMS)

</span><span class="sxs-lookup"><span data-stu-id="46ad3-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="46ad3-153">Azure AD MFA avec cartes à puce</span><span class="sxs-lookup"><span data-stu-id="46ad3-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="46ad3-154">Accès conditionnel Intune</span><span class="sxs-lookup"><span data-stu-id="46ad3-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="46ad3-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="46ad3-155">Azure RMS</span></span> <br/>  <span data-ttu-id="46ad3-156">Azure AD MFA avec cartes à puce</span><span class="sxs-lookup"><span data-stu-id="46ad3-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="46ad3-157">MFA avec cartes à puce</span><span class="sxs-lookup"><span data-stu-id="46ad3-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="46ad3-158">Stratégies des informations de Contoso</span><span class="sxs-lookup"><span data-stu-id="46ad3-158">Contoso's information policies</span></span>

<span data-ttu-id="46ad3-159">Le tableau suivant répertorie les stratégies de traitement des informations de Contoso.</span><span class="sxs-lookup"><span data-stu-id="46ad3-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="46ad3-160">**Accès**</span><span class="sxs-lookup"><span data-stu-id="46ad3-160">**Access**</span></span>|<span data-ttu-id="46ad3-161">**Rétention des données**</span><span class="sxs-lookup"><span data-stu-id="46ad3-161">**Data retention**</span></span>|<span data-ttu-id="46ad3-162">**Protection des informations**</span><span class="sxs-lookup"><span data-stu-id="46ad3-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="46ad3-163">Niveau 1 : valeur commerciale faible</span><span class="sxs-lookup"><span data-stu-id="46ad3-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="46ad3-164">Autoriser l’accès pour tous</span><span class="sxs-lookup"><span data-stu-id="46ad3-164">Allow access to all</span></span> <br/> |<span data-ttu-id="46ad3-165">6 mois</span><span class="sxs-lookup"><span data-stu-id="46ad3-165">6 months</span></span>  <br/> |<span data-ttu-id="46ad3-166">Utiliser le chiffrement</span><span class="sxs-lookup"><span data-stu-id="46ad3-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="46ad3-167">Niveau 2 : valeur commerciale moyenne</span><span class="sxs-lookup"><span data-stu-id="46ad3-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="46ad3-168">Autoriser l’accès aux collaborateurs, aux sous-traitants et aux partenaires de Contoso
</span><span class="sxs-lookup"><span data-stu-id="46ad3-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="46ad3-169">Utiliser MFA, TLS et MAM</span><span class="sxs-lookup"><span data-stu-id="46ad3-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="46ad3-170">2 ans</span><span class="sxs-lookup"><span data-stu-id="46ad3-170">2 years</span></span>  <br/> |<span data-ttu-id="46ad3-171">Utiliser les valeurs de hachage pour l’intégrité des données</span><span class="sxs-lookup"><span data-stu-id="46ad3-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="46ad3-172">Niveau 3 : valeur commerciale forte</span><span class="sxs-lookup"><span data-stu-id="46ad3-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="46ad3-173">Autoriser l’accès aux cadres et aux responsables des équipes techniques et de fabrication
</span><span class="sxs-lookup"><span data-stu-id="46ad3-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="46ad3-174">RMS avec périphériques réseau gérés uniquement</span><span class="sxs-lookup"><span data-stu-id="46ad3-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="46ad3-175">7 ans</span><span class="sxs-lookup"><span data-stu-id="46ad3-175">7 years</span></span>  <br/> |<span data-ttu-id="46ad3-176">Utiliser des signatures numériques pour la non-répudiation des données</span><span class="sxs-lookup"><span data-stu-id="46ad3-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="46ad3-177">Chemin d’accès de Contoso à l’évaluation de la sécurité dans le nuage</span><span class="sxs-lookup"><span data-stu-id="46ad3-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="46ad3-178">Contoso a établi la procédure suivante pour préparer la sécurité du cloud de Microsoft :</span><span class="sxs-lookup"><span data-stu-id="46ad3-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="46ad3-179">Optimiser les comptes Administrateur pour le cloud
</span><span class="sxs-lookup"><span data-stu-id="46ad3-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="46ad3-180">Contoso a effectué une révision complète des comptes Administrateur Windows Server AD existants et a configuré une série de groupes et de comptes Administrateurs dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="46ad3-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="46ad3-181">Classer les données selon trois niveaux
</span><span class="sxs-lookup"><span data-stu-id="46ad3-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="46ad3-182">Contoso effectué une étude critique et déterminé les trois niveaux, qui a été utilisée pour déterminer le cloud Microsoft offre des fonctionnalités visant à protéger les données stratégiques de Contoso.</span><span class="sxs-lookup"><span data-stu-id="46ad3-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="46ad3-183">Déterminer les stratégies d’accès, de conservation et de protection des informations pour les niveaux de données
</span><span class="sxs-lookup"><span data-stu-id="46ad3-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="46ad3-184">En fonction des niveaux de données, Contoso a déterminé des exigences précises, qui seront utilisées pour qualifier les futures charges de travail informatiques déplacées vers le cloud.</span><span class="sxs-lookup"><span data-stu-id="46ad3-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="46ad3-185">Utilisation de Contoso de meilleures pratiques de sécurité Office 365</span><span class="sxs-lookup"><span data-stu-id="46ad3-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="46ad3-186">Conformément aux Office 365 meilleures pratiques de sécurité administrateurs de sécurité et le service informatique de Contoso ont déployé les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="46ad3-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="46ad3-187">**Des comptes d’administrateur global par mot de passe fort très dédiés**</span><span class="sxs-lookup"><span data-stu-id="46ad3-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="46ad3-p105">Au lieu d’attribuer le rôle d’administrateur global aux comptes d’utilisateur de tous les jours, Contoso a créer trois, des comptes d’administrateur global par mot de passe fort très dédiés. Connexion avec un compte d’administrateur global est effectuée uniquement pour les tâches d’administration spécifiques et les mots de passe sont uniquement connus au personnel désigné. Administrateurs de la sécurité de Contoso disposent des rôles d’administrateur aux comptes appropriés à la fonction de cette personne informatique et responsabilité.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="46ad3-191">Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="46ad3-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="46ad3-192">**Authentification multifacteur (MFA) pour les comptes d’utilisateur importantes**</span><span class="sxs-lookup"><span data-stu-id="46ad3-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="46ad3-p106">MFA ajoute une couche de protection supplémentaire à la procédure de connexion en demandant aux utilisateurs à remercier un appel téléphonique, message texte ou une notification de l’application sur leur téléphone active après avoir entré correctement leur mot de passe. Avec MFA, comptes d’utilisateurs Office 365 sont protégés contre de connexion non autorisée, même si un mot de passe est compromis.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="46ad3-195">Pour vous protéger contre une compromission de l’abonnement à Office 365, Contoso activé MFA sur tous les trois comptes d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="46ad3-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="46ad3-196">Pour vous protéger contre les attaques par hameçonnage, dans laquelle une personne malveillante compromet les informations d’identification d’une personne dans l’organisation approuvée et envoie un message électronique malveillant, Contoso activé MFA sur tous les comptes d’utilisateur pour les responsables, y compris les cadres.</span><span class="sxs-lookup"><span data-stu-id="46ad3-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="46ad3-197">Pour plus d’informations, voir [planifier l’authentification multifacteur pour les déploiements d’Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="46ad3-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="46ad3-198">**Gestion des fonctions avancées de sécurité (ASM)**</span><span class="sxs-lookup"><span data-stu-id="46ad3-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="46ad3-p107">ASM utilise configuré les stratégies pour surveiller l’activité anormale. Définir des alertes avec ASM afin que les administrateurs informatiques sont avertis inhabituelle ou risque d’activités des utilisateurs, telles que le téléchargement de grandes quantités de données, les administrateurs de sécurité Contoso Échec de plusieurs tentatives de connexion ou des connexions à partir des adresses IP inconnus ou dangereuses</span><span class="sxs-lookup"><span data-stu-id="46ad3-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="46ad3-201">Pour plus d’informations, voir [Vue d’ensemble de gestion avancées de sécurité dans Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="46ad3-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="46ad3-202">**Enregistrement d’audit de boîtes aux lettres et flux de messagerie sécurisée**</span><span class="sxs-lookup"><span data-stu-id="46ad3-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="46ad3-p108">Spécialistes de la sécurité Contoso utilisent Exchange Online Protection et Protection de menace avancées (DAV) pour protéger contre les programmes malveillants inconnus, les virus et les URL malveillantes transmis par le biais de messages électroniques. Contoso a également activé enregistrement d’audit pour déterminer qui a ouvert une session dans les boîtes aux lettres utilisateur, envoyés de messages et d’autres activités effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur.</span><span class="sxs-lookup"><span data-stu-id="46ad3-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="46ad3-205">Pour plus d'informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="46ad3-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="46ad3-206">Protection contre le courrier indésirable pour Office 365</span><span class="sxs-lookup"><span data-stu-id="46ad3-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="46ad3-207">Protection avancée contre les menaces pour les pièces jointes et liens fiables</span><span class="sxs-lookup"><span data-stu-id="46ad3-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="46ad3-208">Activer l’audit de boîte aux lettres dans Office 365</span><span class="sxs-lookup"><span data-stu-id="46ad3-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="46ad3-209">**Protection contre la perte de données (DLP)**</span><span class="sxs-lookup"><span data-stu-id="46ad3-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="46ad3-210">Contoso a identifié ses données sensibles et configuré les stratégies DLP pour Exchange Online, SharePoint Online et OneDrive empêcher les utilisateurs d’accidentellement ou intentionnellement partage des données.</span><span class="sxs-lookup"><span data-stu-id="46ad3-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="46ad3-211">Pour plus d’informations, reportez-vous à [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="46ad3-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="46ad3-212">See Also</span><span class="sxs-lookup"><span data-stu-id="46ad3-212">See Also</span></span>

[<span data-ttu-id="46ad3-213">Contoso dans le cloud de Microsoft</span><span class="sxs-lookup"><span data-stu-id="46ad3-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="46ad3-214">Ressources relatives à l'architecture informatique du cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="46ad3-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="46ad3-215">[Feuille de route Enterprise Cloud de Microsoft : ressources pour les décideurs (en anglais)](https://sway.com/FJ2xsyWtkJc2taRD)
</span><span class="sxs-lookup"><span data-stu-id="46ad3-215">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>
  
[<span data-ttu-id="46ad3-216">Meilleures pratiques de sécurité pour Office 365</span><span class="sxs-lookup"><span data-stu-id="46ad3-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




