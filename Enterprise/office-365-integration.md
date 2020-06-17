---
title: Intégration de Microsoft 365 aux environnements locaux
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Découvrez comment intégrer Microsoft 365 à vos services d’annuaire existants.
ms.openlocfilehash: 456e3e73451a07750d707e2fca52df9214c2dfaa
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736032"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Intégration de Microsoft 365 aux environnements locaux

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Vous pouvez intégrer Microsoft 365 à vos services d’annuaire existants et à une installation locale d’Exchange Server, Skype entreprise Server 2015 ou SharePoint Server.
  
 - Lorsque vous intégrez des services d’annuaire, vous pouvez synchroniser et gérer les comptes d’utilisateur pour les deux environnements. Vous pouvez également ajouter la synchronisation de hachage de mot de passe ou l’authentification unique (SSO) de sorte que les utilisateurs puissent se connecter aux deux environnements à l’aide de leurs informations d’identification locales.
 - Lorsque vous intégrez des produits serveur sur site, vous créez un environnement hybride. Un environnement hybride peut vous aider lors de la migration des utilisateurs ou des informations vers Microsoft 365, ou vous pouvez continuer à avoir des utilisateurs ou des informations sur site et d’autres dans le Cloud. Pour plus d’informations sur les environnements hybrides, consultez la rubrique [vue d’ensemble du Cloud hybride](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).

Vous pouvez également utiliser les conseillers Azure Active Directory (Azure AD) pour obtenir des conseils de configuration personnalisés (vous devez être connecté à Microsoft 365) :

- [Synchroniser les utilisateurs du répertoire de votre organisation](https://aka.ms/aadconnectpwsync)
- [Conseiller de déploiement AD FS](https://aka.ms/adfsguidance)
- [Guide de configuration d’Azure AD](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Avant de commencer

Avant d’intégrer Microsoft 365 et un environnement local, vous devez également participer à la planification du [réseau et au réglage des performances](network-planning-and-performance.md). Vous voudrez également comprendre les modèles d' [identité](about-office-365-identity.md)disponibles. 

Consultez la rubrique [où gérer les comptes microsoft 365](manage-office-365-accounts.md) pour obtenir la liste des outils que vous pouvez utiliser pour gérer les utilisateurs et les comptes Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-directory-services"></a>Intégration de Microsoft 365 avec les services d’annuaire
Si vous avez des comptes d’utilisateur existants dans un annuaire local, vous ne souhaitez pas recréer tous ces comptes dans Microsoft 365 et risquez d’introduire des différences ou des erreurs entre les environnements. La synchronisation d’annuaires vous permet de mettre en miroir ces comptes entre vos environnements en ligne et locaux. Avec la synchronisation d’annuaires, vos utilisateurs n’ont pas à se souvenir des nouvelles informations pour chaque environnement, et vous n’avez pas à créer ou mettre à jour les comptes deux fois. Vous devrez [préparer votre annuaire local pour la](prepare-for-directory-synchronization.md) synchronisation d’annuaires, vous pouvez le faire manuellement ou utiliser l' [outil IdFix](install-and-run-idfix.md) (l’outil IdFix fonctionne uniquement avec les services de domaine Active Directory [AD DS]). 
  
![Utiliser la synchronisation d’annuaires pour maintenir la synchronisation des informations sur les comptes d’utilisateur en ligne et en ligne](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Si vous souhaitez que les utilisateurs puissent se connecter à Microsoft 365 avec leurs informations d’identification locales, vous pouvez également configurer l’authentification unique. Avec l’authentification unique, Microsoft 365 est configuré pour approuver l’environnement local pour l’authentification des utilisateurs.
  
![Avec l’authentification unique, le même compte est disponible dans les environnements locaux et en ligne.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Différentes techniques de gestion de compte d’utilisateur fournissent différentes expériences pour vos utilisateurs, comme illustré dans le tableau suivant.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>Synchronisation d’annuaires avec ou sans synchronisation de hachage de mot de passe ou authentification directe

Un utilisateur se connecte à son environnement local à l’aide de son compte d’utilisateur (DOMAINE\nom d’utilisateur). Lorsque les utilisateurs accèdent à Microsoft 365, ils doivent se reconnecter avec leur compte professionnel ou scolaire (user@domain.com). Le nom d’utilisateur est le même dans les deux environnements. Lorsque vous ajoutez une synchronisation de hachage de mot de passe ou une authentification directe, l’utilisateur a le même mot de passe pour les deux environnements, mais il devra de nouveau fournir ces informations d’identification lors de la connexion à Microsoft 365. La synchronisation d’annuaires avec la synchronisation de hachage de mot de passe est le scénario de synchronisation d’annuaire le plus couramment utilisé.

Pour configurer la synchronisation d’annuaires, utilisez Azure Active Directory Connect. Pour obtenir des instructions, consultez la section [configuration de la synchronisation d’annuaires pour Microsoft 365](set-up-directory-synchronization.md)et [Azure ad Connect with Express Settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).

En savoir plus sur la [préparation de la synchronisation d’annuaires avec Microsoft 365](prepare-for-directory-synchronization.md) et [l’intégration de vos identifications locales à Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>Synchronisation d’annuaires avec SSO

Un utilisateur se connecte à son environnement local à l’aide de son compte d’utilisateur. Lorsque les utilisateurs accèdent à Microsoft 365, ils se connectent automatiquement ou se connectent à l’aide des mêmes informations d’identification qu’ils utilisent pour leur environnement local (DOMAINE\nom d’utilisateur).

Pour configurer l’authentification unique, vous devez également utiliser Azure AD Connect. Pour obtenir des instructions, consultez [l’installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).

En savoir plus sur [l’authentification unique pour les applications dans Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect remplace les anciennes versions des outils d’intégration des identités telles que DirSync et Azure AD Sync. Pour plus d’informations, voir [qu’est-ce que l’identité hybride avec Azure Active Directory ?](https://go.microsoft.com/fwlink/p/?LinkId=527969). Si vous souhaitez effectuer une mise à jour à partir d’Azure Active Directory Sync vers Azure AD Connect, consultez [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240). 

Consultez également la rubrique [Deploy microsoft 365 Directory Synchronization in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
