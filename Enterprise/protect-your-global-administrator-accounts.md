---
title: Protéger vos comptes d'administrateur général Office 365
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
description: Protégez l'accès administrateur général à votre abonnement Office 365 en procédant comme suit.
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573918"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Protéger vos comptes d'administrateur général Office 365

 **Résumé:** Protégez votre abonnement Office 365 des attaques en fonction de la compromission d'un compte d'administrateur général. 
  
Les violations de sécurité d'un abonnement Office 365, y compris la collecte d'informations et les attaques par hameçonnage, sont généralement réalisées en compromettant les informations d'identification d'un compte d'administrateur général Office 365. La sécurité dans le Cloud est un partenariat entre vous et Microsoft:
  
- Les services de Cloud Computing Microsoft sont basés sur une base de confiance et de sécurité. Microsoft fournit des contrôles et des fonctionnalités de sécurité pour vous aider à protéger vos données et applications.
    
- Vous êtes propriétaire de vos données et des identités et de la responsabilité de leur protection, de la sécurité de vos ressources locales et de la sécurité des composants Cloud que vous contrôlez.
    
Microsoft offre des fonctionnalités pour vous aider à protéger votre organisation, mais elles ne sont efficaces que si vous les utilisez. Si vous ne les utilisez pas, vous pouvez être vulnérable aux attaques. Pour protéger vos comptes d'administrateur général, Microsoft vous aide à obtenir des instructions détaillées pour:
  
1. Créez des comptes d'administrateur général Office 365 dédiés et utilisez-les uniquement lorsque cela est nécessaire.
    
2. ConFigurez l'authentification multifacteur pour vos comptes d'administrateur général Office 365 dédiés et utilisez la forme d'authentification secondaire la plus puissante.
    
3. Activez et configurez la sécurité des applications Cloud d'Office 365 pour surveiller l'activité de compte d'administrateur général suspect.
    
> [!NOTE]
> Bien que cet article soit axé sur les comptes d'administrateur général, vous devez également déterminer si des comptes supplémentaires disposant d'autorisations étendues pour accéder aux données de votre abonnement, telles que l'administrateur eDiscovery ou la sécurité ou la conformité. les comptes d'administrateur doivent être protégés de la même façon. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Étape 1. Créer des comptes d'administrateur général Office 365 dédiés et les utiliser uniquement lorsque cela est nécessaire

Il existe relativement peu de tâches administratives, telles que l'affectation de rôles à des comptes d'utilisateur, qui nécessitent des privilèges d'administrateur général. Par conséquent, au lieu d'utiliser tous les comptes d'utilisateur qui ont été affectés au rôle d'administrateur global, procédez comme suit:
  
1. Déterminez l'ensemble des comptes d'utilisateur auxquels a été attribué le rôle d'administrateur général. Pour ce faire, utilisez cette commande à l'invite de commandes module Microsoft Azure Active Directory pour Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Connectez-vous à votre abonnement Office 365 avec un compte d'utilisateur auquel le rôle d'administrateur global a été attribué.
    
3. Créez au moins un et jusqu'à cinq comptes d'utilisateur d'administrateur général dédiés. **Utilisez des mots de passe forts d'au moins 12 caractères.** Pour plus d'informations, rePortez-vous à [créer un mot de passe fort](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Stockez les mots de passe des nouveaux comptes dans un emplacement sécurisé. 
    
4. Attribuez le rôle d'administrateur global à chacun des nouveaux comptes d'utilisateur d'administrateur général dédié.
    
5. DéConnectez-vous d'Office 365.
    
6. Connectez-vous à l'aide de l'un des nouveaux comptes d'utilisateur d'administrateur général dédiés.
    
7. Pour chaque compte d'utilisateur auquel a été attribué le rôle d'administrateur global à partir de l'étape 1:
    
  - Supprimez le rôle d'administrateur global.
    
  - Attribuer des rôles d'administrateur au compte qui sont appropriés à la fonction et à la responsabilité de ce dernier. Pour plus d'informations sur les différents rôles d'administrateur dans Office 365, reportez-vous à la rubrique [à propos des rôles d'administrateur office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. DéConnectez-vous d'Office 365.
    
