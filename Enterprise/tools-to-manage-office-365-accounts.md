---
title: Outils de gestion des comptes Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Découvrez quels sont les outils à utiliser pour gérer vos utilisateurs Office 365, et comment vous pouvez utiliser dépend de la gestion des identités d’utilisateur. '
ms.openlocfilehash: 62467fb031090a521d0b9e067582b56fabe9e5fd
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540392"
---
# <a name="tools-to-manage-office-365-accounts"></a>Outils de gestion des comptes Office 365

Vous pouvez gérer les utilisateurs d’Office 365 de différentes manières, selon votre configuration. Vous pouvez gérer les utilisateurs dans le centre d’administration Office 365, Windows PowerShell, votre annuaire local, ou dans le portail d’administration d’Azure Active Directory. 

Dès que vous avez acheté Office 365, le centre d’administration et Windows PowerShell peuvent servir à gérer les comptes. Lors de la gestion des identités de nuage chaque personne de votre organisation a un ID d’utilisateur et le mot de passe pour Office 365. Si vous souhaitez intégrer à votre infrastructure local et disposer de comptes utilisateur synchronisé avec Office 365, vous pouvez utiliser Azure Active Directory se connecter pour assurer la synchronisation des identités et assurer la synchronisation de mot de passe si vous le souhaitez ou complète fonctionnalité d’authentification unique.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planifier où et comment vous allez gérer vos comptes d’utilisateurs

Où et comment vous pouvez gérer vos comptes d’utilisateurs varie selon le modèle d’identité que vous souhaitez utiliser pour Office 365. Les deux modèles globales sont fédérés et l’authentification dans le nuage.
  
### <a name="cloud-authentication"></a>Authentification dans le nuage

