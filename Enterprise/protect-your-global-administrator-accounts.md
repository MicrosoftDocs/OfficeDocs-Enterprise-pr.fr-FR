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
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540578"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Protéger vos comptes d’administrateur général Office 365

 **Résumé :** Protéger votre abonnement Office 365 contre les attaques en fonction de la compromission d’un compte d’administrateur global. 
  
Failles de sécurité d’un abonnement à Office 365, notamment la collecte des informations et les attaques par hameçonnage, sont généralement effectuées par compromettre les informations d’identification d’un compte d’administrateur général Office 365. Sécurité dans le nuage est un partenariat entre vous et Microsoft :
  
- Services de cloud computing Microsoft reposent sur une base de gestion de la confidentialité et sécurité. Microsoft vous fournit des contrôles de sécurité et les fonctionnalités pour vous aider à protéger vos données et applications.
    
- Vous possédez vos données et des identités et la responsabilité de protection, la sécurité de vos ressources locales et la sécurité des composants de nuage que vous contrôlez.
    
Microsoft fournit des fonctionnalités pour aider à protéger votre organisation, mais ils sont efficaces uniquement si vous les utilisez. Si vous n’utilisez pas les, vous pouvez être vulnérables aux attaques. Pour protéger vos comptes d’administrateur global, Microsoft est là pour vous aider à obtenir des instructions détaillées pour :
  
1. Créer des comptes d’administrateur général Office 365 dédiés et utilisez-les uniquement lorsque cela est nécessaire.
    
2. Configurer l’authentification multifacteur pour vos comptes d’administrateur général Office 365 dédiés et utilisez la plus puissante d’authentification secondaire.
    
3. Activer et configurer la sécurité d’application Office 365 dans le nuage à surveiller pour les activités de compte administrateur global suspects.
    
> [!NOTE]
> Bien que cet article se concentre sur les comptes d’administrateur global, vous devez également tenir compte si supplémentaires comptes avec une large gamme d’autorisations pour accéder aux données dans votre abonnement, telles que l’administrateur de la découverte électronique ou de sécurité ou de conformité comptes d’administrateur, doivent être protégées de la même manière. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Étape 1. Créer des comptes d’administrateur général Office 365 dédiés et de les utiliser uniquement lorsque cela est nécessaire

Il existe relativement peu de tâches d’administration, telles que l’affectation de rôles aux comptes d’utilisateurs, qui nécessitent des privilèges d’administrateur global. Par conséquent, au lieu d’utiliser des comptes d’utilisateurs de tous les jours qui ont été attribués le rôle d’administrateur global, procédez comme suit :
  
1. Déterminer l’ensemble des comptes d’utilisateurs qui ont été attribués le rôle d’administrateur global. Vous pouvez le faire avec cette commande à l’invite de commandes Microsoft Azure Active Directory Module pour Windows PowerShell :
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Connectez-vous à votre abonnement à Office 365 avec un compte d’utilisateur qui a été affecté le rôle d’administrateur global.
    
