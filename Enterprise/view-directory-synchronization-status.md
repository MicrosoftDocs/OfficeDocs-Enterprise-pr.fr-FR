---
title: Afficher l’état de la synchronisation d’annuaires dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d’annuaires. Vous pouvez également afficher son état.
ms.openlocfilehash: 4c2f0baf6d3657e3eb9974ff7d4f8109e52e603b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571037"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Afficher l’état de la synchronisation d’annuaires dans Microsoft 365

Si vous avez intégré Active Directory sur site à Azure AD en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Consulter l’état de synchronisation des annuaires

- Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d’accueil.
- Vous pouvez également **accéder à utilisateurs** \> **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner plus de **More** \> **synchronisation d’annuaires**. Dans le volet **synchronisation d’annuaires** , sélectionnez **accéder à la gestion DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informations sur la page gérer la synchronisation d’annuaires

Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.
  
En cas de problème avec la synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).
  
|**Élément**|**Objet**|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines de votre client Microsoft 365 que vous avez vérifié. |
|**Domaines non vérifiés** | Les domaines que vous avez ajoutés, mais qui n’ont pas été vérifiés. |
|**Synchronisation d’annuaires activée** |True ou false. Indique si la synchronisation d’annuaires est activée. |
|**Dernière synchronisation d’annuaires** | Dernière exécution de la synchronisation d’annuaires. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Synchronisation de mot de passe activée** | True ou false. Indique si la synchronisation de hachage de mot de passe s’est déplacée entre notre client local et votre client Microsoft 365. |
|**Dernière synchronisation de mot de passe** | Dernière exécution de la synchronisation de hachage de mot de passe. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Version du client de synchronisation d’annuaires** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée. |
|**Compte de service de synchronisation d’annuaires** | Affiche le nom de votre compte de service de synchronisation d’annuaires Microsoft 365. |