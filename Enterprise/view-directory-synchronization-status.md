---
title: Afficher le statut de synchronisation d’annuaires dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d’annuaires. Vous pouvez également afficher son statut.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540633"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Afficher le statut de synchronisation d’annuaires dans Office 365
Si vous avez intégré Active Directory local avec Azure AD par la synchronisation de votre environnement sur site avec Office 365, vous pouvez également vérifier l’état de la synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Afficher l’état de la synchronisation des annuaires
- Se connecter au centre d’administration Office 365 et choisissez **l’État de synchronisation d’annuaire** dans la page d’accueil. 
- Sinon, vous pouvez accéder aux **utilisateurs** \> **utilisateurs actifs**, dans la page **utilisateurs actifs** , cliquez sur **plus de** \> **la synchronisation d’annuaires**. Dans le volet de **La synchronisation d’annuaires** , choisissez **accédez à gestion de la synchronisation d’annuaire**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Pour plus d’informations sur la page de la synchronisation d’annuaire gérer

Le tableau suivant répertorie les fonctionnalités que vous pouvez obtenir des informations à propos de la page.
  
Si il existe un problème avec votre la synchronisation d’annuaires, les erreurs sont répertoriés sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, voir [identifier des erreurs de synchronisation d’annuaire dans Office 365](identify-directory-synchronization-errors.md).
  
|**Élément**|**Elle concerne**|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines dans votre organisation cliente Office 365 que vous avez vérifié vous possédez. |
|**Domaines non vérifiées** | Vous avez ajouté, mais n’a ne pas vérifié les domaines. |
|**Synchronisation d’annuaires** |La valeur True ou False. Spécifie si vous avez activé la synchronisation d’annuaire. |
|**Synchronisation d’annuaire le plus récent** | Heure de la dernière exécution de la synchronisation d’annuaire. Affiche un message d’avertissement et un lien vers un outil de dépannage si la dernière synchronisation a plus de trois jours. |
|**Synchronisation de mot de passe activée** | La valeur True ou False. Spécifie si vous disposez de synchronisation de hachage de mot de passe entre notre locale et votre client Office 365. |
|**Dernière synchronisation de mot de passe** | Heure de la dernière exécution de la synchronisation de hachage de mot de passe. Affiche un message d’avertissement et un lien vers un outil de dépannage si la dernière synchronisation a plus de trois jours. |
|**Version de client de synchronisation de répertoire** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée. |
|**Outil IDFix** | Télécharger le lien sur [IDFix](install-and-run-idfix.md), un outil qui vous permet de vérifier votre annuaire Active Directory local. |
|**Compte de service de synchronisation de répertoire** | Affiche le nom de votre compte de service de synchronisation de répertoire Office 365. |