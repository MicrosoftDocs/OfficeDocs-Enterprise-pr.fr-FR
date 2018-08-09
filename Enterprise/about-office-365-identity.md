---
title: Présentation des identités d’Office 365 et Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/1/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Découvrez comment l’identité de l’utilisateur est gérée dans Office 365.
ms.openlocfilehash: cdd0ab2306e9a966f308006761a83cda8989b898
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213113"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Présentation des identités d’Office 365 et Azure Active Directory

Office 365 utilise le service identité et authentification utilisateur basée sur le cloud Azure Active Directory (AD Azure) pour gérer les utilisateurs. Choix entre si la gestion des identités est configurée entre votre organisation locale et d’Office 365 est une décision au plus tôt qui est un des fondements de votre infrastructure de cloud. Étant donné que la modification de cette configuration ultérieurement peut être difficile, avec soin les options pour déterminer ce qui convient le mieux aux besoins de votre organisation. Vous pouvez choisir parmi deux modèles d’authentification principal dans Office 365 pour configurer et gérer les comptes d’utilisateurs ; l’authentification sur le nuage et l’authentification fédérée.
  
Il est important de considérer soigneusement le modèle d’authentification et d’identité à utiliser pour obtenir et en cours d’exécution. Pensez à la fois, existante, coût et la complexité à mettre en œuvre et gérer chacune des options d’authentification et d’identité. Ces facteurs sont différents pour chaque organisation ; et vous devez comprendre les concepts clés pour les options d’identité pour vous aider à choisir l’authentification et le modèle d’identité que vous souhaitez utiliser pour votre déploiement.
  
## <a name="cloud-authentication"></a>Authentification dans le nuage

Selon si vous avez ou n’avez pas une existante Active Directory environnement local, vous disposez de plusieurs options pour gérer les services d’authentification et d’identité pour vos utilisateurs avec Office 365.
  
### <a name="cloud-only"></a>Nuage uniquement

Avec le modèle en nuage uniquement, vous gérez vos comptes d’utilisateurs dans Office 365 uniquement. Les serveurs locaux sont nécessaires ; tout est traité dans le nuage par Azure AD. Créer et gérer des utilisateurs dans le centre d’administration d’Office 365 ou à l’aide de Windows PowerShell [applets de commande PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) et d’identité et d’authentification sont gérés entièrement dans le nuage par Azure AD. Le modèle en nuage uniquement est généralement parfaitement dans les cas : 
  
- Vous n’avez aucune autre répertoire d’utilisateur local.
    
- Vous avez un répertoire local très complexe et que vous souhaitez simplement éviter le travail à intégrer.
    
- Vous avez un répertoire local existant, mais que vous souhaitez exécuter une version d’essai ou d’un pilote d’Office 365. Ultérieurement, vous pouvez faire correspondre les utilisateurs dans le nuage pour les utilisateurs locaux lorsque vous êtes prêt à se connecter à votre annuaire local.
    
