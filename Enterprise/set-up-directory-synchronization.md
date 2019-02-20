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
description: Découvrez comment configurer la synchronisation d'annuaires entre Office 365 et votre annuaire Active Directory local.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085263"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurer la synchronisation d’annuaires pour Office 365

Office 365 utilise le service de gestion des identités des utilisateurs en nuage Azure Active Directory pour gérer les utilisateurs. Vous pouvez également intégrer Active Directory sur site à Azure AD en synchronisant votre environnement local avec Office 365. Une fois que vous avez configuré la synchronisation, vous pouvez décider que l'authentification de l'utilisateur doit avoir lieu dans Azure AD ou dans votre annuaire local.
  
## <a name="office-365-directory-synchronization"></a>Synchronisation d'annuaires Office 365

Vous pouvez utiliser l'identité synchronisée ou une identité fédérée entre votre organisation locale et Office 365. Avec l'identité synchronisée, vous gérez vos utilisateurs sur site et ils sont authentifiés par Azure AD lorsqu'ils utilisent le même mot de passe dans le Cloud en tant que local. Il s'agit du scénario de synchronisation d'annuaire le plus courant. L'authentification directe ou l'identité fédérée, vous permet de gérer vos utilisateurs en local et de les authentifier par votre annuaire local. L'identité fédérée nécessite une configuration supplémentaire et permet à vos utilisateurs de se connecter uniquement une fois. Pour plus d'informations, consultez la rubrique [understandIng Office 365 Identity and Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Vous souhaitez effectuer une mise à niveau à partir de la synchronisation Windows Azure Active Directory (dirSync) vers Azure Active Directory Connect?

Si vous utilisez actuellement dirSync et que vous souhaitez effectuer la mise à niveau, consultez [Azure.com](https://azure.com) pour [obtenir les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Conditions préalables pour Azure AD Connect

Vous bénéficiez d'un abonnement gratuit à Azure AD avec votre abonnement Office 365. Lorsque vous configurez la synchronisation d'annuaires, vous devez installer Azure Active Directory Connect sur l'un de vos serveurs locaux.
  
Pour Office 365, vous devez:
  
- Vérifiez votre domaine local (la procédure vous guidera à travers cela).
- Vous pouvez [attribuer des rôles d'administrateur dans office 365 pour](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) les autorisations d'entreprise pour votre client Office 365 et Active Directory local.

Pour votre serveur local sur lequel vous installez Azure AD Connect, vous aurez besoin des logiciels suivants:
  
|**SYSTÈME d'exploitation du serveur**|**Autres logiciels**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell est installé par défaut, aucune action n'est requise.  <br> -Les versions net 4.5.1 et versions ultérieures sont proposées via Windows Update. Assurez-vous que vous avez installé les dernières mises à jour de Windows Server dans le panneau de configuration. |
|**Windows server 2008 R2 avec Service Pack 1 (SP1)** ou **Windows Server 2012** | -La dernière version de PowerShell est disponible dans Windows Management Framework 4,0. Recherchez-le sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.Net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -La dernière version prise en charge de PowerShell est disponible dans Windows Management Framework 3,0, disponible sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 et versions ultérieures sont disponibles sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Si vous utilisez Azure Active Directory dirSync, le nombre maximal de membres du groupe de distribution que vous pouvez synchroniser à partir de votre Active Directory local vers Azure Active Directory est de 15 000. Pour Azure AD Connect, ce numéro est 50 000. 
  
Pour consulter plus soigneusement le matériel, les logiciels, les exigences de compte et d'autorisation, les exigences de certificat SSL et les limites d'objet pour Azure AD Connect, lisez [Prerequisites pour Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
Vous pouvez également consulter l' [historique des versions](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect pour voir ce qui est inclus et résolu dans chaque version.

## <a name="to-set-up-directory-synchronization"></a>Pour configurer la synchronisation d'annuaires

1. connectez-vous au centre d'administration Office 365 et **** \> choisissez utilisateurs **actifs** dans le volet de navigation de gauche.
2. dans le centre d'administration Office 365, sur la page **utilisateurs actifs** , **sélectionnez plus** \> de **synchronisation**d'annuaires.

    ![Dans le menu autres, sélectionnez synchronisation d'annuaires.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Sur la page **préparation d'Active Directory** , sélectionnez le lien **Télécharger l'outil Microsoft Azure Active Directory Connect** pour commencer. Pour plus d'informations sur le processus d'installation d'Azure Active Directory Connect, reportez-vous à la feuille de [route Azure ad Connect et Azure ad Connect Health installation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Attribuer des licences à des utilisateurs synchronisés

Une fois que vous avez synchronisé vos utilisateurs vers Office 365, ils sont créés, mais vous devez leur attribuer des licences afin qu'ils puissent utiliser les fonctionnalités d'Office 365, telles que le courrier électronique. Pour obtenir des instructions, consultez la rubrique [attribuer des licences aux utilisateurs dans Office 365 pour les entreprises](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Terminer la configuration des domaines

Suivez les étapes de la procédure [créer des enregistrements DNS pour Office 365 lorsque vous gérez vos enregistrements DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) pour terminer la configuration de vos domaines.