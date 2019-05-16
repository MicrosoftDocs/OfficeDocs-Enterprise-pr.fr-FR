---
title: Utiliser le la messagerie instantanée épuré pour réduire la mémoire utilisée lors de la lecture des messages électroniques
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Cet article contient des informations sur l’amélioration des performances de téléchargement de messages dans Outlook sur le Web.
ms.openlocfilehash: 344047363bd58850fcd08a7f8f2fd46de757668c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070560"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="ef82b-103">Utiliser le la messagerie instantanée épuré pour réduire la mémoire utilisée lors de la lecture des messages électroniques</span><span class="sxs-lookup"><span data-stu-id="ef82b-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="ef82b-104">Cet article contient des informations sur l’amélioration des performances de téléchargement de messages dans Outlook sur le Web.</span><span class="sxs-lookup"><span data-stu-id="ef82b-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="ef82b-105">Cet article fait partie du projet [planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="ef82b-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="ef82b-106">En tant qu’administrateur général Office 365, vous pouvez configurer Outlook sur le Web pour la remise de *la messagerie instantanée* , une version plus petite et moins gourmande en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ef82b-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="ef82b-107">Lorsque les la messagerie instantanée de Lean sont configurés pour Outlook sur le Web, les composants rendus côté serveur sont chargés et optimisent les performances.</span><span class="sxs-lookup"><span data-stu-id="ef82b-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ef82b-108">Depuis le 2018 mars, le la messagerie instantanée épuré n’est actuellement pas disponible pour les messages qui spécifient des restrictions relatives aux droits d’utilisation, tels que la gestion des droits relatifs à l’information (IRM).</span><span class="sxs-lookup"><span data-stu-id="ef82b-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="ef82b-109">Ces fonctionnalités continueront à fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans le la messagerie instantanée épuré:</span><span class="sxs-lookup"><span data-stu-id="ef82b-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="ef82b-110">Compléments Outlook</span><span class="sxs-lookup"><span data-stu-id="ef82b-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="ef82b-111">Présence de Skype entreprise</span><span class="sxs-lookup"><span data-stu-id="ef82b-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="ef82b-112">**Pour configurer le Lean la messagerie instantanée pour tous les utilisateurs au sein de votre organisation Office 365**</span><span class="sxs-lookup"><span data-stu-id="ef82b-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="ef82b-113">[Connectez-vous à Exchange Online à l’aide de Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="ef82b-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="ef82b-114">Exécutez la cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) avec le paramètre LeanPopoutEnabled comme suit:</span><span class="sxs-lookup"><span data-stu-id="ef82b-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="ef82b-115">Par exemple, pour activer le la messagerie instantanée épuré pour tous les utilisateurs de votre organisation:</span><span class="sxs-lookup"><span data-stu-id="ef82b-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="ef82b-116">Pour désactiver la la messagerie instantanée épurée pour tous les utilisateurs de votre organisation:</span><span class="sxs-lookup"><span data-stu-id="ef82b-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


