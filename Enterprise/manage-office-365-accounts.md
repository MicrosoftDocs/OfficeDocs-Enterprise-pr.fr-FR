---
title: Outils permettant de gérer les comptes Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Découvrez les outils à utiliser pour gérer vos utilisateurs de Microsoft 365. '
ms.openlocfilehash: 324a95e111812180cefffe98f2d7ec3c64e956b1
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230230"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>Outils permettant de gérer les comptes Microsoft 365

Vous pouvez gérer les utilisateurs de Microsoft 365 de différentes manières, en fonction de votre configuration. Vous pouvez gérer les utilisateurs dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com), Windows PowerShell, dans les services de domaine Active Directory (AD DS) ou dans le portail d’administration Azure Active Directory (Azure AD). 

Dès que vous achetez Microsoft 365, le centre d’administration et Windows PowerShell peuvent être utilisés pour gérer les comptes. Lors de la gestion des identités de Cloud, toutes les personnes de votre organisation ont un ID d’utilisateur et un mot de passe distincts pour Microsoft 365. Si vous souhaitez intégrer votre infrastructure locale et que les comptes d’utilisateurs sont synchronisés avec Microsoft 365, vous pouvez utiliser Azure AD Connect pour assurer la synchronisation des identités et des mots de passe pour la fonctionnalité d’authentification unique.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planifier l’emplacement et la façon dont vous allez gérer vos comptes d’utilisateurs

L’emplacement et la façon dont vous pouvez gérer vos comptes d’utilisateurs dépend du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles globaux sont l’authentification Cloud et l’authentification fédérée.
  
### <a name="cloud-authentication"></a>Authentification Cloud

- Authentification Cloud : créez et gérez les utilisateurs dans le centre d’administration Microsoft 365. Vous pouvez également utiliser Windows PowerShell ou Azure AD. 
    
- Synchronisation de hachage de mot de passe (hachage) avec authentification unique transparente : le moyen le plus simple d’activer l’authentification pour les objets AD DS dans Azure AD. Avec hachage, vous synchronisez vos objets de compte d’utilisateur AD DS avec Microsoft 365 et vous gérez vos utilisateurs en local. 
    
- L’authentification directe (directe) avec authentification unique transparente fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel exécuté sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre service AD DS. 
    
### <a name="federated-authentication"></a>Authentification fédérée

- Options d’authentification fédérée-principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, les objets AD DS sont synchronisés avec Microsoft 365 et les comptes d’utilisateurs sont gérés en local. 
    
- [Fournisseurs d’identité et d’authentification tiers](about-office-365-identity.md) : les objets AD DS peuvent être synchronisés avec Microsoft 365 et l’accès aux ressources de Cloud est principalement géré par un fournisseur d’identité tiers (IDP). 
    
## <a name="managing-accounts"></a>Gestion des comptes

Lorsque vous décidez de la manière dont votre organisation créera et gérera les comptes, tenez compte des exigences suivantes :
  
- Le logiciel de synchronisation d’annuaires doit être installé sur les serveurs au sein de votre environnement local pour connecter les identités entre Microsoft 365 et AD DS.
    
- Toute option de synchronisation d’annuaires, y compris les options SSO, requiert des attributs AD DS conformes aux normes. Les spécificités des attributs utilisés dans votre répertoire et le nettoyage (le cas échéant) requis sont décrits dans [Prepare to provision Users with Directory Synchronization to Microsoft 365](prepare-for-directory-synchronization.md). Voir [Download and Run the Microsoft 365 ID Fix Tool](install-and-run-idfix.md) pour obtenir des instructions sur l’utilisation de Fix ID pour automatiser le nettoyage d’annuaire. 
    
- Planifiez la façon dont vous allez créer des comptes Microsoft 365.
    
    Le tableau suivant répertorie les différents outils de gestion des comptes.
    