<<<<<<< HEAD
- [Authentification dans le nuage](about-office-365-identity.md#cloud-authentication) - créer et gérer des utilisateurs dans le centre d’administration d’Office 365, vous pouvez également utiliser Windows PowerShell ou Azure Active Directory pour gérer vos utilisateurs. 
    
=======
- [Office 365 identité](about-office-365-identity.md) - créer et gérer des utilisateurs dans le centre d’administration d’Office 365, vous pouvez également utiliser Windows PowerShell ou Azure Active Directory pour gérer vos utilisateurs.
>>>>>>> conversion robmazz
- [Hachage de mot de passe de synchronisation avec transparente unique-](about-office-365-identity.md) - la façon la plus simple pour activer l’authentification pour les objets d’annuaire local dans Azure AD. Avec la synchronisation de hachage de mot de passe (pH), vous synchronisez vos objets compte d’utilisateur Active Directory local avec Office 365 et gérer vos utilisateurs locaux. 
- [L’authentification directe avec transparente unique-](about-office-365-identity.md) - fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel s’exécutant sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre Active Directory sur site. 
    
### <a name="federated-authentication"></a>Authentification fédérée

<<<<<<< HEAD
- [L’authentification directe avec transparente unique-](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on) - principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, objets d’annuaire sont synchronisés avec Office 365 et locaux les comptes d’utilisateurs sont gérés sur site. 
    
=======
- [Office 365 identité](about-office-365-identity.md) - principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, objets d’annuaire sont synchronisés avec Office 365 et locaux comptes d’utilisateurs sont gérés sur site. 
>>>>>>> conversion robmazz
- [Fournisseurs d’authentification et d’identité tiers](about-office-365-identity.md) - annuaire local objets peuvent être synchronisés avec Office 365 et l’accès aux ressources en nuage est principalement géré par un fournisseur d’identité de tiers (IdP). 
    
## <a name="managing-accounts"></a>La gestion des comptes

Lors de la détermination de la manière dont votre organisation créer et gérer les comptes, considérez les points suivants :
  
- Le logiciel de synchronisation d’annuaire doit être installé sur des serveurs dans votre environnement local pour connecter les identités entre Office 365 et votre annuaire local.
- Option de synchronisation n’importe quel répertoire, notamment des options d’authentification unique, nécessite que votre attributs d’annuaire local répond aux normes. Les caractéristiques de quels attributs sont utilisés dans votre annuaire et le nettoyage (le cas échéant) est nécessaire sont décrits dans [Prepare to provision utilisateurs par le biais de la synchronisation d’annuaires vers Office 365](prepare-for-directory-synchronization.md). Pour obtenir des instructions sur l’utilisation d’IdFix pour automatiser le nettoyage d’annuaire, voir [installer et exécuter l’outil IdFix d’Office 365](install-and-run-idfix.md) . 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Planifier la façon dont vous allez créer des comptes d’Office 365
Le tableau suivant répertorie les outils de gestion de compte différent :
    
|**Option**|**Remarques**|
|:-----|:-----|
|**Centre d’administration Office 365** | - [Ajouter des utilisateurs individuellement ou par lot à Office 365 - aide d’administration](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -Fournit une interface web simplifiée pour ajouter et modifier des comptes d’utilisateurs. <br> -Ne peut pas être utilisé pour modifier les utilisateurs si la synchronisation d’annuaires est activée (affectation d’emplacement et de licence peut être définie). <br> -Ne peut pas être utilisé avec les options d’authentification unique. <br> |
|**Windows PowerShell** | - [Gérer Office 365 avec Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Permet d’ajouter des utilisateurs dans utilisateurs en bloc à l’aide d’un script Windows PowerShell. <br> -Peut être utilisé pour attribuer un emplacement et des licences à des comptes, quelle que soit la façon dont les comptes sont créés. <br> |
|**Importation en bloc** | - [Ajouter plusieurs utilisateurs en même temps à Office 365 - aide d’administration](add-several-users-at-the-same-time.md) <br> -Permet d’importer un fichier CSV pour ajouter un groupe d’utilisateurs à Office 365. <br> -Ne peut pas être utilisé avec les options d’authentification unique. <br> |
|**Azure Active Directory** | -Vous obtenez une édition gratuite d’Azure Active Directory avec votre abonnement à Office 365. -Vous pouvez effectuer les fonctions, telles que les mots de passe libre-service réinitialiser pour des utilisateurs de nuage et la personnalisation des pages de connexion et d’accès à l’aide de l’édition gratuite.<br> -Pour obtenir des fonctionnalités améliorées, vous pouvez mettre à niveau à l’édition de base ou l’édition premium. Voir les [éditions d’Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) pour la liste des fonctionnalités prises en charge.<br> |
|**Synchronisation d’annuaires** | - [Intégration de vos identités locale avec Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -La synchronisation d’annuaires avec ou sans la synchronisation de mot de passe, utilisez [Azure AD se connecter avec les paramètres express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br>  -Pour plusieurs forêts et des options d’authentification unique, utilisez [personnalisé Installation d’Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430). <br> -Fournit l’infrastructure nécessaire activer l’authentification unique. <br> -Required pour de nombreux scénarios hybrides (migration intermédiaire, Exchange hybride) <br> -Synchronise la sécurité et les groupes à extension messagerie à partir de votre annuaire local. <br> |
   
Quelle que soit la façon dont vous souhaitez ajouter les comptes d’utilisateurs à Office 365, vous devez gérer plusieurs fonctionnalités de compte, telles que l’attribution de licences, en spécifiant l’emplacement et ainsi de suite. Ces fonctionnalités peuvent être gérées à long terme depuis le centre d’administration Office 365, ou vous pouvez également [créer des comptes d’utilisateurs avec Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
Si vous choisissez d’ajouter et de gérer tous vos utilisateurs via le centre d’administration Office 365, vous spécifiez l’emplacement et l’attribution de licences en même temps que la création de compte Office 365. Par conséquent, pas beaucoup de planification est requise.
    
> [!IMPORTANT]
> Création de comptes dans Office 365 sans attribuer une licence (à SharePoint Online, par exemple) signifie que le propriétaire du compte peut afficher le mais portail Office 365 ne peuvent pas accéder à des services au sein de l’abonnement de votre société. Une fois que vous assignez un emplacement et la licence, le compte est répliqué sur l’ou les services que vous avez affecté. L’utilisateur peut se connecter à leur compte et utiliser les services qui vous assignés.