---
title: Configurer la synchronisation d’annuaires pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/15/2020
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Découvrez comment configurer la synchronisation d’annuaires entre Microsoft 365 et votre annuaire Active Directory local.
ms.openlocfilehash: 775ff04976c92d7e937ddc018e0e1dd617c8fca3
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735986"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Configurer la synchronisation d’annuaires pour Microsoft 365

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Microsoft 365 utilise un client Azure Active Directory (Azure AD) pour stocker et gérer les identités pour l’authentification et les autorisations d’accès aux ressources en nuage. 

Si vous disposez d’un service de domaine Active Directory (AD DS) local, vous pouvez synchroniser vos comptes d’utilisateur, groupes et contacts AD DS avec le client Azure AD de votre abonnement Microsoft 365. Il s’agit de l’identité hybride pour Microsoft 365. Voici ses composants.

![Composants de la synchronisation d’annuaires pour Microsoft 365](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect s’exécute sur un serveur local et synchronise vos services de domaine Active Directory avec le client Azure AD. En plus de la synchronisation d’annuaires, vous pouvez également spécifier les options d’authentification suivantes :

- Synchronisation de hachage de mot de passe (hachage)

  Azure AD effectue l’authentification proprement dite.

- Authentification directe (PTA)

  Les services AD DS d’Azure AD effectuent l’authentification.

- Authentification fédérée

  Azure AD redirige l’ordinateur client demandant l’authentification pour contacter un autre fournisseur d’identité.

Pour plus d’informations, consultez la rubrique [identités hybrides](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. vérifier la configuration requise pour Azure AD Connect

Vous obtenez un abonnement Azure AD gratuit avec votre abonnement Microsoft 365. Lorsque vous configurez la synchronisation d’annuaires, vous devez installer Azure AD Connect sur l’un de vos serveurs locaux.
  
Pour Microsoft 365, vous devez :
  
- Vérifiez votre domaine local. L’Assistant Azure AD Connect vous guide à travers cela.
- Obtenez les noms d’utilisateur et les mots de passe des comptes d’administrateur de votre client et AD DS Microsoft 365.

Pour votre serveur local sur lequel vous installez Azure AD Connect, vous aurez besoin des éléments suivants :
  
|**Système d’exploitation du serveur**|**Autres logiciels**|
|:-----|:-----|
|Windows Server 2012 R2 et versions ultérieures | -PowerShell est installé par défaut, aucune action n’est requise.  <br> -Les versions net 4.5.1 et versions ultérieures sont proposées via Windows Update. Assurez-vous que vous avez installé les dernières mises à jour de Windows Server dans le panneau de configuration. |
|Windows Server 2008 R2 avec Service Pack 1 (SP1) * * ou Windows Server 2012 | -La dernière version de PowerShell est disponible dans Windows Management Framework 4,0. Recherchez-le sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | -La dernière version prise en charge de PowerShell est disponible dans Windows Management Framework 3,0, disponible sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Reportez-vous à la rubrique conditions [préalables pour Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) pour obtenir des informations détaillées sur le matériel, les logiciels, les comptes et les autorisations requises, les exigences de certificat SSL et les limites d’objets pour Azure ad Connect.
  
Vous pouvez également consulter l' [historique des versions](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect pour voir ce qui est inclus et résolu dans chaque version.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. installer Azure AD Connect et configurer la synchronisation d’annuaires

Avant de commencer, vérifiez que vous disposez des éléments suivants :

- Le nom d’utilisateur et le mot de passe d’un administrateur général Microsoft 365
- Le nom d’utilisateur et le mot de passe d’un administrateur de domaine AD DS ;
- Quelle méthode d’authentification (hachage, directe, fédéré)
- Si vous souhaitez utiliser l’authentification [unique transparente Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Procédez comme suit :

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) ( https://admin.microsoft.com) et choisissez **utilisateurs** \> **actifs** dans le volet de navigation de gauche.
2. Sur la page **utilisateurs actifs** , choisissez **plus** (trois points) de \> **synchronisation d’annuaires**.
  
3. Sur la page **préparation d’Azure Active Directory** , sélectionnez l’option **accéder au centre de téléchargement pour obtenir le lien vers l’outil Azure ad Connect** pour commencer. 
4. Suivez les étapes de la feuille de [route Azure ad Connect et Azure ad Connect Health installation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. terminer la configuration des domaines

Suivez les étapes de la procédure [créer des enregistrements DNS pour Microsoft 365 lorsque vous gérez vos enregistrements DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) pour terminer la configuration de vos domaines.

## <a name="next-step"></a>Étape suivante

[Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