Pour vous familiariser avec l’identité de nuage, voir [configurer Office 365 pour entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Synchronisation de hachage de mot de passe avec transparente de l’authentification unique

Le moyen le plus simple pour activer l’authentification pour les objets d’annuaire local dans Azure AD. Avec la synchronisation de hachage de mot de passe (pH), vous synchronisez vos objets compte d’utilisateur Active Directory local avec Office 365 et gérer vos utilisateurs locaux. Les hachages de mots de passe utilisateur sont synchronisés à partir d’Active Directory local avec Azure AD afin que les utilisateurs ont le même mot de passe local et dans le nuage. Lorsque les mots de passe sont modifiés ou réinitialiser localement, les nouveaux hachages de mot de passe sont synchronisés avec Azure AD afin que vos utilisateurs peuvent toujours utiliser le même mot de passe pour les ressources de cloud et les ressources locales. Les mots de passe ne sont jamais envoyés à Azure AD ou stockés dans Azure Active Directory en texte clair. Certaines fonctionnalités premium d’Azure AD, telles que la Protection d’identité, nécessitent pH quelle méthode d’authentification est sélectionnée. Avec transparente de l’authentification unique, les utilisateurs sont automatiquement connectés à Azure AD lorsqu’ils sont sur leurs appareils d’entreprise et connectés à votre réseau d’entreprise.
  
Pour plus d’informations sur la [sélection de synchronisation de hachage de mot de passe](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) et [transparente de l’authentification unique](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Authentification pass-through avec transparente de l’authentification unique

Fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel s’exécutant sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec Active Directory local. Avec l’authentification directe (PTA), vous synchronisez l’objets locaux pour le compte d’utilisateur Active Directory avec Office 365 et de gérer vos utilisateurs locaux. Permet à vos utilisateurs à se connecter à des applications à l’aide de leur compte local et le mot de passe et de ressources Office 365 et les locaux. Cette configuration valide les mots de passe des utilisateurs directement par rapport à Active Directory sur site sans envoyer les hachages de mot de passe à Office 365. États de sociétés avec une condition de sécurité à appliquer immédiatement compte d’utilisateur local, utilisent cette méthode d’authentification des stratégies de mot de passe et heures d’ouverture de session. Avec transparente de l’authentification unique, les utilisateurs sont automatiquement connectés à Azure AD lorsqu’ils sont sur leurs appareils d’entreprise et connectés à votre réseau d’entreprise.
  
Pour plus d’informations sur la [sélection de l’authentification directe](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) et [transparente de l’authentification unique](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Options d’authentification fédérée

Si vous avez un existant Active Directory environnement local, vous pouvez intégrer Office 365 avec votre annuaire à l’aide de l’authentification fédérée pour gérer les services d’authentification et d’identité pour vos utilisateurs dans Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identité fédérée avec Active Directory Federation Services (ADFS)

Principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, objets d’annuaire sont synchronisés avec Office 365 et locaux comptes d’utilisateurs sont gérés sur site. Avec AD FS, les utilisateurs ont le même mot de passe local et dans le nuage et qu’ils n’ont pas à se reconnecter à utiliser Office 365. Ce modèle d’authentification fédérée peut fournir des conditions d’authentification supplémentaires, telles que l’authentification par carte à puce ou une authentification multifacteur de tiers et est généralement requis lorsque les organisations disposent d’une demande d’authentification prise en charge pas en mode natif par Azure AD.
  
En savoir plus sur le [choix d’une identité fédérée avec AD FS](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Fournisseurs d’authentification et d’identité tiers

Objets d’annuaire peuvent être synchronisés avec Office 365 et locaux l’accès aux ressources dans le nuage est principalement géré par un fournisseur d’identité de tiers (IdP). Si votre organisation utilise une solution tierce fédération, vous pouvez configurer l’authentification avec cette solution pour Office 365 à condition que la solution de fédération tiers est compatible avec Azure AD.
  
Pour plus d’informations sur la [compatibilité de fédération Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configuration d’identité et authentification avec Office 365

Intégration de vos annuaires locaux avec Office 365 et Azure AD a été simplifié avec [Azure AD se connecter](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect est la meilleure façon de se connecter à vos répertoires et recommandation de Microsoft pour les organisations à synchroniser les utilisateurs vers le nuage.
  
Vous pouvez également utiliser les conseillers Azure AD : [Gestionnaire d’Azure AD se connecter](https://aka.ms/aadconnectpwsync), le [Gestionnaire de déploiement d’AD FS](https://aka.ms/adfsguidance)et le [guide de configuration Azure AD Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Formation vidéo

Pour plus d’informations, consultez le cours vidéo [Office 365 : gérer des identités à l’aide des Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), proposée par apprentissage LinkedIn.
  
## <a name="see-also"></a>Voir aussi

[Préparer la mise en service des utilisateurs via la synchronisation d’annuaires vers Office 365](https://support.office.com/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e)
  
[Connecter PowerShell aux services Office 365](https://support.office.com/article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
  
[Résolution des problèmes de synchronisation d’annuaires pour Office 365](https://support.office.com/article/fixing-problems-with-directory-synchronization-for-office-365-79c43023-5a47-45ae-8068-d8a26eee6bc2d)
  