Le résultat doit être:
  
- Les seuls comptes d'utilisateur de votre abonnement qui ont le rôle d'administrateur global sont les nouveaux comptes d'administrateur général dédiés. Vérifiez cela à l'aide de la commande PowerShell suivante:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Tous les autres comptes d’utilisateur qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur qui sont associés à leurs responsabilités.
    
À partir de ce moment-là, vous vous connectez avec les comptes d'administrateur général dédiés uniquement pour les tâches qui nécessitent des privilèges d'administrateur général. Toutes les autres opérations d'administration d'Office 365 doivent être réalisées en affectant d'autres rôles d'administration aux comptes d'utilisateur.
  
> [!NOTE]
> Oui, cela nécessite des étapes supplémentaires pour se déconnecter de votre compte d'utilisateur quotidien et se connecter avec un compte d'administrateur général dédié. Toutefois, cela ne doit être réalisé qu'occasionnellement pour les opérations de l'administrateur général. Considérez que la récupérant votre abonnement Office 365 après une violation de compte d'administrateur général nécessite beaucoup plus d'étapes. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Étape 2. ConFigurez l'authentification multifacteur pour vos comptes d'administrateur général Office 365 dédiés et utilisez la forme d'authentification secondaire la plus puissante.

L'authentification multifacteur (MFA) pour vos comptes d'administrateur général nécessite des informations supplémentaires au-delà du nom de compte et du mot de passe. Office 365 prend en charge ces méthodes de vérification:
  
- appel téléphonique ;
    
- code d'accès généré de façon aléatoire ;
    
- carte à puce (virtuelle ou physique) ;
    
- appareil biométrique.
    
Si vous êtes une petite entreprise qui utilise des comptes d'utilisateur stockés uniquement dans le Cloud (le modèle d'identité Cloud), procédez comme suit pour configurer l'authentification multiFACTEUR à l'aide d'un appel téléphonique ou d'un code de vérification de message texte envoyé à un téléphone intelligent:
  
