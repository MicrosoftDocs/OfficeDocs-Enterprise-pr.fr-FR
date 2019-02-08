---
title: Protéger vos comptes d’administrateur général Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Protéger l’accès d’administrateur global à votre abonnement Office 365 avec ces trois étapes.
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897517"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="19395-103">Protéger vos comptes d’administrateur général Office 365</span><span class="sxs-lookup"><span data-stu-id="19395-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="19395-104">**Résumé :** Protéger votre abonnement Office 365 contre les attaques en fonction de la compromission d’un compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="19395-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="19395-p101">Failles de sécurité d’un abonnement à Office 365, notamment la collecte des informations et les attaques par hameçonnage, sont généralement effectuées par compromettre les informations d’identification d’un compte d’administrateur général Office 365. Sécurité dans le nuage est un partenariat entre vous et Microsoft :</span><span class="sxs-lookup"><span data-stu-id="19395-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="19395-p102">Services de cloud computing Microsoft reposent sur une base de gestion de la confidentialité et sécurité. Microsoft vous fournit des contrôles de sécurité et les fonctionnalités pour vous aider à protéger vos données et applications.</span><span class="sxs-lookup"><span data-stu-id="19395-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="19395-109">Vous possédez vos données et des identités et la responsabilité de protection, la sécurité de vos ressources locales et la sécurité des composants de nuage que vous contrôlez.</span><span class="sxs-lookup"><span data-stu-id="19395-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="19395-p103">Microsoft fournit des fonctionnalités pour aider à protéger votre organisation, mais ils sont efficaces uniquement si vous les utilisez. Si vous n’utilisez pas les, vous pouvez être vulnérables aux attaques. Pour protéger vos comptes d’administrateur global, Microsoft est là pour vous aider à obtenir des instructions détaillées pour :</span><span class="sxs-lookup"><span data-stu-id="19395-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="19395-113">Créer des comptes d’administrateur général Office 365 dédiés et utilisez-les uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="19395-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="19395-114">Configurer l’authentification multifacteur pour vos comptes d’administrateur général Office 365 dédiés et utilisez la plus puissante d’authentification secondaire.</span><span class="sxs-lookup"><span data-stu-id="19395-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="19395-115">Activer et configurer la sécurité d’application Office 365 dans le nuage à surveiller pour les activités de compte administrateur global suspects.</span><span class="sxs-lookup"><span data-stu-id="19395-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="19395-116">Bien que cet article se concentre sur les comptes d’administrateur global, vous devez également tenir compte si supplémentaires comptes avec une large gamme d’autorisations pour accéder aux données dans votre abonnement, telles que l’administrateur de la découverte électronique ou de sécurité ou de conformité comptes d’administrateur, doivent être protégées de la même manière.</span><span class="sxs-lookup"><span data-stu-id="19395-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="19395-p104">Étape 1. Créer des comptes d’administrateur général Office 365 dédiés et de les utiliser uniquement lorsque cela est nécessaire</span><span class="sxs-lookup"><span data-stu-id="19395-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="19395-p105">Il existe relativement peu de tâches d’administration, telles que l’affectation de rôles aux comptes d’utilisateurs, qui nécessitent des privilèges d’administrateur global. Par conséquent, au lieu d’utiliser des comptes d’utilisateurs de tous les jours qui ont été attribués le rôle d’administrateur global, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19395-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="19395-p106">Déterminer l’ensemble des comptes d’utilisateurs qui ont été attribués le rôle d’administrateur global. Vous pouvez le faire avec cette commande à l’invite de commandes Microsoft Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="19395-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="19395-123">Connectez-vous à votre abonnement à Office 365 avec un compte d’utilisateur qui a été affecté le rôle d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="19395-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="19395-p107">Créer au moins une et un maximum de cinq dédié comptes d’utilisateur administrateur global. **Utilisation des mots de passe forts au moins 12 caractères long.** Pour plus d’informations, voir [créer un mot de passe](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Stocker les mots de passe pour les nouveaux comptes dans un endroit sûr.</span><span class="sxs-lookup"><span data-stu-id="19395-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="19395-128">Attribuer le rôle d’administrateur global à chacun des comptes d’utilisateur administrateur global nouveau dédié.</span><span class="sxs-lookup"><span data-stu-id="19395-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="19395-129">Vous déconnecter de Office 365.</span><span class="sxs-lookup"><span data-stu-id="19395-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="19395-130">Connectez-vous à l’aide d’une des nouveaux comptes d’utilisateur administrateur global dédié.</span><span class="sxs-lookup"><span data-stu-id="19395-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="19395-131">Pour chaque compte d’utilisateur existant qui a été affecté le rôle d’administrateur global de l’étape 1 :</span><span class="sxs-lookup"><span data-stu-id="19395-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="19395-132">Supprimer le rôle d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="19395-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="19395-p108">Attribuer des rôles d’administrateur au compte qui conviennent à la fonction et la responsabilité de l’utilisateur. Pour plus d’informations sur les différents rôles d’administrateur dans Office 365, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="19395-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="19395-135">Vous déconnecter de Office 365.</span><span class="sxs-lookup"><span data-stu-id="19395-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="19395-136">Le résultat doit être :</span><span class="sxs-lookup"><span data-stu-id="19395-136">The result should be:</span></span>
  
- <span data-ttu-id="19395-p109">Les comptes d’utilisateurs uniquement dans votre abonnement ayant le rôle d’administrateur global sont le nouvel ensemble de comptes d’administrateur global dédié. Vérifier avec la commande PowerShell suivante :</span><span class="sxs-lookup"><span data-stu-id="19395-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="19395-139">Tous les autres comptes d’utilisateur qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur qui sont associés à leurs responsabilités.</span><span class="sxs-lookup"><span data-stu-id="19395-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="19395-p110">À partir de ce moment qui interviennent, vous vous connectez avec les comptes d’administrateur global dédié uniquement pour les tâches qui nécessitent des privilèges d’administrateur global. Tous les autres administration Office 365 doit être effectuée en assignant des autres rôles d’administration aux comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="19395-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="19395-p111">Oui, cela nécessite des étapes supplémentaires pour se déconnecter en tant que votre compte d’utilisateur de tous les jours et connectez-vous avec un compte d’administrateur global dédié. Mais cela seulement doit être effectuée occasionnellement pour les opérations d’administrateur global. Tenez compte des points récupération votre abonnement Office 365 après qu’une violation de compte d’administrateur global nécessite beaucoup plus d’étapes.</span><span class="sxs-lookup"><span data-stu-id="19395-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="19395-p112">Étape 2. Configurer l’authentification multifacteur pour vos comptes d’administrateur général Office 365 dédiés et d’utiliser la plus puissante d’authentification secondaire</span><span class="sxs-lookup"><span data-stu-id="19395-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="19395-p113">L’authentification multifacteur (MFA) pour vos comptes d’administrateur global nécessite des informations supplémentaires au-delà du nom de compte et mot de passe. Office 365 prend en charge ces méthodes de vérification :</span><span class="sxs-lookup"><span data-stu-id="19395-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="19395-149">appel téléphonique ;</span><span class="sxs-lookup"><span data-stu-id="19395-149">A phone call</span></span>
    
- <span data-ttu-id="19395-150">code d'accès généré de façon aléatoire ;</span><span class="sxs-lookup"><span data-stu-id="19395-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="19395-151">carte à puce (virtuelle ou physique) ;</span><span class="sxs-lookup"><span data-stu-id="19395-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="19395-152">appareil biométrique.</span><span class="sxs-lookup"><span data-stu-id="19395-152">A biometric device</span></span>
    
<span data-ttu-id="19395-153">Si vous êtes une petite entreprise qui est à l’aide de comptes d’utilisateurs stockés uniquement dans le nuage (le modèle d’identité dans le nuage), utilisez ces étapes pour configurer MFA à l’aide d’un appel téléphonique ou un code de vérification de message texte envoyé à un téléphone intelligent :</span><span class="sxs-lookup"><span data-stu-id="19395-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="19395-154">[Activer MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="19395-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="19395-155">[Configurer la vérification étape 2 pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) pour configurer chaque dédiée compte d’administrateur global pour l’appel téléphonique ou un message texte en tant que la méthode de vérification.</span><span class="sxs-lookup"><span data-stu-id="19395-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="19395-p114">Si vous êtes une entreprise de grande taille qui utilise un modèle d’identité hybride Office 365, vous disposez de plusieurs options de vérification. Si vous avez l’infrastructure de sécurité déjà en place pour une méthode d’authentification secondaire plus puissante, utilisez les étapes ci-après :</span><span class="sxs-lookup"><span data-stu-id="19395-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="19395-158">[Activer MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="19395-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="19395-159">[Configurer la vérification étape 2 pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) pour configurer chaque dédiée compte d’administrateur global pour la méthode de vérification approprié.</span><span class="sxs-lookup"><span data-stu-id="19395-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="19395-p115">Si l’infrastructure de sécurité de la méthode de vérification renforcée souhaité n’est pas en place et fonctionne pour Office 365 MFA, il est vivement recommandé que vous configurez des comptes d’administrateur global dédié avec MFA à l’aide d’un appel téléphonique ou un message texte code de vérification envoyé vers un téléphone intelligent pour vos comptes d’administrateur global comme mesure de sécurité intermédiaire. Ne laissez pas vos comptes d’administrateur global dédié sans la protection supplémentaire fournie par MFA.</span><span class="sxs-lookup"><span data-stu-id="19395-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="19395-162">Pour plus d’informations, reportez-vous à [Planifier l’authentification multifacteur pour les déploiements Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="19395-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="19395-163">Pour vous connecter aux services Office 365 avec MFA et PowerShell, consultez [cet article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="19395-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="19395-p116">Étape 3. Surveiller les activités de compte administrateur global suspectes</span><span class="sxs-lookup"><span data-stu-id="19395-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="19395-p117">Sécurité d’application Office 365 Cloud vous permet de créer des stratégies pour vous informer du comportement suspect dans votre abonnement. Sécurité d’application dans le nuage est intégré dans Office 365 E5, mais il est également disponible en tant que service séparé. Par exemple, si vous n’avez pas Office 365 E5, vous pouvez acheter des licences dans le nuage application sécurité individuelles pour les comptes d’utilisateur qui sont affectées à l’administrateur global, administrateur de sécurité et rôles d’administrateur de conformité.</span><span class="sxs-lookup"><span data-stu-id="19395-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="19395-169">Si vous disposez de sécurité d’application Cloud dans votre abonnement Office 365, utilisez les étapes ci-après :</span><span class="sxs-lookup"><span data-stu-id="19395-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="19395-170">Connectez-vous au portail Office 365 avec un compte qui est affecté le rôle d’administrateur de sécurité ou l’administrateur de la conformité.</span><span class="sxs-lookup"><span data-stu-id="19395-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="19395-171">[Activer la sécurité d’application Office 365 dans le nuage](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="19395-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="19395-172">Passez en revue vos [stratégies de détection des anomalies dans Office 365 Cloud application sécurité](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) pour vous informer par courrier électronique de modèles anormales de l’activité administrative privilégiée.</span><span class="sxs-lookup"><span data-stu-id="19395-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="19395-173">Pour ajouter un compte d’utilisateur au rôle administrateur de sécurité, [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) avec un compte d’administrateur global dédié et MFA, renseignez le nom d’utilisateur principal du compte d’utilisateur, puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="19395-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="19395-174">Pour ajouter un compte d’utilisateur au rôle administrateur de conformité, renseignez le nom d’utilisateur principal du compte d’utilisateur, puis exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="19395-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="19395-175">Protections supplémentaires pour les entreprises</span><span class="sxs-lookup"><span data-stu-id="19395-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="19395-176">Une fois les étapes 1 à 3, utilisent ces méthodes supplémentaires pour s’assurer que votre compte d’administrateur global et la configuration que vous effectuez l’utiliser, sont aussi sécurisé que possible.</span><span class="sxs-lookup"><span data-stu-id="19395-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="19395-177">Station de travail d’un accès privilégié (patte)</span><span class="sxs-lookup"><span data-stu-id="19395-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="19395-p118">Pour vérifier que l’exécution de tâches doté de privilèges élevés est aussi sécurisée que possible, utilisez une patte. Une patte est un ordinateur dédié qui est utilisé uniquement pour les tâches de configuration sensibles, tels que de la configuration d’Office 365 qui nécessite un compte d’administrateur global. Cet ordinateur n’étant pas utilisé tous les jours pour la navigation sur Internet ou par courrier électronique, il est mieux protégé contre les menaces et les attaques Internet.</span><span class="sxs-lookup"><span data-stu-id="19395-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="19395-181">Pour obtenir des instructions sur la façon de configurer une patte, voir [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="19395-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="19395-182">Gestion des identités Azure AD privilégié (GIP)</span><span class="sxs-lookup"><span data-stu-id="19395-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="19395-183">Au lieu de devoir vos comptes d’administrateur global d’être définitivement attribuer le rôle Administrateur général, vous pouvez utiliser Azure AD GIP pour permettre à la demande, juste-à-temps attribution du rôle Administrateur général lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="19395-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="19395-p119">Au lieu de vos comptes d’administrateur global en cours d’un administrateur définitif, ils deviennent des administrateurs éligibles. Le rôle d’administrateur global est inactif jusqu'à ce que quelqu'un a besoin. Vous pouvez ensuite compléter un processus d’activation pour ajouter le rôle Administrateur général pour le compte d’administrateur général pour un laps de temps prédéfini. Lors de l’expiration du délai, GIP supprime le rôle d’administrateur global à partir du compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="19395-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="19395-188">À l’aide de GIP et ce processus réduit considérablement la durée de vos comptes d’administrateur global sont vulnérables aux attaques et à utiliser par les utilisateurs malveillants.</span><span class="sxs-lookup"><span data-stu-id="19395-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="19395-189">Pour plus d’informations, voir [Gestion des identités configurer Azure AD privilégié](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="19395-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="19395-190">GIP est disponible avec Azure Active Directory Premium P2, qui est inclus avec la mobilité d’entreprise + E5 de sécurité (EMS), ou vous pouvez acheter des licences individuelles pour vos comptes d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="19395-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="19395-191">Logiciel de gestion (SIEM) des informations et des événements sécurité de journalisation d’Office 365</span><span class="sxs-lookup"><span data-stu-id="19395-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="19395-p120">SIEM s’exécutent sur un serveur effectue une analyse en temps réel des alertes de sécurité et des événements créés par les applications et le matériel réseau. Pour autoriser votre serveur SIEM à inclure des événements et alertes de sécurité Office 365 dans son analyse et de génération de rapports, vous pouvez intégrer dans votre système SIEM :</span><span class="sxs-lookup"><span data-stu-id="19395-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="19395-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="19395-194">Azure AD</span></span>
    
    <span data-ttu-id="19395-195">Pour plus d’informations, voir les [journaux d’intégrer des ressources Azure dans vos systèmes SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="19395-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="19395-196">Sécurité de l’application cloud Office 365</span><span class="sxs-lookup"><span data-stu-id="19395-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="19395-197">Pour plus d’informations, voir [intégrer votre serveur SIEM avec Office 365 Cloud Application Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="19395-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="19395-198">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="19395-198">Next step</span></span>

<span data-ttu-id="19395-199">Voir [meilleures pratiques de sécurité pour Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="19395-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

