---
title: Consulter l’état de synchronisation des annuaires dans Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d’annuaires. Vous pouvez également afficher son état.
ms.openlocfilehash: 4204d72719e928982b2b6222fb971d62c0f1f8d6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070410"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Consulter l’état de synchronisation des annuaires dans Office 365

Si vous avez intégré Active Directory sur site à Azure AD en synchronisant votre environnement local avec Office 365, vous pouvez également vérifier l’état de votre synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Afficher l’état de la synchronisation d’annuaires

- Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d’accueil.
- Vous pouvez également accéder à **** \> utilisateurs **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner **plus** \> de synchronisation d' **annuaires**. Dans le volet **synchronisation** d’annuaires, sélectionnez **accéder à la gestion DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informations sur la page gérer la synchronisation d’annuaires

Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.
  
En cas de problème avec la synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Office 365](identify-directory-synchronization-errors.md).
  
|**Item**|**Objet**|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines dans votre client 365 Office que vous avez vérifié. |
|**Domaines non vérifiés** | Les domaines que vous avez ajoutés, mais qui n’ont pas été vérifiés. |
|**Synchronisation d’annuaires activée** |True ou false. Indique si la synchronisation d’annuaires est activée. |
|**Dernière synchronisation d’annuaires** | Dernière exécution de la synchronisation d’annuaires. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Synchronisation de mot de passe activée** | True ou false. Spécifie si la synchronisation de hachage de mot de passe entre notre client local et votre client 365 Office est terminée. |
|**Dernière synchronisation de mot de passe** | Dernière exécution de la synchronisation de hachage de mot de passe. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Version du client de synchronisation d’annuaires** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée. |
|**Outil IDFix** | Téléchargez le lien vers [IDFix](install-and-run-idfix.md), un outil que vous pouvez utiliser pour vérifier l’Active Directory local. |
|**Compte de service de synchronisation d’annuaires** | Affiche le nom de votre compte de service de synchronisation d’annuaires Office 365. |