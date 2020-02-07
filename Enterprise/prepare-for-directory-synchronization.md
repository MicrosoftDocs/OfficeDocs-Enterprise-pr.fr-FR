---
title: Préparer la synchronisation d’annuaires vers Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment préparer la mise en service des utilisateurs vers Office 365 à l’aide de la synchronisation d’annuaires et des avantages à long terme de cette méthode.
ms.openlocfilehash: 948db4d5dca8d5deb9844ff9a7ec652653a5ab6b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841171"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="018a0-103">Préparer la synchronisation d’annuaires vers Office 365</span><span class="sxs-lookup"><span data-stu-id="018a0-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="018a0-104">*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.</span><span class="sxs-lookup"><span data-stu-id="018a0-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="018a0-105">Les avantages de la synchronisation hybride des identités et des annuaires de votre organisation sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="018a0-105">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="018a0-106">Réduction des programmes d’administration au sein de votre organisation</span><span class="sxs-lookup"><span data-stu-id="018a0-106">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="018a0-107">Activer le scénario d’authentification unique (facultatif)</span><span class="sxs-lookup"><span data-stu-id="018a0-107">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="018a0-108">Automatisation des modifications de compte dans Office 365</span><span class="sxs-lookup"><span data-stu-id="018a0-108">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="018a0-109">Pour plus d’informations sur les avantages liés à l’utilisation de la synchronisation d’annuaires, consultez la rubrique feuille de [route de synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525398) et [identité hybride pour Office 365](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="018a0-109">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="018a0-110">Toutefois, la synchronisation d’annuaires nécessite une planification et une préparation afin de s’assurer que vos services de domaine Active Directory (AD DS) sont synchronisés avec le client Azure Active Directory (Azure AD) de votre abonnement Office 365 avec un minimum d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="018a0-110">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="018a0-111">Suivez les étapes ci-dessous pour obtenir les meilleurs résultats.</span><span class="sxs-lookup"><span data-stu-id="018a0-111">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="018a0-112">1. tâches de nettoyage d’annuaire</span><span class="sxs-lookup"><span data-stu-id="018a0-112">1. Directory cleanup tasks</span></span>

<span data-ttu-id="018a0-113">Avant de synchroniser vos services AD DS avec votre client Azure AD, vous devez nettoyer votre service AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-113">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="018a0-114">Si vous n’effectuez pas le nettoyage AD DS avant la synchronisation, le processus de déploiement peut avoir un impact significatif.</span><span class="sxs-lookup"><span data-stu-id="018a0-114">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="018a0-115">Cela peut prendre des jours, voire des semaines, pour parcourir le cycle de synchronisation d’annuaires, l’identification des erreurs et la resynchronisation.</span><span class="sxs-lookup"><span data-stu-id="018a0-115">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="018a0-116">Dans votre AD DS, effectuez les tâches de nettoyage suivantes pour chaque compte d’utilisateur auquel est attribuée une licence Office 365 :</span><span class="sxs-lookup"><span data-stu-id="018a0-116">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="018a0-117">Assurez-vous d’une adresse de messagerie unique et valide dans l’attribut **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="018a0-117">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
  
