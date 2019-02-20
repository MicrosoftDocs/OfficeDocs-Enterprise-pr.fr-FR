---
title: Désactiver la synchronisation d’annuaires pour Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Découvrez comment utiliser PowerShell pour désactiver la synchronisation d'annuaires pour Office 365
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085073"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Désactiver la synchronisation d’annuaires pour Office 365
Vous pouvez utiliser PowerShell pour désactiver la synchronisation d'annuaires. Toutefois, il n'est pas recommandé de désactiver la synchronisation d'annuaires en tant qu'étape de résolution des problèmes. Si vous avez besoin d'aide pour résoudre les problèmes liés à la synchronisation d'annuaires, consultez l'article [résolution des problèmes liés à la synchronisation d'annuaires pour Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits professionnels si nécessaire.
  
## <a name="turn-off-directory-synchronization"></a>Désactiver la synchronisation d'annuaires  
Pour désactiver la synchronisation d'annuaires:
  
1. Tout d'abord, installez les logiciels requis et connectez-vous à votre abonnement Office 365. Pour obtenir des instructions pour les deux, consultez la rubrique [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Utilisez [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) pour désactiver la synchronisation d'annuaires: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```