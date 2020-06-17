---
title: Protéger vos comptes d’administrateur général Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/15/2020
audience: Admin
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
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Protégez l’accès administrateur général à votre abonnement Microsoft 365.
ms.openlocfilehash: 6378a7c7b6e8479e25cf6465006f422cdc2137b0
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735722"
---
# <a name="protect-your-microsoft-365-global-administrator-accounts"></a>Protéger vos comptes d’administrateur général Microsoft 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Les violations de sécurité d’un abonnement Microsoft 365, y compris la collecte d’informations et les attaques par hameçonnage, sont généralement réalisées en compromettant les informations d’identification d’un compte d’administrateur général Microsoft 365. La sécurité dans le Cloud est un partenariat entre vous et Microsoft :
  
- Les services de Cloud Computing Microsoft sont basés sur une base de confiance et de sécurité. Microsoft fournit des contrôles et des fonctionnalités de sécurité pour vous aider à protéger vos données et applications.
    
- Vous êtes propriétaire de vos données et des identités et de la responsabilité de leur protection, de la sécurité de vos ressources locales et de la sécurité des composants Cloud que vous contrôlez.
    
Microsoft offre des fonctionnalités pour vous aider à protéger votre organisation, mais elles ne sont efficaces que si vous les utilisez. Si vous ne les utilisez pas, vous pouvez être vulnérable aux attaques. Pour protéger vos comptes d’administrateur général, Microsoft vous aide à obtenir des instructions détaillées pour :
  
1. Créez des comptes d’administrateur général Microsoft 365 dédiés et utilisez-les uniquement lorsque cela est nécessaire.
    
2. Configurez l’authentification multifacteur pour vos comptes d’administrateur général Microsoft 365 dédiés et utilisez la forme d’authentification secondaire la plus puissante.
    
> [! Remarques] bien que cet article soit axé sur les comptes d’administrateur général, vous devez déterminer si des comptes supplémentaires avec des autorisations étendues pour accéder aux données de votre abonnement, tels que les comptes d’administrateur eDiscovery ou d’administrateur de sécurité ou de conformité, doivent être protégés de la même manière. <br > Il est possible de créer un compte d’administrateur général sans ajouter de licences.
  
## <a name="step-1-create-dedicated-microsoft-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Étape 1. Créez des comptes d’administrateur général Microsoft 365 dédiés et utilisez-les uniquement lorsque cela est nécessaire.

Il existe relativement peu de tâches administratives, telles que l’affectation de rôles à des comptes d’utilisateur, qui nécessitent des privilèges d’administrateur général. Par conséquent, au lieu d’utiliser tous les comptes d’utilisateur qui ont été affectés au rôle d’administrateur global, procédez comme suit :
  
1. Déterminez l’ensemble des comptes d’utilisateur auxquels a été attribué le rôle d’administrateur général. Vous pouvez effectuer cette opération avec Azure active (Azure AD) Directory PowerShell for Graph :
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. Connectez-vous à votre abonnement Microsoft 365 avec un compte d’utilisateur auquel le rôle d’administrateur global a été attribué.
    
