---
title: Détecter et résoudre les accorde consentement illicite dans Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Découvrez comment identifier et corriger l’attaque accorde consentement illicite dans Office 365.
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>Détecter et résoudre les accorde consentement illicite dans Office 365

**Résumé**  Découvrez comment identifier et corriger l’attaque accorde consentement illicite dans Office 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Quel est l’attaque de grant consentement illicite dans Office 365 ?
Dans une autorisation illicite accorder l’attaque, que l’intrus crée une application Azure inscrits qui demande l’accès aux données telles que les informations de contact, courrier électronique, ou des documents. L’intrus astuces puis un utilisateur final en accorder cette autorisation d’application pour accéder à leurs données via une attaque par hameçonnage, soit par injection de code illicite dans un site de confiance. Une fois le consentement de l’utilisateur a été octroyée à l’application illicite, il dispose d’un accès au niveau des comptes à des données sans avoir besoin d’un compte d’organisation. Étapes de correction normale, comme la réinitialisation des mots de passe des comptes touchées ou nécessitant l’authentification multifacteur (MFA) sur les comptes, ne sont pas efficaces contre ce type d’attaque, car ils sont des applications tierces et qui sont externes à l’organisation. Un modèle d’interaction qui suppose que l’entité qui appelle les informations est automation et non par un humain tirer parti de ces attaques.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>À quoi une autorisation illicite grant attaque ressemble dans Office 365 ?
Vous devez rechercher le Office 365 **journal d’audit** pour rechercher des signes, également appelées indicateurs de compromis (IOC) de l’attaque. Pour les organisations avec de nombreuses applications inscrites Azure et une base d’utilisateurs de grande taille, la meilleure pratique consiste pour passer en revue les attributions organisations consentement de l’utilisateur une fois par semaine.
### <a name="steps-for-finding-signs-of-this-attack"></a>Pour rechercher des signes d’attaque
1. Ouvrez **Centre de conformité et de sécurité** dans votre organisation cliente Office 365.
2. Naviguez jusqu’au nœud de **recherche et enquête** et sélectionnez le **journal d’audit de** la recherche.
3. Créer une recherche (toutes les activités et tous les utilisateurs) et filtrer les résultats de consentement à l’application et ajouter OAuth2PermissionGrant.
4. Examinez les propriétés étendues et vérifier si IsAdminContent est défini sur True.


