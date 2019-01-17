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
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="53eaa-103">Afficher les erreurs de synchronisation d’annuaire dans Office 365</span><span class="sxs-lookup"><span data-stu-id="53eaa-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="53eaa-p101">Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le centre d’administration d’Office 365. Uniquement les erreurs d’objet utilisateur sont affichés. Pour afficher les erreurs à l’aide de PowerShell, voir [objets identifier avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="53eaa-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="53eaa-107">Après l’affichage, voir [résolution des problèmes de synchronisation d’annuaires pour Office 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="53eaa-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="53eaa-108">Afficher les erreurs de synchronisation d’annuaires dans le centre d’administration</span><span class="sxs-lookup"><span data-stu-id="53eaa-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="53eaa-109">Pour afficher les erreurs dans le centre d’administration :</span><span class="sxs-lookup"><span data-stu-id="53eaa-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="53eaa-110">Connectez-vous à Office 365 à l'aide de votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="53eaa-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="53eaa-111">Accédez au [Centre d’administration sur Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="53eaa-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="53eaa-112">Dans la page **d’accueil** , vous verrez la vignette de **l’État de synchronisation d’annuaire** .</span><span class="sxs-lookup"><span data-stu-id="53eaa-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![L’état de synchronisation d’annuaire en mosaïque dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="53eaa-114">Dans la fenêtre, choisissez l' **État de synchronisation d’annuaire** pour accéder à la page **État de synchronisation d’annuaire** .</span><span class="sxs-lookup"><span data-stu-id="53eaa-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="53eaa-115">Au bas de la page, vous pouvez voir s’il existe des erreurs de synchronisation d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="53eaa-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Dans la page État de synchronisation d’annuaire, vous pouvez voir s’il existe des erreurs de synchronisation d’annuaire d’objet](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="53eaa-117">Choisissez que **nous avons trouvé des erreurs de synchronisation d’annuaire d’objet** pour accéder à une vue détaillée des erreurs de synchronisation de répertoire.</span><span class="sxs-lookup"><span data-stu-id="53eaa-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="53eaa-118">Vous pouvez également accéder à la page **d’erreurs de synchronisation d’annuaire** si vous choisissez **nous avons trouvé des erreurs de synchronisation d’annuaire d’objet** sur la vignette de **l’état de synchronisation d’annuaire** .</span><span class="sxs-lookup"><span data-stu-id="53eaa-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Page d’erreurs de synchronisation d’annuaire](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="53eaa-120">Dans la page **d’erreurs de synchronisation d’annuaire** , choisissez une des erreurs répertoriées pour afficher le volet de détails avec des informations sur l’erreur et des conseils sur la façon de résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="53eaa-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
