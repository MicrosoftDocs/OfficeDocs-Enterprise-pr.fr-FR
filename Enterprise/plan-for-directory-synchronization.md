---
title: Identité hybride et synchronisation d’annuaires pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
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
ms.openlocfilehash: 7dfb5a34e7a5a1bf1368a059859ef32049a15473
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072536"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Identité hybride et synchronisation d’annuaires pour Office 365

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

En fonction des besoins de l’entreprise et des exigences techniques, le modèle d’identité hybride et la synchronisation d’annuaires constituent le choix le plus courant pour les clients d’entreprise qui adoptent Office 365. La synchronisation d’annuaires vous permet de gérer les identités dans vos services de domaine Active Directory (AD DS) et toutes les mises à jour des comptes d’utilisateur, des groupes et des contacts sont synchronisées avec le client Azure Active Directory (Azure AD) de votre abonnement Office 365.

>[!Note]
>Lorsque les comptes d’utilisateur AD DS sont synchronisés pour la première fois, une licence Office 365 n’est pas automatiquement attribuée et ne peut pas accéder aux services 365 Office, tels que le courrier électronique. Vous devez attribuer une licence à ces comptes d’utilisateur, de manière individuelle ou dynamique via l’appartenance à un groupe.
>

## <a name="authentication-for-hybrid-identity"></a>Authentification pour l’identité hybride

Il existe deux types d’authentification lors de l’utilisation du modèle d’identité hybride :

- Authentification gérée

  Azure AD gère le processus d’authentification à l’aide d’une version hachée stockée localement du mot de passe ou envoie les informations d’identification à un agent logiciel local pour qu’il soit authentifié par le service AD DS local.

- Authentification fédérée

  Azure AD redirige l’ordinateur client demandant l’authentification pour contacter un autre fournisseur d’identité.

### <a name="managed-authentication"></a>Authentification gérée

Il existe deux types d’authentification gérée :

- Synchronisation de hachage de mot de passe (hachage)

  Azure AD effectue l’authentification proprement dite.

- Authentification directe (PTA)

  Les services AD DS d’Azure AD effectuent l’authentification.


#### <a name="password-hash-synchronization"></a>Synchronisation de hachage de mot de passe

Avec la synchronisation de hachage de mot de passe (hachage), vous synchronisez vos comptes d’utilisateur AD DS avec Office 365 et vous gérez vos utilisateurs en local. Les hachages des mots de passe des utilisateurs sont synchronisés entre votre AD DS et Azure AD afin que les utilisateurs aient le même mot de passe sur site et dans le Cloud. Il s’agit de la méthode la plus simple pour activer l’authentification pour les identités AD DS dans Azure AD. 

![Synchronisation de hachage de mot de passe (hachage)](./media/plan-for-directory-synchronization/phs-authentication.png)

Lorsque les mots de passe sont modifiés ou réinitialisés en local, les nouveaux hachages de mot de passe sont synchronisés avec Azure AD afin que les utilisateurs puissent toujours utiliser le même mot de passe pour les ressources en nuage et les ressources locales. Les mots de passe utilisateur ne sont jamais envoyés à Azure AD ou stockés dans Azure AD en texte clair. Certaines fonctionnalités avancées d’Azure AD, telles que la protection des identités, nécessitent hachage, quelle que soit la méthode d’authentification sélectionnée.
  