3. Créer au moins une et un maximum de cinq dédié comptes d’utilisateur administrateur global. **Utilisation des mots de passe forts au moins 12 caractères long.** Pour plus d’informations, voir [créer un mot de passe](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Stocker les mots de passe pour les nouveaux comptes dans un endroit sûr. 
    
4. Attribuer le rôle d’administrateur global à chacun des comptes d’utilisateur administrateur global nouveau dédié.
    
5. Vous déconnecter de Office 365.
    
6. Connectez-vous à l’aide d’une des nouveaux comptes d’utilisateur administrateur global dédié.
    
7. Pour chaque compte d’utilisateur existant qui a été affecté le rôle d’administrateur global de l’étape 1 :
    
  - Supprimer le rôle d’administrateur global.
    
  - Attribuer des rôles d’administrateur au compte qui conviennent à la fonction et la responsabilité de l’utilisateur. Pour plus d’informations sur les différents rôles d’administrateur dans Office 365, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Vous déconnecter de Office 365.
    
Le résultat doit être :
  
- Les comptes d’utilisateurs uniquement dans votre abonnement ayant le rôle d’administrateur global sont le nouvel ensemble de comptes d’administrateur global dédié. Vérifier avec la commande PowerShell suivante :
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Tous les autres comptes d’utilisateur qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur qui sont associés à leurs responsabilités.
    
À partir de ce moment qui interviennent, vous vous connectez avec les comptes d’administrateur global dédié uniquement pour les tâches qui nécessitent des privilèges d’administrateur global. Tous les autres administration Office 365 doit être effectuée en assignant des autres rôles d’administration aux comptes d’utilisateur.
  
> [!NOTE]
> Oui, cela nécessite des étapes supplémentaires pour se déconnecter en tant que votre compte d’utilisateur de tous les jours et connectez-vous avec un compte d’administrateur global dédié. Mais cela seulement doit être effectuée occasionnellement pour les opérations d’administrateur global. Tenez compte des points récupération votre abonnement Office 365 après qu’une violation de compte d’administrateur global nécessite beaucoup plus d’étapes. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Étape 2. Configurer l’authentification multifacteur pour vos comptes d’administrateur général Office 365 dédiés et d’utiliser la plus puissante d’authentification secondaire

L’authentification multifacteur (MFA) pour vos comptes d’administrateur global nécessite des informations supplémentaires au-delà du nom de compte et mot de passe. Office 365 prend en charge ces méthodes de vérification :
  
- Un appel téléphonique
    
- Un code secret généré de manière aléatoire
    
- Une carte à puce (virtuelle ou physique)
    
- Un périphérique biométrique
    
Si vous êtes une petite entreprise qui est à l’aide de comptes d’utilisateurs stockés uniquement dans le nuage (le modèle d’identité dans le nuage), utilisez ces étapes pour configurer MFA à l’aide d’un appel téléphonique ou un code de vérification de message texte envoyé à un téléphone intelligent :
  
1. [Activer MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configurer la vérification étape 2 pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) pour configurer chaque dédiée compte d’administrateur global pour l’appel téléphonique ou un message texte en tant que la méthode de vérification. 
    
Si vous êtes une entreprise de grande taille qui utilise un modèle d’identité hybride Office 365, vous disposez de plusieurs options de vérification. Si vous avez l’infrastructure de sécurité déjà en place pour une méthode d’authentification secondaire plus puissante, utilisez les étapes ci-après :
  
1. [Activer MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configurer la vérification étape 2 pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) pour configurer chaque dédiée compte d’administrateur global pour la méthode de vérification approprié. 
    
Si l’infrastructure de sécurité de la méthode de vérification renforcée souhaité n’est pas en place et fonctionne pour Office 365 MFA, il est vivement recommandé que vous configurez des comptes d’administrateur global dédié avec MFA à l’aide d’un appel téléphonique ou un message texte code de vérification envoyé vers un téléphone intelligent pour vos comptes d’administrateur global comme mesure de sécurité intermédiaire. Ne laissez pas vos comptes d’administrateur global dédié sans la protection supplémentaire fournie par MFA.
  
Pour plus d’informations, reportez-vous à [Planifier l’authentification multifacteur pour les déploiements Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Pour vous connecter aux services Office 365 avec MFA et PowerShell, consultez [cet article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Étape 3. Surveiller les activités de compte administrateur global suspectes

Sécurité d’application Office 365 dans le nuage permet de vous permet de créer des stratégies pour vous informer du comportement suspect dans votre abonnement. Sécurité d’application dans le nuage est intégré dans Office 365 E5, mais il est également disponible en tant que service séparé. Par exemple, si vous n’avez pas Office 365 E5, vous pouvez acheter des licences dans le nuage application sécurité individuelles pour les comptes d’utilisateur qui sont affectées à l’administrateur global, administrateur de sécurité et rôles d’administrateur de conformité.
  
Si vous disposez de sécurité d’application Cloud dans votre abonnement Office 365, utilisez les étapes ci-après :
  
1. Connectez-vous au portail Office 365 avec un compte qui est affecté le rôle d’administrateur de sécurité ou l’administrateur de la conformité.
    
2. [Activer la sécurité d’application Office 365 dans le nuage](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Passez en revue vos [stratégies de détection des anomalies dans Office 365 Cloud application sécurité](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) pour vous informer par courrier électronique de modèles anormales de l’activité administrative privilégiée. 
    
Pour ajouter un compte d’utilisateur au rôle administrateur de sécurité, [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) avec un compte d’administrateur global dédié et MFA, renseignez le nom d’utilisateur principal du compte d’utilisateur, puis exécutez les commandes suivantes : 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Pour ajouter un compte d’utilisateur au rôle administrateur de conformité, renseignez le nom d’utilisateur principal du compte d’utilisateur, puis exécutez les commandes suivantes :
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Protections supplémentaires pour les entreprises

Une fois les étapes 1 à 3, utilisent ces méthodes supplémentaires pour s’assurer que votre compte d’administrateur global et la configuration que vous effectuez l’utiliser, sont aussi sécurisé que possible.
  
### <a name="privileged-access-workstation-paw"></a>Station de travail d’un accès privilégié (patte)

Pour vérifier que l’exécution de tâches doté de privilèges élevés est aussi sécurisée que possible, utilisez une patte. Une patte est un ordinateur dédié qui est utilisé uniquement pour les tâches de configuration sensibles, tels que de la configuration d’Office 365 qui nécessite un compte d’administrateur global. Cet ordinateur n’étant pas utilisé tous les jours pour la navigation sur Internet ou par courrier électronique, il est mieux protégé contre les menaces et les attaques Internet.
  
Pour obtenir des instructions sur la façon de configurer une patte, voir [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gestion des identités Azure AD privilégié (GIP)

Au lieu de devoir vos comptes d’administrateur global d’être définitivement attribuer le rôle Administrateur général, vous pouvez utiliser Azure AD GIP pour permettre à la demande, juste-à-temps attribution du rôle Administrateur général lorsque cela est nécessaire.
  
Au lieu de vos comptes d’administrateur global en cours d’un administrateur définitif, ils deviennent des administrateurs éligibles. Le rôle d’administrateur global est inactif jusqu'à ce que quelqu'un a besoin. Vous pouvez ensuite compléter un processus d’activation pour ajouter le rôle Administrateur général pour le compte d’administrateur général pour un laps de temps prédéfini. Lors de l’expiration du délai, GIP supprime le rôle d’administrateur global à partir du compte d’administrateur global.
  
À l’aide de GIP et ce processus réduit considérablement la durée de vos comptes d’administrateur global sont vulnérables aux attaques et à utiliser par les utilisateurs malveillants.
  
Pour plus d’informations, voir [Gestion des identités configurer Azure AD privilégié](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> GIP est disponible avec Azure Active Directory Premium P2, qui est inclus avec la mobilité d’entreprise + E5 de sécurité (EMS), ou vous pouvez acheter des licences individuelles pour vos comptes d’administrateur global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Logiciel de gestion (SIEM) des informations et des événements sécurité de journalisation d’Office 365

SIEM s’exécutent sur un serveur effectue une analyse en temps réel des alertes de sécurité et des événements créés par les applications et le matériel réseau. Pour autoriser votre serveur SIEM à inclure des événements et alertes de sécurité Office 365 dans son analyse et de génération de rapports, vous pouvez intégrer dans votre système SIEM :
  
- Azure AD
    
    Pour plus d’informations, voir les [journaux d’intégrer des ressources Azure dans vos systèmes SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Sécurité de l’application cloud Office 365
    
    Pour plus d’informations, voir [intégrer votre serveur SIEM avec Office 365 Cloud Application Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Étape suivante

Voir [meilleures pratiques de sécurité pour Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

