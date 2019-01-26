---
title: Configurer la synchronisation d’annuaires pour Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Découvrez comment configurer la synchronisation d’annuaires entre Office 365 et Active Directory local.
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555440"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurer la synchronisation d’annuaires pour Office 365

Office 365 utilise le service de gestion de l’identité utilisateur basée sur le cloud Azure Active Directory pour gérer les utilisateurs. Vous pouvez également intégrer Active Directory local avec Azure AD par la synchronisation de votre environnement sur site avec Office 365. Après avoir configuré la synchronisation, vous pouvez décider d’avoir leur authentification utilisateur ont lieu dans Azure AD ou au sein de votre annuaire local.
  
## <a name="office-365-directory-synchronization"></a>Synchronisation d’annuaires Office 365

Vous pouvez utiliser soit synchronisée identité ou les identités fédérées entre votre organisation locale et d’Office 365. Avec l’identité synchronisée, vous gérez vos utilisateurs locaux et qu’ils sont authentifiés par Azure AD lorsque qu’ils utilisent le même mot de passe dans le nuage comme local. C’est le scénario de synchronisation de répertoire les plus courants. L’authentification directe ou identité fédérée, vous permet de gérer vos utilisateurs locaux et qu’ils sont authentifiés par votre annuaire local. Identité fédérée requiert une configuration supplémentaire et permet à vos utilisateurs à signer uniquement une seule fois. Pour plus d’informations, voir les [identités Office 365 et Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Vous souhaitez mettre à niveau à partir de synchronisation Windows Azure Active Directory (DirSync) pour Azure Active Directory se connecter ?

Si vous utilisez actuellement DirSync et que vous souhaitez mettre à niveau, consultez sur [azure.com](https://azure.com) pour [obtenir des instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Conditions préalables pour Azure AD se connecter

Vous obtenez un abonnement gratuit à Azure AD avec votre abonnement à Office 365. Lorsque vous configurez la synchronisation d’annuaires, vous allez installer Azure Active Directory se connecter sur un de vos serveurs sur site.
  
Pour Office 365 vous devez :
  
- Vérifiez que votre domaine local (la procédure vous guidera cela).
- Autorisé [assigner des rôles d’administrateur dans Office 365 pour entreprises](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) pour votre client Office 365 et Active Directory local.

Sur lequel vous installez Azure AD se connecter à votre serveur local, vous devez les logiciels suivants :
  
|**Système d’exploitation serveur**|**Autres logiciels**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell est installé par défaut, aucune action n’est requise.  <br> -Net 4.5.1 et versions ultérieures sont proposées par le biais de Windows Update. Assurez-vous que vous avez installé les dernières mises à jour pour Windows Server dans le panneau de configuration. |
|**Windows Server 2008 R2 avec Service Pack 1 (SP1)** ou **Windows Server 2012** | -La dernière version de PowerShell est disponible dans Windows Management Framework 4.0. Rechercher sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -La version la plus récente de PowerShell est disponible dans Windows Management Framework 3.0, disponible sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Si vous utilisez DirSync Azure Active Directory, le nombre maximal de membres de groupe de distribution que vous pouvez synchroniser à partir d’Active Directory local pour Azure Active Directory est de 15 000. Pour se connecter AD Azure, ce numéro est de 50 000. 
  
Pour examiner plus attentivement matériel, logiciel, le compte et les autorisations requises, requise pour les certificats SSL et limites de l’objet pour Azure AD Connect, lisent [les conditions préalables pour Azure Active Directory se connecter](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
Vous pouvez également consulter la Azure AD Connect [historique des versions de version](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) pour voir ce qui est inclus et résolu dans chaque version.

## <a name="to-set-up-directory-synchronization"></a>Pour configurer la synchronisation d’annuaires

1. Se connecter au centre d’administration Office 365 et choisissez **utilisateurs** \> **Utilisateurs actifs** sur le volet de navigation gauche.
2. Dans le centre d’administration Office 365, dans la page **utilisateurs actifs** , choisissez **plus** \> **la synchronisation d’annuaires**.

    ![Dans le menu autres, choisissez la synchronisation d’annuaires](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Dans la page **Préparation d’Active Directory** , sélectionnez le lien de **l’outil de téléchargement Microsoft Azure Active Directory se connecter** pour commencer. Pour plus d’informations sur le processus d’installation Azure Active Directory se connecter, voir [Azure plan AD Connect et Azure AD se connecter d’intégrité de l’installation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Attribuer des licences aux utilisateurs synchronisés

Après avoir synchronisé vos utilisateurs vers Office 365, ils sont créés, mais vous devez leur attribuer des licences afin qu’ils puissent utiliser les fonctionnalités d’Office 365, tels que la messagerie. Pour plus d’informations, voir [attribuer des licences aux utilisateurs dans Office 365 pour entreprises](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Terminer la configuration des domaines

Suivez les étapes [créer des enregistrements DNS pour Office 365 lorsque vous gérez vos enregistrements DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) pour terminer la configuration de vos domaines.