2. <span data-ttu-id="018a0-118">Supprimez toutes les valeurs en double dans l’attribut **proxyAddresses** .</span><span class="sxs-lookup"><span data-stu-id="018a0-118">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="018a0-119">Dans la mesure du possible, vérifiez que la valeur de l’attribut **userPrincipalName** est valide et unique dans l’objet **User** de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="018a0-119">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="018a0-120">Pour une expérience de synchronisation optimale, vérifiez que l’UPN AD DS correspond à l’UPN Azure AD.</span><span class="sxs-lookup"><span data-stu-id="018a0-120">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="018a0-121">Si un utilisateur n’a pas de valeur pour l’attribut **userPrincipalName** , l’objet **User** doit contenir une valeur valide et unique pour l’attribut **sAMAccountName** .</span><span class="sxs-lookup"><span data-stu-id="018a0-121">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="018a0-122">Supprimez toutes les valeurs en double dans l’attribut **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="018a0-122">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="018a0-123">Pour une utilisation optimale de la liste d’adresses globale (LAG), assurez-vous que les informations figurant dans les attributs suivants du compte d’utilisateur AD DS sont correctes :</span><span class="sxs-lookup"><span data-stu-id="018a0-123">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="018a0-124">givenName</span><span class="sxs-lookup"><span data-stu-id="018a0-124">givenName</span></span>
  - <span data-ttu-id="018a0-125">surname</span><span class="sxs-lookup"><span data-stu-id="018a0-125">surname</span></span>
  - <span data-ttu-id="018a0-126">displayName</span><span class="sxs-lookup"><span data-stu-id="018a0-126">displayName</span></span>
  - <span data-ttu-id="018a0-127">Fonction</span><span class="sxs-lookup"><span data-stu-id="018a0-127">Job Title</span></span>
  - <span data-ttu-id="018a0-128">Service</span><span class="sxs-lookup"><span data-stu-id="018a0-128">Department</span></span>
  - <span data-ttu-id="018a0-129">Bureau</span><span class="sxs-lookup"><span data-stu-id="018a0-129">Office</span></span>
  - <span data-ttu-id="018a0-130">Téléphone (bureau)</span><span class="sxs-lookup"><span data-stu-id="018a0-130">Office Phone</span></span>
  - <span data-ttu-id="018a0-131">Téléphone mobile</span><span class="sxs-lookup"><span data-stu-id="018a0-131">Mobile Phone</span></span>
  - <span data-ttu-id="018a0-132">Numéro de télécopie</span><span class="sxs-lookup"><span data-stu-id="018a0-132">Fax Number</span></span>
  - <span data-ttu-id="018a0-133">Rue</span><span class="sxs-lookup"><span data-stu-id="018a0-133">Street Address</span></span>
  - <span data-ttu-id="018a0-134">Ville</span><span class="sxs-lookup"><span data-stu-id="018a0-134">City</span></span>
  - <span data-ttu-id="018a0-135">Département ou région</span><span class="sxs-lookup"><span data-stu-id="018a0-135">State or Province</span></span>
  - <span data-ttu-id="018a0-136">Code postal</span><span class="sxs-lookup"><span data-stu-id="018a0-136">Zip or Postal Code</span></span>
  - <span data-ttu-id="018a0-137">Pays ou région</span><span class="sxs-lookup"><span data-stu-id="018a0-137">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="018a0-138">2. préparation de l’objet et des attributs de l’annuaire</span><span class="sxs-lookup"><span data-stu-id="018a0-138">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="018a0-139">La réussite de la synchronisation d’annuaires entre vos services de domaine Active Directory et Office 365 nécessite que vos attributs AD DS soient correctement préparés.</span><span class="sxs-lookup"><span data-stu-id="018a0-139">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="018a0-140">Par exemple, vous devez vous assurer que des caractères spécifiques ne sont pas utilisés dans certains attributs synchronisés avec l’environnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-140">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="018a0-141">Les caractères inattendus ne provoquent pas l’échec de la synchronisation d’annuaires, mais peuvent renvoyer un avertissement.</span><span class="sxs-lookup"><span data-stu-id="018a0-141">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="018a0-142">Les caractères non valides entraînent l’échec de la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="018a0-142">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="018a0-143">La synchronisation d’annuaires échoue également si certains de vos utilisateurs AD DS possèdent un ou plusieurs attributs en double.</span><span class="sxs-lookup"><span data-stu-id="018a0-143">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="018a0-144">Chaque utilisateur doit avoir des attributs uniques.</span><span class="sxs-lookup"><span data-stu-id="018a0-144">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="018a0-145">Les attributs que vous devez préparer sont répertoriés ici :</span><span class="sxs-lookup"><span data-stu-id="018a0-145">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="018a0-146">**displayName**</span><span class="sxs-lookup"><span data-stu-id="018a0-146">**displayName**</span></span>
    
  - <span data-ttu-id="018a0-147">Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-147">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="018a0-148">Si cet attribut existe dans l’objet User, il doit y avoir une valeur pour lui.</span><span class="sxs-lookup"><span data-stu-id="018a0-148">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="018a0-149">Autrement dit, l’attribut ne doit pas être vide.</span><span class="sxs-lookup"><span data-stu-id="018a0-149">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="018a0-150">Nombre maximal de caractères : 256</span><span class="sxs-lookup"><span data-stu-id="018a0-150">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="018a0-151">**givenName**</span><span class="sxs-lookup"><span data-stu-id="018a0-151">**givenName**</span></span>
    
  - <span data-ttu-id="018a0-152">Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 ne l’exige pas ou ne l’utilise pas.</span><span class="sxs-lookup"><span data-stu-id="018a0-152">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="018a0-153">Nombre maximal de caractères : 64</span><span class="sxs-lookup"><span data-stu-id="018a0-153">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="018a0-154">**e-mails**</span><span class="sxs-lookup"><span data-stu-id="018a0-154">**mail**</span></span>
    
  - <span data-ttu-id="018a0-155">La valeur de l’attribut doit être unique dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-155">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="018a0-156">S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé.</span><span class="sxs-lookup"><span data-stu-id="018a0-156">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="018a0-157">Les utilisateurs suivants n’apparaîtront pas dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-157">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="018a0-158">Vous devez modifier la valeur dans Office 365 ou modifier les deux valeurs dans AD DS afin que les deux utilisateurs apparaissent dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-158">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="018a0-159">**mailnickname** (alias Exchange)</span><span class="sxs-lookup"><span data-stu-id="018a0-159">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="018a0-160">La valeur de l’attribut ne peut pas commencer par un point (.).</span><span class="sxs-lookup"><span data-stu-id="018a0-160">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="018a0-161">La valeur de l’attribut doit être unique dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-161">The attribute value must be unique within the directory.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="018a0-162">Les traits de soulignement (« _ ») dans le nom synchronisé indiquent que la valeur d’origine de cet attribut contient des caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="018a0-162">Underscores ("_") in the synchronized name indicates that the original value of this attribute contains invalid characters.</span></span> <span data-ttu-id="018a0-163">La valeur d’origine peut contenir des lettres, des chiffres et les caractères !, #, $,%, &, \*',, +,-,/, =, ?, ^, _, ', {, |,} et ~.</span><span class="sxs-lookup"><span data-stu-id="018a0-163">The original value can contain letters, numbers, and the characters !, #, $, %, &, ', \*, +, -, /, =, ?, ^, _, \`, {, |, } and ~.</span></span> <span data-ttu-id="018a0-164">Pour plus d’informations sur cet attribut, consultez la rubrique [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span><span class="sxs-lookup"><span data-stu-id="018a0-164">For more information on this attribute, see [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span></span>
    >
      
