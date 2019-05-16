---
title: Présentation de l’identité Office 365 et d’Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Découvrez comment l’identité de l’utilisateur est gérée dans Office 365.
ms.openlocfilehash: 85cfce4b08236bfcee74b6fe6d9c29766e7211c6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068760"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Présentation de l’identité Office 365 et d’Azure Active Directory

Office 365 utilise l’identité de l’utilisateur en nuage et le service d’authentification Azure Active Directory (Azure AD) pour gérer les utilisateurs. Le choix de la configuration de la gestion des identités entre votre organisation locale et Office 365 est une décision précoce qui fait partie des bases de votre infrastructure cloud. Étant donné que la modification ultérieure de cette configuration peut être difficile, étudiez attentivement les options permettant de déterminer ce qui convient le mieux aux besoins de votre organisation. Vous pouvez choisir entre deux modèles d’authentification principaux dans Office 365 pour configurer et gérer les comptes d’utilisateur; **authentification Cloud** et **authentification fédérée**.
  
Il est important de déterminer avec soin les modèles d’authentification et d’identité à utiliser pour être opérationnels. Réfléchissez au temps, à la complexité et au coût de l’implémentation et de la maintenance de chacune des options d’authentification et d’identité. Ces facteurs sont différents pour chaque organisation; et vous devez comprendre les concepts clés pour les options d’identité pour vous aider à choisir le modèle d’authentification et d’identité que vous souhaitez utiliser pour votre déploiement.
  
## <a name="cloud-authentication"></a>Authentification Cloud

Selon que vous disposez ou non d’un environnement Active Directory local, vous disposez de plusieurs options pour gérer l’authentification et les services d’identité de vos utilisateurs avec Office 365.
  
### <a name="cloud-only"></a>Cloud uniquement

Avec le modèle de Cloud uniquement, vous gérez vos comptes d’utilisateur dans Office 365 uniquement. Aucun serveur local n’est requis; Il est tous géré dans le Cloud par Azure AD. La création et la gestion des utilisateurs dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) ou à l’aide des applets de commande [PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) Windows PowerShell, ainsi que l’identité et l’authentification sont entièrement gérées dans le Cloud par Azure ad. Le modèle de Cloud uniquement est généralement un bon choix si: 
  
- Vous n’avez pas d’autre répertoire d’utilisateur local.
    
- Vous disposez d’un annuaire local très complexe et souhaitez simplement éviter le travail à s’intégrer.
    
- Vous disposez d’un annuaire local existant, mais vous souhaitez exécuter une version d’évaluation ou une version pilote d’Office 365. Par la suite, vous pouvez faire correspondre les utilisateurs du Cloud aux utilisateurs locaux lorsque vous êtes prêt à vous connecter à votre annuaire local.
    
Pour commencer à utiliser l’identité Cloud, consultez la rubrique [set up Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Synchronisation de hachage de mot de passe avec authentification unique transparente

Le moyen le plus simple d’activer l’authentification pour les objets d’annuaire locaux dans Azure AD. La synchronisation de hachage de mot de passe (hachage) vous permet de synchroniser vos objets de compte d’utilisateur Active Directory sur site avec Office 365 et de gérer vos utilisateurs en local. Les hachages des mots de passe des utilisateurs sont synchronisés de votre annuaire Active Directory local vers Azure AD afin que les utilisateurs aient le même mot de passe sur site et dans le Cloud. Lorsque les mots de passe sont modifiés ou réinitialisés en local, les nouveaux hachages de mot de passe sont synchronisés avec Azure AD afin que les utilisateurs puissent toujours utiliser le même mot de passe pour les ressources en nuage et les ressources locales. Les mots de passe ne sont jamais envoyés à Azure AD ou stockés dans Azure AD en texte clair. Certaines fonctionnalités avancées d’Azure AD, telles que la protection des identités, nécessitent hachage, quelle que soit la méthode d’authentification sélectionnée. Avec l’authentification unique transparente, les utilisateurs sont automatiquement connectés à Azure AD lorsqu’ils se trouvent sur leurs appareils d’entreprise et connectés à votre réseau d’entreprise.
  
En savoir plus sur le choix de la [synchronisation de hachage de mot de passe](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) et de l' [authentification unique transparente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Authentification directe avec authentification unique transparente

Fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel exécuté sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre annuaire Active Directory local. Avec l’authentification directe (directe), vous synchronisez les objets de compte d’utilisateur Active Directory locaux avec Office 365 et vous gérez vos utilisateurs en local. Permet à vos utilisateurs de se connecter à des ressources et des applications locales et Office 365 à l’aide de leur compte local et de leur mot de passe. Cette configuration valide les mots de passe des utilisateurs directement par rapport à votre annuaire Active Directory local sans envoyer de hachage de mot de passe à Office 365. Les entreprises dont la sécurité est requise pour appliquer immédiatement les États locaux des comptes d’utilisateur, les stratégies de mot de passe et les heures d’ouverture de session utiliseront cette méthode d’authentification. Avec l’authentification unique transparente, les utilisateurs sont automatiquement connectés à Azure AD lorsqu’ils se trouvent sur leurs appareils d’entreprise et connectés à votre réseau d’entreprise.
  
En savoir plus sur le [choix de l’authentification directe et de l’authentification](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) [unique transparente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Options d’authentification fédérée

Si vous disposez d’un environnement Active Directory existant en local, vous pouvez intégrer Office 365 à votre annuaire à l’aide de l’authentification fédérée pour gérer les services d’authentification et d’identité pour vos utilisateurs dans Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identité fédérée avec Active Directory Federation Services (AD FS)

Principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, les objets d’annuaire locaux sont synchronisés avec Office 365 et les comptes d’utilisateurs sont gérés en local. Avec les services ADFS (Active Directory Federation Services), les utilisateurs ont le même mot de passe sur site et dans le Cloud et ils n’ont pas besoin de se connecter à nouveau pour utiliser Office 365. Ce modèle d’authentification fédérée peut fournir des exigences d’authentification supplémentaires, telles que l’authentification par carte à puce ou une authentification multifacteur tierce et est généralement requise lorsque les organisations ont une exigence d’authentification. non pris en charge en mode natif par Azure AD.
  
En savoir plus sur le [choix de l’identité fédérée avec AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Fournisseurs d’identité et d’authentification tiers

Les objets d’annuaire locaux peuvent être synchronisés avec Office 365 et l’accès aux ressources de Cloud est principalement géré par un fournisseur d’identité tiers (IdP). Si votre organisation utilise une solution de Fédération tierce, vous pouvez configurer l’authentification avec cette solution pour Office 365 à condition que la solution de Fédération tierce soit compatible avec Azure AD.
  
En savoir plus sur la [compatibilité de Fédération Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configuration de l’identité et de l’authentification avec Office 365

L’intégration de vos annuaires locaux avec Office 365 et Azure AD a été simplifiée avec [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect est la meilleure façon de connecter vos annuaires et est recommandé par Microsoft pour les organisations de synchroniser leurs utilisateurs avec le Cloud.
  
Vous pouvez également utiliser les conseillers Azure AD: le [conseiller Azure ad Connect](https://aka.ms/aadconnectpwsync), le [conseiller de déploiement AD FS](https://aka.ms/adfsguidance)et le [Guide de configuration d’Azure ad Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Vidéo de formation

Pour plus d’informations, reportez-vous au cours vidéo [Office 365: gérer les identités à l’aide d’Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), qui vous a été présenté par LinkedIn Learning.
