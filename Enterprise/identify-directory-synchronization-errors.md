---
title: Afficher les erreurs de synchronisation d’annuaire dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires dans le centre d’administration Office 365.
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327336"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Afficher les erreurs de synchronisation d’annuaire dans Office 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le centre d’administration d’Office 365. Uniquement les erreurs d’objet utilisateur sont affichés. Pour afficher les erreurs à l’aide de PowerShell, voir [objets identifier avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Après l’affichage, voir [résolution des problèmes de synchronisation d’annuaires pour Office 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans le centre d’administration

Pour afficher les erreurs dans le centre d’administration :
  
1. Connectez-vous à Office 365 à l'aide de votre compte professionnel ou scolaire. 
    
2. Accédez au [Centre d’administration sur Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Dans la page **d’accueil** , vous verrez la vignette de **l’État de synchronisation d’annuaire** . 
    
    ![L’état de synchronisation d’annuaire en mosaïque dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Dans la fenêtre, choisissez l' **État de synchronisation d’annuaire** pour accéder à la page **État de synchronisation d’annuaire** . 
    
    Au bas de la page, vous pouvez voir s’il existe des erreurs de synchronisation d’annuaire.
    
    ![Dans la page État de synchronisation d’annuaire, vous pouvez voir s’il existe des erreurs de synchronisation d’annuaire d’objet](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Choisissez que **nous avons trouvé des erreurs de synchronisation d’annuaire d’objet** pour accéder à une vue détaillée des erreurs de synchronisation de répertoire. 
    
    > [!NOTE]
    > Vous pouvez également accéder à la page **d’erreurs de synchronisation d’annuaire** si vous choisissez **nous avons trouvé des erreurs de synchronisation d’annuaire d’objet** sur la vignette de **l’état de synchronisation d’annuaire** . 
  
![Page d’erreurs de synchronisation d’annuaire](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Dans la page **d’erreurs de synchronisation d’annuaire** , choisissez une des erreurs répertoriées pour afficher le volet de détails avec des informations sur l’erreur et des conseils sur la façon de résoudre le problème. 
