---
title: Désactivation de la synchronisation d’annuaires pour Microsoft 365
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Découvrez comment utiliser PowerShell pour désactiver la synchronisation d’annuaires pour Microsoft 365
ms.openlocfilehash: 1e3e26a262c112c05fe22cda2dbe3f14efb61f87
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387707"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Désactivation de la synchronisation d’annuaires pour Microsoft 365
Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires. Toutefois, il n’est pas recommandé de désactiver la synchronisation d’annuaires en tant qu’étape de résolution des problèmes. Si vous avez besoin d’aide pour résoudre les problèmes liés à la synchronisation d’annuaires, consultez l’article [résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) . 
  
[Contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits professionnels si nécessaire.
  
## <a name="turn-off-directory-synchronization"></a>Désactiver la synchronisation d’annuaires  
Pour désactiver la synchronisation d’annuaires :
  
1. Tout d’abord, installez les logiciels requis et connectez-vous à votre abonnement Microsoft 365. Pour obtenir des instructions, consultez [la rubrique se connecter avec le module Microsoft Azure Active Directory pour Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Utilisez [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) pour désactiver la synchronisation d’annuaires : 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Si vous utilisez cette commande, vous devez attendre 72 heures avant de réactiver la synchronisation d’annuaires.
>
 
