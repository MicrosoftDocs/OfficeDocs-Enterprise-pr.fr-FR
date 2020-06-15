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
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="eebd9-103">Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="eebd9-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="eebd9-104">Vous pouvez afficher les erreurs de synchronisation d’annuaires dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="eebd9-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="eebd9-105">Seules les erreurs d’objet utilisateur sont affichées.</span><span class="sxs-lookup"><span data-stu-id="eebd9-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="eebd9-106">Pour afficher les erreurs à l’aide de PowerShell, consultez la rubrique [identifier les objets avec DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="eebd9-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="eebd9-107">Après l’affichage, consultez la rubrique [résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) pour corriger les problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="eebd9-107">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="eebd9-108">Afficher les erreurs de synchronisation d’annuaires dans le centre d’administration</span><span class="sxs-lookup"><span data-stu-id="eebd9-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="eebd9-109">Pour afficher les erreurs dans le centre d’administration :</span><span class="sxs-lookup"><span data-stu-id="eebd9-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="eebd9-110">Connectez-vous à Microsoft 365 à l’aide de votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="eebd9-110">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="eebd9-111">Accédez à la rubrique [à propos du centre d’administration](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="eebd9-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="eebd9-112">Sur la page d' **Accueil** , vous verrez la vignette d' **État DirSync** .</span><span class="sxs-lookup"><span data-stu-id="eebd9-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Vignette d’État DirSync dans l’aperçu du centre d’administration](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="eebd9-114">Sur la vignette, choisissez **État DirSync** pour accéder à la page État de la **synchronisation d’annuaires** .</span><span class="sxs-lookup"><span data-stu-id="eebd9-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="eebd9-115">Au bas de la page, vous pouvez voir s’il existe des erreurs DirSync.</span><span class="sxs-lookup"><span data-stu-id="eebd9-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Sur la page État de la synchronisation d’annuaires, vous pouvez voir s’il existe des erreurs d’objet DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="eebd9-117">Choisissez des **Erreurs d’objets DirSync trouvés** pour accéder à une vue détaillée des erreurs de synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="eebd9-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="eebd9-118">Vous pouvez également accéder à la page des **Erreurs** DirSync si vous choisissez des **Erreurs d’objet DirSync** sur la vignette d' **État DirSync** .</span><span class="sxs-lookup"><span data-stu-id="eebd9-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Page des erreurs DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="eebd9-120">Sur la page **Erreurs de synchronisation d’annuaire** , choisissez l’une des erreurs indiquées pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la résolution de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="eebd9-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
