---
title: Désactiver la synchronisation d’annuaires pour Office 365
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Découvrez comment utiliser PowerShell pour désactiver la synchronisation d’annuaires pour Office 365
ms.openlocfilehash: 83a01d827217db141016f622a2cb417f93f88e76
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070360"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="237bb-103">Désactiver la synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="237bb-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="237bb-104">Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="237bb-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="237bb-105">Toutefois, il n’est pas recommandé de désactiver la synchronisation d’annuaires en tant qu’étape de résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="237bb-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="237bb-106">Si vous avez besoin d’aide pour résoudre les problèmes liés à la synchronisation d’annuaires, consultez l’article [résolution des problèmes liés à la synchronisation d’annuaires pour Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="237bb-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="237bb-107">[Contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits professionnels si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="237bb-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="237bb-108">Désactiver la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="237bb-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="237bb-109">Pour désactiver la synchronisation d’annuaires:</span><span class="sxs-lookup"><span data-stu-id="237bb-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="237bb-110">Tout d’abord, installez les logiciels requis et connectez-vous à votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="237bb-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="237bb-111">Pour obtenir des instructions pour les deux, consultez la rubrique [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="237bb-111">For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="237bb-112">Utilisez [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) pour désactiver la synchronisation d’annuaires:</span><span class="sxs-lookup"><span data-stu-id="237bb-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```