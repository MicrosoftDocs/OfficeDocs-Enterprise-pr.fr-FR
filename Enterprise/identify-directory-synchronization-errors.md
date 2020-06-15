---
title: Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires dans le centre d’administration Microsoft 365.
ms.openlocfilehash: d10abc29a08da4352d4c0779698e2062175008b4
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711644"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com). Seules les erreurs d’objet utilisateur sont affichées. Pour afficher les erreurs à l’aide de PowerShell, consultez la rubrique [identifier les objets avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Après l’affichage, consultez la rubrique [résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans le centre d’administration

Pour afficher les erreurs dans le centre d’administration :
  
1. Connectez-vous à Microsoft 365 à l’aide de votre compte professionnel ou scolaire. 
    
2. Accédez à la rubrique [à propos du centre d’administration](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. Sur la page d' **Accueil** , vous verrez la vignette d' **État DirSync** . 
    
    ![Vignette d’État DirSync dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. Sur la vignette, choisissez **État DirSync** pour accéder à la page État de la **synchronisation d’annuaires** . 
    
    Au bas de la page, vous pouvez voir s’il existe des erreurs DirSync.
    
    ![Sur la page État de la synchronisation d’annuaires, vous pouvez voir s’il existe des erreurs d’objet DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Choisissez des **Erreurs d’objets DirSync trouvés** pour accéder à une vue détaillée des erreurs de synchronisation d’annuaires. 
    
    > [!NOTE]
    > Vous pouvez également accéder à la page des **Erreurs** DirSync si vous choisissez des **Erreurs d’objet DirSync** sur la vignette d' **État DirSync** . 
  
![Page des erreurs DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. Sur la page **Erreurs de synchronisation d’annuaire** , choisissez l’une des erreurs indiquées pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la résolution de l’erreur. 