Si cette valeur est true, cela indique que personne ayant accès administrateur Global peut disposer d’un accès étendu aux données. Si cette erreur est inattendue, procédez comme pour [Confirmer une attaque](detect-and-remediate-illicit-consent-grants.md#confirmattack).

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>Comment vérifier une attaque
Si vous disposez d’une ou plusieurs instances de l’IOCs répertoriés ci-dessus, vous devez faire des investigations positive confirmer que l’attaque s’est produite. Vous pouvez utiliser une de ces trois méthodes pour confirmer l’attaque.
- Inventaire des applications et leurs autorisations à l’aide du portail d’Azure Active Directory. Cette méthode est complète, mais vous ne pouvez vérifier qu’un utilisateur à un moment qui peut être beaucoup de temps si vous disposez de plusieurs utilisateurs à vérifier.
- Inventaire des applications et leurs autorisations à l’aide de PowerShell. Il s’agit de la méthode plus rapide et plus complète, avec le moins de surcharge.
- Demander à vos utilisateurs individuellement vérifier leurs applications et les autorisations et retourne les résultats aux administrateurs de correction.

## <a name="inventory-apps-with-access-in-your-organization"></a>Inventaire applications Access dans votre organisation
Vous pouvez effectuer cette action pour vos utilisateurs avec le Azure Active Directory portail ou de PowerShell ou demander à vos utilisateurs individuellement énumérer leur accès aux applications.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Étapes de l’utilisation du portail d’annuaire Azure Active
Vous pouvez rechercher les applications à laquelle un utilisateur donné dispose des autorisations à l’aide d' [Azure Active Directory portail](https://portal.azure.com/). 
1. Connectez-vous au portail Azure avec des droits d’administration.
2. Sélectionnez le serveur lame Azure Active Directory.
3. Sélectionnez **les utilisateurs**.
4. Sélectionnez l’utilisateur que vous souhaitez consulter.
5. Sélectionnez **Applications**.

Vous verrez les applications qui sont affectées à l’utilisateur et que les applications ont des autorisations.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Énumérer les étapes pour vos utilisateurs leur accès aux applications
Demander à vos utilisateurs d’accéder à https://myapps.microsoft.com et consulter leur propre accès application il. Ils doivent être en mesure de voir toutes les applications Access, afficher les informations (y compris dans l’étendue d’accès) et être en mesure de révoquer les privilèges d’applications suspectes ou illicites.

### <a name="steps-for-doing-this-with-powershell"></a>Étapes de cette procédure avec PowerShell
Pour vérifier l’attaque illicite Grant consentement, le plus simple consiste à exécuter [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), ce qui provoque le vidage de toutes les OAuth consentement accorde les autorisations d’application pour tous les utilisateurs dans votre location dans un fichier .csv. 

#### <a name="pre-requisites"></a>Conditions préalables
- La bibliothèque Windows Azure AD PowerShell est installée.
- Droits d’administrateur global sur le client que le script s’exécutera.
- Administrateur local sur l’ordinateur à partir de laquelle sera exécuté les scripts.

> [!IMPORTANT]
> Il est vivement recommandé que vous avez besoin de l’authentification multifacteur sur votre compte d’administration.  Ce script prend en charge l’authentification MFA.

1. Connectez-vous à l’ordinateur que vous allez exécuter le script avec des droits d’administrateur local.
2. Téléchargez ou copiez le script [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) à partir de référentiels dans un dossier à partir duquel vous allez exécuter la scruipt.  Ce sera le même dossier dans lequel le fichier « permissions.csv » de sortie est écrits.
3. Ouvrez une instance PowerShell en tant qu’administrateur et ouvrez le dossier que vous avez enregistré le script pour.
4. Se connecter à votre annuaire à l’aide de l’applet de commande [Connect-AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0) .
5. Exécutez la ligne de commande PowerShell comme suit :`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

Le script génère un fichier nommé Permissions.csv. Suivez ces étapes pour rechercher les attributions d’autorisations illicite d’application : 
1. Recherchez la valeur « AllPrinciples » dans la colonne ConsentType (colonne G). L’autorisation AllPrincipals permet à l’application cliente accéder au contenu de tout le monde dans la location. Les applications Office 365 natives doivent cette autorisation afin de fonctionner correctement. Toutes les applications non Microsoft avec cette autorisation doivent être examinées avec soin.
2.  Dans la révision de colonne (F) autorisation les autorisations que chaque délégué application a pour le contenu. Recherchez les autorisations « Lecture » et « Écriture » ou « *. Tous les » autorisation et passer en revue les que ces avec soin car ils ne peuvent pas être appropriées.
3.  Passez en revue les utilisateurs ayant des autorisations accordées. Si le profil haute ou haute affecte les utilisateurs ont inapproprié autorisations accordées, vous devez approfondir.
4.  Dans la colonne ClientDisplayName (colonne C) Rechercher pour les applications qui semblent suspectes. Applications avec des noms mal orthographiés, des noms super terne ou noms pirate sonne doivent être examinées avec soin.

## <a name="determine-the-scope-of-the-attack"></a>Déterminer l’étendue de l’attaque
Une fois que vous avez terminé l’inventaire des accès de l’application, passez en revue le Office 365 **journal d’audit** pour déterminer l’étendue de l’infraction.  Recherche sur les utilisateurs, les délais qui avait l’application illicite d’accéder à votre organisation et les autorisations de l’application a rencontré. Vous pouvez rechercher **journal d’audit** dans [Centre de conformité et de sécurité pour Microsoft Office 365](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c). 

> [!IMPORTANT]
> [Audit de boîte aux lettres](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918) et [l’activité de l’audit pour les utilisateurs et les administrateurs](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014) doivent avoir été activé avant l’attaque, vous pouvez obtenir ces informations.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>Comment arrêter et corriger une attaque de grant illicite consentement de l’utilisateur
Après avoir identifié une application avec des autorisations illicites, vous devez supprimer ce access de différentes manières.
- Vous pouvez révoquer l’autorisation de l’application dans Azure Active Directory Portal par :
    - Accédez à l’utilisateur affecté dans le serveur lame **Utilisateur Azure Active Directory** .
    - Sélectionnez **Applications**.
    - Sélectionnez l’application illicite.
    - Cliquez sur **Supprimer** dans l’exploration vers le bas.
- Vous pouvez annuler l’octroi d’autorisation OAuth avec PowerShell en suivant les étapes de [Remove-AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0).
- Vous pouvez annuler l’attribution de rôle d’application de Service avec PowerShell en suivant les étapes de [Remove-AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0).
- Vous pouvez également désactiver connexion dans complètement le compte affecté, qui à son tour désactive l’accès aux données de ce compte application. Ce n’est pas idéal pour la productivité de l’utilisateur final, bien sûr, mais si vous utilisez pour limiter l’impact rapidement, il peut être une correction à court terme viable.
- Vous pouvez désactiver applications intégrées pour votre location. Il s’agit d’une étape importante qui désactive la possibilité pour les utilisateurs finaux accorder l’autorisation sur un client à l’échelle. Cela empêche les utilisateurs de par inadvertance accorder l’accès à une application malveillante. Cela n’est pas recommandé comme il nuit gravement aux de vos utilisateurs être productifs avec les applications tierces.  Vous pouvez procéder en suivant les étapes dans les [Applications intégrée activer ou désactiver](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Sécuriser Office 365 comme une sécurité pro
Votre abonnement Office 365 est fourni avec un ensemble de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs puissantes.  Utiliser le [Guide de sécurité Office 365 : principaux des priorités pour les 30 premiers jours, 90 jours et au-delà](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) à mettre en œuvre les meilleures pratiques pour la sécurisation de votre client Office 365 de Microsoft.
- Tâches à accomplir dans les 30 jours.  Ces ont une incidence immédiate et sont faible impact à vos utilisateurs.
- Tâches à accomplir dans 90 jours. Ces prennent un peu plus de temps pour planifier et implémenter mais sensiblement améliorer votre sécurité.
- Au-delà de 90 jours. Ces améliorations créer votre premier travail 90 jours.

## <a name="see-also"></a>Voir aussi :
- [Application inattendue dans ma liste des applications](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application) guide les administrateurs par le biais de différentes actions que à effectuer après la réalisation des applications inattendues avec un accès aux données qu’ils souhaitent.
- [Intégrer des applications Azure Active Directory]  (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent) est une vue d’ensemble de consentement de l’utilisateur et des autorisations.  Une attention particulière à la section [vue d’ensemble de l’infrastructure de consentement de l’utilisateur](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework) .
- [Problèmes de développement de mon application](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map) fournit des liens vers différentes consentement articles connexes.
- [Objets application et service principal dans Azure Active Directory (AD Azure)](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects) fournit une vue d’ensemble de l’Application et le Service principales objets principaux pour le modèle d’application.
- [Gérer l’accès aux applications](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps) est une vue d’ensemble des fonctionnalités que les administrateurs doivent gérer l’accès utilisateur aux applications.