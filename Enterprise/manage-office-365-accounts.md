---
title: Outils permettant de gérer les comptes Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
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
description: 'Découvrez les outils à utiliser pour gérer vos utilisateurs Office 365, ainsi que la manière dont vous pouvez les utiliser en fonction de la gestion des identités des utilisateurs. '
ms.openlocfilehash: fb98c7103aaadb16ac6f7d459a2595022110bb94
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487070"
---
# <a name="tools-to-manage-office-365-accounts"></a>Outils permettant de gérer les comptes Office 365

Vous pouvez gérer les utilisateurs d'Office 365 de différentes manières, en fonction de votre configuration. Vous pouvez gérer les utilisateurs dans le [Centre d'administration 365 de Microsoft](https://admin.microsoft.com), Windows PowerShell, votre annuaire local ou dans le portail d'administration Azure Active Directory. Dès que vous achetez Office 365, le centre d'administration et Windows PowerShell peuvent être utilisés pour gérer les comptes. Lors de la gestion des identités de Cloud, toutes les personnes de votre organisation ont un ID d'utilisateur et un mot de passe distincts pour Office 365. Si vous souhaitez effectuer une intégration avec votre infrastructure locale et que des comptes d'utilisateurs sont synchronisés avec Office 365, vous pouvez utiliser Azure Active Directory Connect pour assurer la synchronisation des identités et éventuellement une synchronisation de mot de passe, ou complète fonctionnalité d'authentification unique.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planifier l'emplacement et la façon dont vous allez gérer vos comptes d'utilisateurs

L'emplacement et la façon dont vous pouvez gérer vos comptes d'utilisateurs dépend du modèle d'identité que vous souhaitez utiliser pour votre Office 365. Les deux modèles globaux sont l'authentification Cloud et l'authentification fédérée.
  
### <a name="cloud-authentication"></a>Authentification Cloud

- [Authentification Cloud](about-office-365-identity.md#cloud-authentication) : créer et gérer des utilisateurs dans le centre d'administration, vous pouvez également utiliser Windows PowerShell ou Azure Active Directory pour gérer vos utilisateurs. 
    
- [Synchronisation de hachage de mot de passe avec authentification unique transparente](about-office-365-identity.md) : le moyen le plus simple d'activer l'authentification pour les objets d'annuaire locaux dans Azure ad. La synchronisation de hachage de mot de passe (hachage) vous permet de synchroniser vos objets de compte d'utilisateur Active Directory sur site avec Office 365 et de gérer vos utilisateurs en local. 
    
- [Authentification directe avec authentification unique transparente](about-office-365-identity.md) : fournit une validation de mot de passe simple pour les services d'authentification Azure ad à l'aide d'un agent logiciel exécuté sur un ou plusieurs serveurs locaux afin de valider directement les utilisateurs avec votre Active Directory en local. 
    
### <a name="federated-authentication"></a>Authentification fédérée

- [Options d'authentification fédérée](about-office-365-identity.md#federated-authentication-options) -principalement pour les grandes organisations d'entreprise avec des exigences d'authentification plus complexes, les objets d'annuaire locaux sont synchronisés avec Office 365 et les comptes d'utilisateurs sont gérés en local. 
    
- Les [fournisseurs d'identité et d'authentification tiers](about-office-365-identity.md) -les objets d'annuaire locaux peuvent être synchronisés avec Office 365 et l'accès aux ressources de Cloud est principalement géré par un fournisseur d'identité tiers (IDP). 
    
## <a name="managing-accounts"></a>Gestion des comptes

Lorsque vous décidez de la manière dont votre organisation créera et gérera les comptes, tenez compte des éléments suivants:
  
- Le logiciel de synchronisation d'annuaires doit être installé sur les serveurs au sein de votre environnement local pour connecter les identités entre Office 365 et votre annuaire local.
    
- Toute option de synchronisation d'annuaires, y compris les options SSO, requiert des attributs d'annuaire sur site conformes aux normes. Les spécificités des attributs utilisés dans votre répertoire et le nettoyage (le cas échéant) requis sont décrits dans prepare [to provision Users with Directory Synchronization to Office 365](prepare-for-directory-synchronization.md). Voir [installer et exécuter l'outil IdFix Office 365](install-and-run-idfix.md) pour obtenir des instructions sur l'utilisation de IdFix pour automatiser le nettoyage d'annuaire. 
    
- Planifiez la façon dont vous allez créer des comptes Office 365.
    
    Le tableau suivant répertorie les différents outils de gestion des comptes.
    
|**Option**|**Notes**|
|:-----|:-----|
|Centre d'administration  <br/> |[Ajouter des utilisateurs individuellement ou en bloc à Office 365-aide de l'administrateur](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Fournit une interface Web simple pour ajouter et modifier des comptes d'utilisateurs.  <br/>  Ne peut pas être utilisé pour modifier des utilisateurs si la synchronisation d'annuaires est activée (l'attribution d'emplacement et de licence peut être définie).  <br/>  Ne peut pas être utilisé avec les options d'authentification unique.  <br/> |
|Windows PowerShell  <br/> |[Gérer Office 365 avec Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Vous permet d'ajouter des utilisateurs en bloc à l'aide d'un script Windows PowerShell.  <br/>  Peut être utilisé pour affecter un emplacement et des licences aux comptes, quelle que soit la façon dont les comptes sont créés.  <br/> |
|Importation en bloc  <br/> |[Ajouter plusieurs utilisateurs simultanément à Office 365 - Aide aux administrateurs](add-several-users-at-the-same-time.md) <br/>  Permet d'importer un fichier CSV pour ajouter un groupe d'utilisateurs à Office 365.  <br/>  Ne peut pas être utilisé avec les options d'authentification unique.  <br/> |
|Azure Active Directory  <br/> |Vous obtenez une édition gratuite d'Azure Active Directory avec votre abonnement Office 365. Vous pouvez effectuer des fonctions comme la réinitialisation du mot de passe en libre-service pour les utilisateurs du Cloud, et la personnalisation des pages de connexion et du panneau d'accès à l'aide de l'édition gratuite. Pour bénéficier de fonctionnalités améliorées, vous pouvez effectuer une mise à niveau vers la version Standard Edition ou Premium. Pour obtenir la liste des fonctionnalités prises en charge, rePortez-vous à [Azure Active Directory Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) .  <br/> |
|Synchronisation d’annuaires  <br/> |[Intégration de vos identités locales à Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Pour la synchronisation d'annuaires avec ou sans synchronisation de mot de passe, utilisez [les paramètres Azure ad Connect avec Express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Pour plusieurs forêts et options d'authentification unique, utilisez [l'installation personnalisée d'Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Fournit l'infrastructure nécessaire à l'activation de l'authentification unique.  <br/>  Requis pour de nombreux scénarios hybrides:  <br/>  Migration intermédiaire  <br/>  Exchange hybride  <br/>  Synchronise les groupes à extension messagerie et de sécurité à partir de votre annuaire local.  <br/> |
   
- Quelle que soit la façon dont vous envisagez d'ajouter les comptes d'utilisateur à Office 365, vous devez gérer plusieurs fonctionnalités de compte, telles que l'attribution de licences, la spécification de l'emplacement, etc. Ces fonctionnalités peuvent être gérées à long terme à partir du centre d'administration ou vous pouvez également [créer des comptes d'utilisateur avec Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Si vous décidez d'ajouter et de gérer tous vos utilisateurs par le biais du centre d'administration, vous devez spécifier l'emplacement et attribuer des licences en même temps que la création du compte Office 365. Par conséquent, la planification n'est pas obligatoire.
    
    > [!IMPORTANT]
    > La création de comptes dans Office 365 sans l'attribution d'une licence (à SharePoint Online, par exemple) signifie que le propriétaire du compte peut consulter le portail Office 365, mais ne peut accéder à aucun des services de l'abonnement de votre entreprise. Une fois que vous avez affecté un emplacement et la licence, le compte est répliqué vers le service ou les services que vous avez attribués. L'utilisateur peut se connecter à son compte et utiliser les services que vous lui avez attribués. 
  
## <a name="next-steps"></a>Étapes suivantes

[Intégration d'Office 365 aux environnements locaux](office-365-integration.md)
  
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d'utilisateurs dans Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

