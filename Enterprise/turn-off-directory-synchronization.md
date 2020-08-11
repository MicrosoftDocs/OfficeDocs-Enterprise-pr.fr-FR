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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Dans cet article, vous trouverez des informations sur l’utilisation de PowerShell pour désactiver la synchronisation d’annuaires pour Microsoft 365.
ms.openlocfilehash: 815d20ff6a0697f1533e44305e20e61a9282312b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603646"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="c9943-103">Désactivation de la synchronisation d’annuaires pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c9943-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="c9943-104">Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="c9943-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="c9943-105">Toutefois, il n’est pas recommandé de désactiver la synchronisation d’annuaires en tant qu’étape de résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="c9943-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="c9943-106">Si vous avez besoin d’aide pour résoudre les problèmes liés à la synchronisation d’annuaires, consultez l’article [résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="c9943-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="c9943-107">[Contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits professionnels si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c9943-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="c9943-108">Désactiver la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="c9943-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="c9943-109">Pour désactiver la synchronisation d’annuaires :</span><span class="sxs-lookup"><span data-stu-id="c9943-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="c9943-110">Tout d’abord, installez les logiciels requis et connectez-vous à votre abonnement Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c9943-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="c9943-111">Pour obtenir des instructions, consultez [la rubrique se connecter avec le module Microsoft Azure Active Directory pour Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9943-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="c9943-112">Utilisez [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) pour désactiver la synchronisation d’annuaires :</span><span class="sxs-lookup"><span data-stu-id="c9943-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
><span data-ttu-id="c9943-113">Si vous utilisez cette commande, vous devez attendre 72 heures avant de réactiver la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="c9943-113">If you use this command, you must wait 72 hours before you can turn directory synchronization back on.</span></span>
>
 
