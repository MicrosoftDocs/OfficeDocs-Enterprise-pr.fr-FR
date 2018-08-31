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
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Découvrez comment utiliser PowerShell pour désactiver la synchronisation d’annuaires pour Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540559"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="35132-103">Désactiver la synchronisation d’annuaires pour Office 365</span><span class="sxs-lookup"><span data-stu-id="35132-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="35132-p101">Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires. Toutefois, il est déconseillé de désactiver la synchronisation d’annuaires comme étape de dépannage. Si vous avez besoin d’aide Résolution des problèmes de synchronisation d’annuaires, consultez l’article de la [correction des problèmes avec la synchronisation d’annuaires pour Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="35132-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="35132-107">[Contacter le support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits d’entreprise si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="35132-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="35132-108">Désactiver la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="35132-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="35132-109">Pour désactiver la synchronisation d’annuaires :</span><span class="sxs-lookup"><span data-stu-id="35132-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="35132-p102">Tout d’abord, installez les logiciels requis et se connecter à votre abonnement Office 365. Pour obtenir des instructions pour les deux, voir [se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="35132-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="35132-112">[Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) permet de désactiver la synchronisation d’annuaires :</span><span class="sxs-lookup"><span data-stu-id="35132-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```