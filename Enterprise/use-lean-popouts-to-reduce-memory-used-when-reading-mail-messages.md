---
title: Permet de réduire la mémoire utilisée lors de la lecture des messages vocaux popouts maigre
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Cet article contient des informations pour améliorer les performances de téléchargement de message dans Outlook sur le web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540401"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="2c2b3-103">Permet de réduire la mémoire utilisée lors de la lecture des messages vocaux popouts maigre</span><span class="sxs-lookup"><span data-stu-id="2c2b3-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="2c2b3-p101">Cet article contient des informations pour améliorer les performances de téléchargement de message dans Outlook sur le web. Cet article fait partie du projet [de planification du réseau et de réglage des performances pour Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="2c2b3-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="2c2b3-p102">Un administrateur global d’Office 365, vous pouvez configurer Outlook sur le web afin d’offrir *popouts maigre* , un plus petit, moins la version gourmandes en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer. Maigre popouts sont configurés pour Outlook sur le web, composants de rendu côté serveur sont chargés qui optimisent les performances.</span><span class="sxs-lookup"><span data-stu-id="2c2b3-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2c2b3-108">À compter de mars 2018, popouts maigre n’est actuellement pas disponibles pour les messages qui spécifient les restrictions de droits d’utilisation, telles que Information Rights Management (IRM).</span><span class="sxs-lookup"><span data-stu-id="2c2b3-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="2c2b3-109">Ces fonctionnalités continueront de fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans maigre popouts :</span><span class="sxs-lookup"><span data-stu-id="2c2b3-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="2c2b3-110">Compléments Outlook</span><span class="sxs-lookup"><span data-stu-id="2c2b3-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="2c2b3-111">Skype pour présence commerciale</span><span class="sxs-lookup"><span data-stu-id="2c2b3-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="2c2b3-112">**Pour configurer maigre popouts pour tous les utilisateurs au sein de votre organisation Office 365**</span><span class="sxs-lookup"><span data-stu-id="2c2b3-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="2c2b3-113">[Se connecter à Exchange Online à l’aide de PowerShell à distance](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="2c2b3-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="2c2b3-114">Exécutez l’applet de commande [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) avec le paramètre LeanPopoutEnabled comme suit :</span><span class="sxs-lookup"><span data-stu-id="2c2b3-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="2c2b3-115">Par exemple, pour activer maigre popouts pour tous les utilisateurs de votre organisation :</span><span class="sxs-lookup"><span data-stu-id="2c2b3-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="2c2b3-116">Pour désactiver maigre popouts pour tous les utilisateurs de votre organisation :</span><span class="sxs-lookup"><span data-stu-id="2c2b3-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