- <span data-ttu-id="018a0-165">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="018a0-165">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="018a0-166">Attribut à valeurs multiples</span><span class="sxs-lookup"><span data-stu-id="018a0-166">Multiple-value attribute</span></span>
  - <span data-ttu-id="018a0-167">Nombre maximal de caractères par valeur : 256</span><span class="sxs-lookup"><span data-stu-id="018a0-167">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="018a0-168">La valeur de l’attribut ne doit pas contenir d’espace.</span><span class="sxs-lookup"><span data-stu-id="018a0-168">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="018a0-169">La valeur de l’attribut doit être unique dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-169">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="018a0-170">Caractères non valides : \< \> (); , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="018a0-170">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="018a0-171">Notez que les caractères non valides s’appliquent aux caractères qui suivent le délimiteur de type et à «  : », ce qui signifie que SMTP :User@contso.com est autorisé, mais SMTP :user :M@contoso.com ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="018a0-171">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="018a0-172">Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="018a0-172">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="018a0-173">S’il existe des adresses en double ou indésirables, consultez la rubrique d’aide [suppression des adresses de proxy en double et indésirables dans Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="018a0-173">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="018a0-174">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="018a0-174">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="018a0-175">Nombre maximal de caractère : 20</span><span class="sxs-lookup"><span data-stu-id="018a0-175">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="018a0-176">La valeur de l’attribut doit être unique dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-176">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="018a0-177">Caractères non valides : [\ "|, \< \> / : + =;?</span><span class="sxs-lookup"><span data-stu-id="018a0-177">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="018a0-178">\* ']</span><span class="sxs-lookup"><span data-stu-id="018a0-178">\* ']</span></span>
  - <span data-ttu-id="018a0-179">Si un utilisateur a un attribut **sAMAccountName** non valide mais qu’il dispose d’un attribut **userPrincipalName** valide, le compte d’utilisateur est créé dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-179">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="018a0-180">Si **sAMAccountName** et **userPrincipalName** sont tous deux incorrects, l’attribut **userPrincipalName** AD DS doit être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="018a0-180">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="018a0-181">**sn** (nom)</span><span class="sxs-lookup"><span data-stu-id="018a0-181">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="018a0-182">Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Office 365, mais Office 365 ne l’exige pas ou ne l’utilise pas.</span><span class="sxs-lookup"><span data-stu-id="018a0-182">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="018a0-183">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="018a0-183">**targetAddress**</span></span>
    
    <span data-ttu-id="018a0-184">Il est nécessaire que l’attribut **TargetAddress** (par exemple, SMTP :Tom@contoso.com) qui est rempli pour l’utilisateur doit apparaître dans la lag Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-184">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="018a0-185">Dans les scénarios de migration de messagerie tiers, cela nécessite l’extension de schéma Office 365 pour les services de domaine Active Directory.</span><span class="sxs-lookup"><span data-stu-id="018a0-185">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="018a0-186">L’extension de schéma Office 365 ajoutera également d’autres attributs utiles pour gérer les objets Office 365 qui sont renseignés à l’aide d’un outil de synchronisation d’annuaires à partir d’AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-186">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="018a0-187">Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution est ajouté.</span><span class="sxs-lookup"><span data-stu-id="018a0-187">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="018a0-188">Nombre maximal de caractères : 256</span><span class="sxs-lookup"><span data-stu-id="018a0-188">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="018a0-189">La valeur de l’attribut ne doit pas contenir d’espace.</span><span class="sxs-lookup"><span data-stu-id="018a0-189">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="018a0-190">La valeur de l’attribut doit être unique dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-190">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="018a0-191">Caractères non valides \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="018a0-191">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="018a0-192">Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="018a0-192">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="018a0-193">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="018a0-193">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="018a0-194">L’attribut **userPrincipalName** doit être au format de connexion de style Internet où le nom d’utilisateur est suivi par le signe arobase (@) et un nom de domaine : par exemple, user@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="018a0-194">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="018a0-195">Toutes les adresses SMTP (simple mail transport Protocol) doivent respecter les normes de messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="018a0-195">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="018a0-196">Le nombre maximal de caractères pour l’attribut **userPrincipalName** est 113.</span><span class="sxs-lookup"><span data-stu-id="018a0-196">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="018a0-197">Un nombre de caractères spécifique est autorisé avant et après le signe @, comme suit :</span><span class="sxs-lookup"><span data-stu-id="018a0-197">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="018a0-198">Nombre maximal de caractères pour le nom d’utilisateur devant le signe arobase (@) : 64</span><span class="sxs-lookup"><span data-stu-id="018a0-198">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="018a0-199">Nombre maximal de caractères pour le nom de domaine qui suit le signe arobase (@) : 48</span><span class="sxs-lookup"><span data-stu-id="018a0-199">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="018a0-200">Caractères non valides : &amp; \* \% +/= ?</span><span class="sxs-lookup"><span data-stu-id="018a0-200">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="018a0-201">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="018a0-201">{ } | \< \> ( ) ; : , [ ] " '</span></span>
  - <span data-ttu-id="018a0-202">Un tréma est également un caractère non valide.</span><span class="sxs-lookup"><span data-stu-id="018a0-202">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="018a0-203">Le caractère @ est requis dans chaque valeur **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="018a0-203">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="018a0-204">Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="018a0-204">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="018a0-205">Le nom d’utilisateur ne peut pas se terminer par un point (.&amp;), une esperluette (), un espace ou un signe arobase (@).</span><span class="sxs-lookup"><span data-stu-id="018a0-205">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="018a0-206">Le nom d’utilisateur ne peut pas contenir d’espaces.</span><span class="sxs-lookup"><span data-stu-id="018a0-206">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="018a0-207">Les domaines routables doivent être utilisés ; par exemple, les domaines locaux ou internes ne peuvent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="018a0-207">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="018a0-208">Unicode est converti en caractères de trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="018a0-208">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="018a0-209">**userPrincipalName** ne peut pas contenir de valeurs en double dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-209">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="018a0-210">Voir [Prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) pour utiliser l’outil IdFix pour identifier les erreurs dans les attributs de votre AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-210">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="018a0-211">3. préparer l’attribut userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="018a0-211">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="018a0-212">Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation de se connecter à votre annuaire à l’aide de **sAMAccountName** ou de **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="018a0-212">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="018a0-213">De même, les utilisateurs finaux peuvent se connecter à Office 365 à l’aide du nom d’utilisateur principal (UPN) de leur compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="018a0-213">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="018a0-214">La synchronisation d’annuaires tente de créer des utilisateurs dans Azure Active Directory à l’aide du même nom d’utilisateur principal qui se trouve dans votre AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-214">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="018a0-215">Le nom d’utilisateur principal est mis en forme comme une adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="018a0-215">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="018a0-216">Dans Office 365, le nom d’utilisateur principal est l’attribut par défaut utilisé pour générer l’adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="018a0-216">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="018a0-217">Il est facile d’obtenir le **userPrincipalName** (dans AD DS et dans Azure AD) et l’adresse de messagerie principale dans **proxyAddresses** définie sur différentes valeurs.</span><span class="sxs-lookup"><span data-stu-id="018a0-217">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="018a0-218">Lorsqu’elles sont définies sur des valeurs différentes, les administrateurs et les utilisateurs finaux peuvent être confondus.</span><span class="sxs-lookup"><span data-stu-id="018a0-218">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="018a0-219">Il est préférable d’aligner ces attributs afin de réduire la confusion.</span><span class="sxs-lookup"><span data-stu-id="018a0-219">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="018a0-220">Pour répondre aux exigences de l’authentification unique avec les services ADFS (Active Directory Federation Services) 2,0, vous devez vous assurer que l’UPN dans Azure Active Directory et votre AD DS correspondent et utilise un espace de noms de domaine valide.</span><span class="sxs-lookup"><span data-stu-id="018a0-220">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="018a0-221">4. Ajoutez un autre suffixe UPN à AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-221">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="018a0-222">Vous devrez peut-être ajouter un autre suffixe UPN pour associer les informations d’identification d’entreprise de l’utilisateur à l’environnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="018a0-222">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="018a0-223">Un suffixe UPN est la partie d’un UPN située à droite du caractère @.</span><span class="sxs-lookup"><span data-stu-id="018a0-223">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="018a0-224">Les UPN qui sont utilisés pour l’authentification unique peuvent contenir des lettres, des chiffres, des points, des traits d’unions et des traits de soulignement, mais aucun autre type de caractère.</span><span class="sxs-lookup"><span data-stu-id="018a0-224">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="018a0-225">Pour plus d’informations sur l’ajout d’un autre suffixe UPN à Active Directory, consultez la rubrique [préparer la synchronisation d’annuaires]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="018a0-225">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="018a0-226">5. faire correspondre l’UPN AD DS avec l’UPN Office 365</span><span class="sxs-lookup"><span data-stu-id="018a0-226">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="018a0-227">Si vous avez déjà configuré la synchronisation d’annuaires, il se peut que l’UPN de l’utilisateur pour Office 365 ne corresponde pas à l’UPN AD DS de l’utilisateur défini dans votre AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-227">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="018a0-228">Cela peut se produire lorsqu’un utilisateur obtient une licence avant la vérification du domaine.</span><span class="sxs-lookup"><span data-stu-id="018a0-228">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="018a0-229">Pour résoudre ce problème, utilisez [PowerShell pour corriger le nom UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730) afin de mettre à jour l’UPN de l’utilisateur afin de s’assurer que l’upn Office 365 correspond au nom d’utilisateur et au domaine de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="018a0-229">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="018a0-230">Si vous mettez à jour l’UPN dans AD DS et souhaitez le synchroniser avec l’identité Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Office 365 avant d’apporter les modifications dans AD DS.</span><span class="sxs-lookup"><span data-stu-id="018a0-230">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="018a0-231">Découvrez également [Comment préparer un domaine non routable (par exemple, le domaine. local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="018a0-231">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="018a0-232">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="018a0-232">Next steps</span></span>

<span data-ttu-id="018a0-233">Consultez [la rubrique prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) pour vous aider à corriger les erreurs dans les attributs de votre AD DS avant la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="018a0-233">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="018a0-234">Si vous avez corrigé toutes les erreurs d’attribut identifiées avec l’outil IdFix et que vous avez terminé les étapes 1 à 5 ci-dessus, voir [configurer la synchronisation d’annuaires](set-up-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="018a0-234">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