Pour plus d’informations, voir [Choosing hachage](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
#### <a name="pass-through-authentication"></a>Authentification directe

L’authentification directe (directe) fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel exécuté sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre service AD DS. Avec l’authentification directe (directe), vous synchronisez les comptes d’utilisateur AD DS avec Office 365 et vous gérez vos utilisateurs en local. 

![Authentification directe (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

DIRECTE permet à vos utilisateurs de se connecter à des ressources et des applications locales et Office 365 à l’aide de leur compte local et de leur mot de passe. Cette configuration valide les mots de passe des utilisateurs directement par rapport à votre service AD DS local sans stocker les hachages de mots de passe dans Azure AD. 

DIRECTE est également destiné aux organisations disposant d’un impératif de sécurité pour appliquer immédiatement les États de compte d’utilisateur, les stratégies de mot de passe et les heures d’ouverture de session locaux. 
  
Pour plus d’informations, voir [Choosing directe](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .
  
### <a name="federated-authentication"></a>Authentification fédérée

L’authentification fédérée est principalement destinée aux grandes entreprises ayant des exigences d’authentification plus complexes. Les identités AD DS sont synchronisées avec Office 365 et les comptes d’utilisateurs sont gérés en local. Avec l’authentification fédérée, les utilisateurs ont le même mot de passe sur site et dans le Cloud et ils n’ont pas besoin de se connecter à nouveau pour utiliser Office 365. 

L’authentification fédérée peut prendre en charge des exigences d’authentification supplémentaires, telles que l’authentification par carte à puce ou une authentification multifacteur tierce et est généralement requise lorsque les organisations ont une condition d’authentification non pris en charge en mode natif par Azure AD.
 
Voir [choix de l’authentification fédérée](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) pour en savoir plus.
  
#### <a name="third-party-authentication-and-identity-providers"></a>Fournisseurs d’identité et d’authentification tiers

Les objets d’annuaire locaux peuvent être synchronisés avec Office 365 et l’accès aux ressources de Cloud est principalement géré par un fournisseur d’identité tiers (IdP). Si votre organisation utilise une solution de Fédération tierce, vous pouvez configurer l’authentification avec cette solution pour Office 365 à condition que la solution de Fédération tierce soit compatible avec Azure AD.
  
Pour en savoir plus, voir [compatibilité de Fédération Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .
  
## <a name="ad-ds-cleanup"></a>Nettoyage des services de domaine Active Directory

Pour garantir une transition transparente vers Office 365 à l’aide de la synchronisation, vous devez préparer votre forêt AD DS avant de commencer le déploiement de la synchronisation d’annuaires d’Office 365.
  
Lorsque vous [configurez la synchronisation d’annuaires dans Office 365](set-up-directory-synchronization.md), l’une des étapes consiste à [Télécharger et à exécuter l’outil IdFix](install-and-run-idfix.md). Vous pouvez utiliser l’outil IdFix pour faciliter le [nettoyage d’annuaire](prepare-directory-attributes-for-synch-with-idfix.md).
  
Le nettoyage de votre annuaire doit se concentrer sur les tâches suivantes :

- Supprimez les attributs **ProxyAddress** et **userPrincipalName** en double.
- Mettre à jour les attributs **userPrincipalName** vides et non valides avec des attributs **userPrincipalName** valides.
- Supprimez les caractères non valides et douteables dans les attributs **GivenName**, Surname ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailnickname**et **userPrincipalName** . Pour plus d’informations sur la préparation des attributs, voir [liste des attributs synchronisés par l’outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Il s’agit des mêmes attributs que ceux qui sont synchronisés avec Azure AD Connect. 
  
## <a name="multi-forest-deployment-considerations"></a>Considérations relatives au déploiement dans plusieurs forêts

Pour plusieurs forêts et options d’authentification unique, utilisez [l’installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si votre organisation dispose de plusieurs forêts pour l’authentification (forêts d’ouverture de session), nous vous recommandons vivement les suivants :
  
- **Envisagez de consolider vos forêts.** En règle générale, il y a plus de charge nécessaire pour gérer plusieurs forêts. À moins que votre organisation n’ait des contraintes de sécurité qui dictent le besoin de forêts distinctes, envisagez de simplifier votre environnement local.
- **Utilisez uniquement dans votre forêt d’ouverture de session principale.** Envisagez de déployer Office 365 uniquement dans votre forêt d’ouverture de session principale pour le déploiement initial d’Office 365. 

Si vous ne pouvez pas consolider votre déploiement AD DS à forêts multiples ou si vous utilisez d’autres services d’annuaire pour gérer les identités, vous pourrez peut-être les synchroniser avec l’aide de Microsoft ou d’un partenaire.
  
Pour plus d’informations, consultez la rubrique [synchronisation d’annuaires de forêts multiples avec un scénario d’authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=525321) .
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Fonctionnalités dépendant de la synchronisation d’annuaires
  
La synchronisation d’annuaires est requise pour les fonctionnalités et fonctionnalités suivantes :
  
- Authentification unique transparente Azure AD (SSO)
- Coexistence Skype
- Déploiement Exchange hybride, notamment :
  - Liste d’adresses globale (GAL) entièrement partagée entre votre environnement Exchange local et Office 365.
  - Synchronisation des informations GAL provenant de différents systèmes de messagerie.
  - Possibilité d’ajouter et de supprimer des utilisateurs des offres de services Office 365. Cette possibilité nécessite ce qui suit :
  - La synchronisation bidirectionnelle doit être configurée lors de la configuration de la synchronisation d’annuaires. Par défaut, les outils de synchronisation d’annuaires écrivent des informations d’annuaire uniquement dans le Cloud. Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d’écriture différée de sorte qu’un nombre limité d’attributs d’objets sont copiés à partir du Cloud, puis réécrits dans vos services AD DS locaux. L’écriture différée est également appelée mode hybride Exchange. 
  - Un déploiement Exchange hybride local
  - Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Office 365 tout en conservant les autres boîtes aux lettres utilisateur en local.
  - Les expéditeurs approuvés et les expéditeurs bloqués en local sont répliqués vers Office 365.
  - Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».
  - Vous disposez d’une solution d’authentification multifacteur ou de carte à puce sur site intégrée.
- Synchronisation de photos, de miniatures, de salles de conférence et de groupes de sécurité

## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à déployer l’identité hybride, consultez la rubrique préparer la mise [en service des utilisateurs](prepare-for-directory-synchronization.md).
  
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