3. Créez jusqu’à un maximum de quatre comptes d’utilisateur d’administrateur général dédiés. **Utilisez des mots de passe forts d’au moins 12 caractères.** Pour plus d’informations, reportez-vous à [créer un mot de passe fort](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Stockez les mots de passe des nouveaux comptes dans un emplacement sécurisé. 
    
4. Attribuez le rôle d’administrateur global à chacun des nouveaux comptes d’utilisateur d’administrateur général dédié.
    
5. Déconnectez-vous de Microsoft 365.
    
6. Connectez-vous à l’aide de l’un des nouveaux comptes d’utilisateur d’administrateur général dédiés.
    
7. Pour chaque compte d’utilisateur auquel a été attribué le rôle d’administrateur global à partir de l’étape 1 :
    
  - Supprimez le rôle d’administrateur global.
    
  - Attribuer des rôles d’administrateur au compte qui sont appropriés à la fonction et à la responsabilité de ce dernier. Pour plus d’informations sur les différents rôles d’administrateur dans Microsoft 365, voir [à propos des rôles d’administrateur](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).
    
8. Déconnectez-vous de Microsoft 365.
    
Le résultat doit être :
  
- Les seuls comptes d’utilisateurs de votre abonnement dotés du rôle Administrateur général sont les comptes du nouvel ensemble de comptes Administrateur général dédiés. Vérifiez cela à l’aide de la commande PowerShell suivante :
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- Tous les autres comptes d’utilisateurs qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur associés à leurs responsabilités.
    
À partir de ce moment-là, vous vous connectez avec les comptes d’administrateur général dédiés uniquement pour les tâches qui nécessitent des privilèges d’administrateur général. Toutes les autres opérations d’administration de Microsoft 365 doivent être réalisées en affectant d’autres rôles d’administration aux comptes d’utilisateur.
  
> [!NOTE]
> Cette opération nécessite des étapes supplémentaires pour se déconnecter de votre compte d’utilisateur quotidien et se connecter avec un compte d’administrateur général dédié. Toutefois, cela ne doit être réalisé qu’occasionnellement pour les opérations de l’administrateur général. Considérez que la récupérant votre abonnement Microsoft 365 après une violation de compte d’administrateur général nécessite beaucoup plus d’étapes.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-global-administrator-accounts-and-use-the-strongest-form-of-additional-verification"></a>Étape 2. Configurez l’authentification multifacteur pour vos comptes d’administrateur général Microsoft 365 dédiés et utilisez la forme de vérification supplémentaire la plus puissante.

L’authentification multifacteur (MFA) nécessite des informations supplémentaires au-delà du nom de compte et du mot de passe. Microsoft 365 prend en charge ces méthodes de vérification supplémentaires :
  
- L’application Microsoft Authenticator

- appel téléphonique ;
    
- Code de vérification généré de manière aléatoire envoyé par le biais d’un message texte
    
- carte à puce (virtuelle ou physique) ;
    
- appareil biométrique.
    
>[!Note]
>Pour les organisations qui doivent adhérer aux normes de l’Institut NIST (National Institute of Standards and Technology), l’utilisation d’un appel téléphonique ou de méthodes de vérification supplémentaires basées sur des messages de texte est restreinte. Pour plus d’informations, cliquez [ici](https://pages.nist.gov/800-63-FAQ/#q-b01) .
>

Si vous êtes une petite entreprise qui utilise des comptes d’utilisateur stockés uniquement dans le Cloud (le modèle d’identité en nuage uniquement), suivez ces étapes pour configurer l’authentification multifacteur à l’aide d’un appel téléphonique ou d’un code de vérification de message texte envoyé à un téléphone intelligent :
  
1. [Configurez MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. Configurez l' [authentification multifacteur pour Microsoft 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) pour configurer chaque compte d’administrateur général dédié pour les appels téléphoniques ou les messages texte comme méthode de vérification. 
    
Si vous êtes une organisation plus importante qui utilise un modèle d’identité hybride Microsoft 365, vous disposez de davantage d’options de vérification. Si l’infrastructure de sécurité est déjà en place pour une méthode d’authentification secondaire plus puissante, procédez comme suit :
  
1. [Configurez MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).
    
2. Configurez l' [authentification multifacteur pour vos nouveaux comptes administrateur général](https://support.office.com/article/set-up-your-microsoft-365-sign-in-for-multi-factor-authentication-ace1d096-61e5-449b-a875-58eb3d74de14) afin de configurer chaque compte d’administrateur général dédié pour la méthode de vérification appropriée. 
    
Si l’infrastructure de sécurité pour la méthode de vérification renforcée souhaitée n’est pas en place et ne fonctionne pas pour Microsoft 365 MFA, nous vous recommandons vivement de configurer des comptes d’administrateur global dédiés avec MFA à l’aide de l’application Microsoft Authenticator, un appel téléphonique ou un code de vérification de message texte envoyé à un téléphone intelligent pour vos comptes d’administrateur général comme mesure de sécurité provisoire. Ne laissez pas vos comptes d’administrateur général dédiés sans la protection supplémentaire fournie par MFA.
  
Pour plus d’informations, reportez-vous à la rubrique [plan for Multi-Factor Authentication for Microsoft 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).
  
Pour vous connecter aux services Microsoft 365 avec MFA et PowerShell, consultez les articles suivants :

- [Office 365 PowerShell pour les comptes d’utilisateur, les groupes et les licences](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Microsoft Teams](https://docs.microsoft.com/office365/enterprise/powershell/manage-microsoft-teams-with-office-365-powershell#sign-in-with-multi-factor-authentication-mfa)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/mfa-connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [Skype Entreprise Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>Protections supplémentaires pour les organisations d’entreprise

Après les étapes 1 et 2, utilisez ces méthodes supplémentaires pour vous assurer que votre compte d’administrateur général, ainsi que la configuration que vous exécutez en l’utilisant, sont aussi sécurisés que possible.
  
### <a name="privileged-access-workstation"></a>Station de travail accès privilégié

Pour vous assurer que l’exécution des tâches à privilèges élevés est aussi sécurisée que possible, utilisez une station de travail accès privilégié (patte). Une patte est un ordinateur dédié qui est utilisé uniquement pour les tâches de configuration sensibles, telles que la configuration de Microsoft 365 qui nécessite un compte d’administrateur général. Étant donné que cet ordinateur n’est pas utilisé quotidiennement pour la navigation Internet ou le courrier électronique, il est mieux protégé contre les attaques et les menaces Internet.
  
Pour obtenir des instructions sur la configuration d’une patte, voir [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw) .
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Au lieu que le rôle administrateur général soit attribué de façon permanente à vos comptes d’administrateur général, vous pouvez utiliser Azure AD Privileged Identity Management (PIM) pour activer l’attribution à la demande, juste-à-temps, du rôle d’administrateur général lorsque cela est nécessaire.
  
Au lieu que vos comptes d’administrateur général sont un administrateur permanent, ils deviennent administrateurs éligibles. Le rôle administrateur général est inactif jusqu’à ce qu’un utilisateur en ait besoin. Vous devez ensuite effectuer un processus d’activation pour ajouter le rôle administrateur général au compte d’administrateur général pour une durée déterminée. Lorsque le temps arrive à expiration, PIM supprime le rôle administrateur général du compte d’administrateur général.
  
L’utilisation de PIM et de ce processus réduit considérablement le temps que vos comptes d’administrateur général sont vulnérables aux attaques et à l’utilisation par des utilisateurs malveillants.

Le GIP est disponible avec Azure AD Premium P2, inclus dans Microsoft 365 entreprise E5 ou Enterprise Mobility + Security (EMS) E5, ou vous pouvez acheter des licences individuelles pour vos comptes d’administrateur général.
  
Pour plus d’informations, consultez la rubrique [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Logiciel de gestion des informations et des événements de sécurité (SIEM) pour la journalisation Microsoft 365

Les logiciels SIEM exécutés sur un serveur effectuent une analyse en temps réel des alertes de sécurité et des événements créés par les applications et le matériel réseau. Pour permettre à votre serveur SIEM d’inclure des alertes et des événements de sécurité Microsoft 365 dans ses fonctions d’analyse et de création de rapports, intégrez Azure AD dans votre SEIM. Voir [Introduction to Azure log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Étape suivante

Si vous configurez l’identité pour votre abonnement Microsoft 365, consultez les éléments suivants :

- [Identités de Cloud uniquement](cloud-only-identities.md) si vous utilisez l’identité en nuage uniquement
- [Préparer la synchronisation d’annuaires](prepare-for-directory-synchronization.md) si vous utilisez une identité hybride

  
## <a name="see-also"></a>Voir aussi

Feuille de [route Microsoft 365 Security](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).
