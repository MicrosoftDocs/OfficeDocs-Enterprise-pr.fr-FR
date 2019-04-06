---
title: Afficher les erreurs de synchronisation d'annuaires dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d'annuaires dans le centre d'administration Microsoft 365.
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001807"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="a56fe-103">Afficher les erreurs de synchronisation d'annuaires dans Office 365</span><span class="sxs-lookup"><span data-stu-id="a56fe-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="a56fe-104">Vous pouvez afficher les erreurs de synchronisation d'annuaires dans le [Centre d'administration Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a56fe-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="a56fe-105">Seules les erreurs d'objet utilisateur sont affichées.</span><span class="sxs-lookup"><span data-stu-id="a56fe-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="a56fe-106">Pour afficher les erreurs à l'aide de PowerShell, consultez la rubrique [identifier les objets avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="a56fe-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="a56fe-107">Après l'affichage, consultez la rubrique [résolution des problèmes liés à la synchronisation d'annuaires pour Office 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="a56fe-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="a56fe-108">Afficher les erreurs de synchronisation d'annuaires dans le centre d'administration</span><span class="sxs-lookup"><span data-stu-id="a56fe-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="a56fe-109">Pour afficher les erreurs dans le centre d'administration:</span><span class="sxs-lookup"><span data-stu-id="a56fe-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="a56fe-110">Connectez-vous à Office 365 avec votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="a56fe-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="a56fe-111">Accédez à la rubrique [à propos du centre d'administration](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="a56fe-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="a56fe-112">Sur la page d' **Accueil** , vous verrez la vignette d' **État DirSync** .</span><span class="sxs-lookup"><span data-stu-id="a56fe-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Vignette d'État dirSync dans l'aperçu du centre d'administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="a56fe-114">Sur la vignette, choisissez **État DirSync** pour accéder à la page État de la **synchronisation** d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="a56fe-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="a56fe-115">Au bas de la page, vous pouvez voir s'il existe des erreurs dirSync.</span><span class="sxs-lookup"><span data-stu-id="a56fe-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Sur la page État de la synchronisation d'annuaires, vous pouvez voir s'il existe des erreurs d'objet dirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="a56fe-117">Choisissez des **Erreurs d'objets DirSync trouvés** pour accéder à une vue détaillée des erreurs de synchronisation d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="a56fe-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="a56fe-118">Vous pouvez également accéder à la page des **Erreurs** DirSync si vous choisissez des **Erreurs d'objet DirSync** sur la vignette d' **État DirSync** .</span><span class="sxs-lookup"><span data-stu-id="a56fe-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Page des erreurs dirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="a56fe-120">Sur la page **Erreurs de synchronisation d'annuaire** , choisissez l'une des erreurs indiquées pour afficher le volet d'informations avec des informations sur l'erreur et des conseils sur la résolution de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="a56fe-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