|**Option**|**Notes**|
|:-----|:-----|
|Centre d’administration  <br/> |[Ajouter des utilisateurs individuellement ou en bloc](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  Fournit une interface Web simple pour ajouter et modifier des comptes d’utilisateurs.  <br/>  Ne peut pas être utilisé pour modifier des utilisateurs si la synchronisation d’annuaires est activée (l’attribution d’emplacement et de licence peut être définie).  <br/>  Ne peut pas être utilisé avec les options d’authentification unique.  <br/> |
|Windows PowerShell  <br/> |[Gérer Microsoft 365 avec Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Vous permet d’ajouter des utilisateurs en bloc à l’aide d’un script Windows PowerShell.  <br/>  Peut être utilisé pour affecter un emplacement et des licences aux comptes, quelle que soit la façon dont les comptes sont créés.  <br/> |
|Importation en bloc  <br/> |[Ajouter plusieurs utilisateurs simultanément](add-several-users-at-the-same-time.md) <br/>  Permet d’importer un fichier CSV pour ajouter un groupe d’utilisateurs à Microsoft 365.  <br/>  Ne peut pas être utilisé avec les options d’authentification unique.  <br/> |
|Azure AD  <br/> |Vous obtenez une édition gratuite d’Azure AD avec votre abonnement Microsoft 365. Vous pouvez effectuer des fonctions comme la réinitialisation du mot de passe en libre-service pour les utilisateurs du Cloud, et la personnalisation des pages de connexion et du panneau d’accès à l’aide de l’édition gratuite. Pour bénéficier de fonctionnalités améliorées, vous pouvez effectuer une mise à niveau vers la version Basic Edition, Azure AD Premium P1 ou Azure AD Premium P2. Pour obtenir la liste des fonctionnalités prises en charge, reportez-vous à [Azure ad Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) .  <br/> |
|Synchronisation d’annuaires  <br/> |[Intégration de vos identités locales à Azure AD](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Pour la synchronisation d’annuaires avec ou sans synchronisation de mot de passe, utilisez [les paramètres Azure ad Connect avec Express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Pour plusieurs forêts et options d’authentification unique, utilisez [l’installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Fournit l’infrastructure nécessaire à l’activation de l’authentification unique.  <br/>  Requis pour de nombreux scénarios hybrides :  <br/>  Migration intermédiaire  <br/>  Exchange hybride  <br/>  Synchronise les groupes à extension messagerie et de sécurité à partir de votre AD DS.  <br/> |
   
- Quelle que soit la façon dont vous envisagez d’ajouter les comptes d’utilisateur à Microsoft 365, vous devez gérer plusieurs fonctionnalités de compte, telles que l’attribution de licences, la spécification de l’emplacement, etc. Ces fonctionnalités peuvent être gérées à long terme à partir du centre d’administration ou vous pouvez également [créer des comptes d’utilisateur avec PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Si vous décidez d’ajouter et de gérer tous vos utilisateurs par le biais du centre d’administration, vous devez spécifier l’emplacement et attribuer des licences en même temps que la création du compte Microsoft 365. Par conséquent, la planification n’est pas obligatoire.
    
    > [!IMPORTANT]
    > La création de comptes dans Microsoft 365 sans l’attribution d’une licence (à SharePoint Online, par exemple) signifie que le propriétaire du compte peut consulter le centre d’administration Microsoft 365, mais qu’il ne peut accéder à aucun des services de l’abonnement de votre entreprise. Une fois que vous avez affecté un emplacement et la licence, le compte est répliqué vers le service ou les services que vous avez attribués. L’utilisateur peut se connecter à son compte et utiliser les services que vous lui avez attribués. 
  
## <a name="next-steps"></a>Étapes suivantes

[Intégration de Microsoft 365 aux environnements locaux](office-365-integration.md)
  
## <a name="see-also"></a>Voir aussi

[Gérer les utilisateurs et les groupes dans Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