1. [Activer l'authentification multifacteur](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. Configurez la [vérification en deux étapes pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) afin de configurer chaque compte d'administrateur général dédié pour les appels téléphoniques ou les messages texte comme méthode de vérification. 
    
Si vous êtes une organisation plus importante qui utilise un modèle d'identité hybride Office 365, vous disposez de davantage d'options de vérification. Si l'infrastructure de sécurité est déjà en place pour une méthode d'authentification secondaire plus puissante, procédez comme suit:
  
1. [Activer l'authentification multifacteur](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. Configurez la [vérification en deux étapes pour Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) afin de configurer chaque compte d'administrateur général dédié pour la méthode de vérification appropriée. 
    
Si l'infrastructure de sécurité pour la méthode de vérification renforcée souhaitée n'est pas en place et ne fonctionne pas pour Office 365 MFA, nous vous recommandons vivement de configurer des comptes d'administrateur global dédiés avec MFA à l'aide d'un appel téléphonique ou d'un message texte. Code de vérification envoyé à un téléphone intelligent pour vos comptes d'administrateur général comme mesure de sécurité provisoire. Ne laissez pas vos comptes d'administrateur général dédiés sans la protection supplémentaire fournie par MFA.
  
Pour plus d’informations, reportez-vous à [Planifier l’authentification multifacteur pour les déploiements Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Pour vous connecter aux services Office 365 avec MFA et PowerShell, consultez [cet article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Étape 3. Surveiller l'activité du compte d'administrateur général suspect

Office 365 Cloud App Security vous permet de créer des stratégies pour vous informer d'un comportement suspect dans votre abonnement. La sécurité des applications Cloud est intégrée à Office 365 E5, mais elle est également disponible en tant que service distinct. Par exemple, si vous n'avez pas Office 365 E5, vous pouvez acheter des licences de sécurité d'application Cloud individuelles pour les comptes d'utilisateur auxquels sont attribués les rôles administrateur général, administrateur de sécurité et administrateur de conformité.
  
Si vous disposez de la sécurité de l'application Cloud dans votre abonnement Office 365, procédez comme suit:
  
1. Connectez-vous au centre d'administration Microsoft 365 avec un compte auquel le rôle administrateur de sécurité ou administrateur de conformité est attribué.
    
2. [Activez la sécurité des applications Cloud Office 365](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Examinez vos [stratégies de détection des anomalies dans Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) pour vous informer par courrier électronique des modèles anormaux d'activité administrative privilégiée. 
    
Pour ajouter un compte d'utilisateur au rôle administrateur de sécurité, [Connectez-vous à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) avec un compte d'administrateur général dédié et MFA, indiquez le nom d'utilisateur principal du compte d'utilisateur, puis exécutez les commandes suivantes: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Pour ajouter un compte d'utilisateur au rôle administrateur de conformité, indiquez le nom d'utilisateur principal du compte d'utilisateur, puis exécutez les commandes suivantes:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Protections supplémentaires pour les organisations d'entreprise

Après les étapes 1-3, utilisez ces méthodes supplémentaires pour vous assurer que votre compte d'administrateur général, ainsi que la configuration que vous exécutez en l'utilisant, sont aussi sécurisés que possible.
  
### <a name="privileged-access-workstation-paw"></a>Station de travail accès privilégié (patte)

Pour vous assurer que l'exécution des tâches à privilèges élevés est aussi sécurisée que possible, utilisez une patte. Une patte est un ordinateur dédié qui est utilisé uniquement pour les tâches de configuration sensibles, telles que la configuration d'Office 365 qui nécessite un compte d'administrateur général. Étant donné que cet ordinateur n'est pas utilisé quotidiennement pour la navigation Internet ou le courrier électronique, il est mieux protégé contre les attaques et les menaces Internet.
  
Pour obtenir des instructions sur la configuration d'une patte, [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)voir.
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gestion des identités par privilège pour Azure AD

Au lieu que le rôle administrateur général soit attribué de façon permanente aux comptes d'administrateur général, vous pouvez utiliser Azure AD PIM pour activer l'attribution à la demande, juste-à-temps, du rôle d'administrateur général lorsque cela est nécessaire.
  
Au lieu que vos comptes d'administrateur général sont un administrateur permanent, ils deviennent administrateurs éligibles. Le rôle administrateur général est inactif jusqu'à ce qu'un utilisateur en ait besoin. Vous devez ensuite effectuer un processus d'activation pour ajouter le rôle administrateur général au compte d'administrateur général pour une durée déterminée. Lorsque le temps arrive à expiration, PIM supprime le rôle administrateur général du compte d'administrateur général.
  
L'utilisation de PIM et de ce processus réduit considérablement le temps que vos comptes d'administrateur général sont vulnérables aux attaques et à l'utilisation par des utilisateurs malveillants.
  
Pour plus d'informations, consultez la rubrique [configure Azure ad Privileged identIty Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> Le GIP est disponible avec Azure Active Directory Premium P2, inclus dans Enterprise Mobility + Security (EMS) E5, ou vous pouvez acheter des licences individuelles pour vos comptes d'administrateur général. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Logiciel de gestion des informations et des événements de sécurité (SIEM) pour la journalisation Office 365

Les logiciels SIEM exécutés sur un serveur effectuent une analyse en temps réel des alertes de sécurité et des événements créés par les applications et le matériel réseau. Pour permettre à votre serveur SIEM d'inclure les alertes de sécurité Office 365 et les événements dans ses fonctions d'analyse et de création de rapports, intégrez-les dans votre système SIEM:
  
- Azure AD
    
    Pour plus d'informations, reportez-vous à [la rubrique intégration des journaux Azure ressources dans vos systèmes Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Sécurité de l’application cloud Office 365
    
    Pour plus d'informations, consultez [la rubrique intégration de votre serveur Siem à la sécurité des applications Cloud Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Étape suivante

Consultez [les meilleures pratiques en matière de sécurité pour Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

