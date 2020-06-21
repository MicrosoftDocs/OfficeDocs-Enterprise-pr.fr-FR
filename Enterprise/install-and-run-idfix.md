---
title: Télécharger et exécuter l’outil IdFix de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Comment télécharger et exécuter l’outil IdFix de Microsoft 365 pour nettoyer vos services de domaine Active Directory (AD DS) avant de le synchroniser avec Microsoft 365.
ms.openlocfilehash: c4df63e6162b1d53cb7a45f046542443177b25ff
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774859"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="8eba5-103">Télécharger et exécuter l’outil IdFix de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8eba5-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="8eba5-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="8eba5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="8eba5-105">IdFix identifie les erreurs telles que les doublons et les problèmes de mise en forme dans votre domaine des services de domaine Active Directory (AD DS) avant la synchronisation avec Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8eba5-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="8eba5-106">Pour terminer cette tâche, vous devez être familiarisé avec les objets utilisateur, groupe et contact dans AD DS.</span><span class="sxs-lookup"><span data-stu-id="8eba5-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="8eba5-107">Si vous ne pouvez pas effectuer cette tâche, il existe deux autres opérations que vous pouvez effectuer.</span><span class="sxs-lookup"><span data-stu-id="8eba5-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="8eba5-108">Ces méthodes peuvent être plus faciles, mais elles peuvent également prendre plus de temps ou avoir d’autres inconvénients.</span><span class="sxs-lookup"><span data-stu-id="8eba5-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="8eba5-109">Ce sont :</span><span class="sxs-lookup"><span data-stu-id="8eba5-109">They are:</span></span>
  
- <span data-ttu-id="8eba5-110">**Exécuter la synchronisation d’annuaires sans exécuter IdFix**</span><span class="sxs-lookup"><span data-stu-id="8eba5-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="8eba5-111">Vous pouvez synchroniser votre annuaire sans utiliser l’outil IdFix, mais il n’est pas recommandé de le faire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="8eba5-112">La correction des erreurs avant la synchronisation nécessite moins de temps et permet souvent d’effectuer une transition plus fluide vers le nuage.</span><span class="sxs-lookup"><span data-stu-id="8eba5-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="8eba5-113">**Embaucher un consultant**</span><span class="sxs-lookup"><span data-stu-id="8eba5-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="8eba5-114">L’obtention d’une aide expert peut permettre à vos utilisateurs de fonctionner rapidement et de synchroniser votre annuaire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="8eba5-115">Ce dont vous avez besoin pour exécuter IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-115">What you need to run IdFix</span></span>

<span data-ttu-id="8eba5-116">Le moyen le plus simple d’obtenir et d’exécuter IdFix est de le télécharger sur un ordinateur qui est joint à votre domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="8eba5-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="8eba5-117">Vous pouvez l’exécuter sur le contrôleur de domaine si vous le souhaitez, mais cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="8eba5-118">Configuration matérielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-118">IdFix hardware requirements</span></span>

<span data-ttu-id="8eba5-119">L’ordinateur sur lequel vous téléchargez IdFix doit satisfaire à la configuration matérielle minimale requise suivante :</span><span class="sxs-lookup"><span data-stu-id="8eba5-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="8eba5-120">4 Go de RAM</span><span class="sxs-lookup"><span data-stu-id="8eba5-120">4 GB RAM</span></span>
- <span data-ttu-id="8eba5-121">2 Go d’espace disque</span><span class="sxs-lookup"><span data-stu-id="8eba5-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="8eba5-122">Configuration logicielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-122">IdFix software requirements</span></span>

<span data-ttu-id="8eba5-123">L’ordinateur sur lequel vous téléchargez IdFix doit être joint au même domaine AD DS que celui à partir duquel vous voulez synchroniser les utilisateurs avec Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8eba5-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="8eba5-124">.NET Framework 4,0 doit également être installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8eba5-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="8eba5-125">Si vous exécutez Windows Server 2008 ou une version ultérieure, .NET Framework est probablement déjà installé.</span><span class="sxs-lookup"><span data-stu-id="8eba5-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="8eba5-126">Si ce n’est pas le cas, vous pouvez [Télécharger .net 4,0 à partir du centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou de Windows Update.</span><span class="sxs-lookup"><span data-stu-id="8eba5-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="8eba5-127">Exigences en matière d’autorisations IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-127">IdFix permissions requirements</span></span>

<span data-ttu-id="8eba5-128">Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture et en écriture au domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="8eba5-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="8eba5-129">Si vous n’êtes pas certain que votre compte d’utilisateur répond à ces exigences et que vous n’êtes pas sûr de savoir comment procéder, vous pouvez toujours télécharger et exécuter IdFix.</span><span class="sxs-lookup"><span data-stu-id="8eba5-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="8eba5-130">Si votre compte d’utilisateur ne dispose pas des autorisations appropriées, IdFix affiche simplement une erreur lorsque vous tentez de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="8eba5-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="8eba5-131">Télécharger et extraire IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-131">Download and extract IdFix</span></span>

<span data-ttu-id="8eba5-132">Suivez ces instructions.</span><span class="sxs-lookup"><span data-stu-id="8eba5-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="8eba5-133">Connectez-vous à l’ordinateur sur lequel vous souhaitez exécuter l’outil IdFix.</span><span class="sxs-lookup"><span data-stu-id="8eba5-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="8eba5-134">Accédez au site [outil de correction d’erreurs DirSync IdFix](https://github.com/microsoft/idfix) .</span><span class="sxs-lookup"><span data-stu-id="8eba5-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="8eba5-135">Cliquez sur **lancer** dans la section de **lancement ClickOnce** pour télécharger le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="8eba5-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="8eba5-136">Ouvrez le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="8eba5-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="8eba5-137">Dans la fenêtre **IdFix** , sélectionnez **extraire**, puis **extraire tout**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="8eba5-138">Par défaut, IdFix est extrait `C:\Users\<your user name>\Documents\IdFix` .</span><span class="sxs-lookup"><span data-stu-id="8eba5-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="8eba5-139">Sélectionnez **extraire**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-139">Choose **Extract**.</span></span>

<span data-ttu-id="8eba5-140">Vos étapes peuvent varier en fonction de votre version de Windows et de votre navigateur Internet.</span><span class="sxs-lookup"><span data-stu-id="8eba5-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="8eba5-141">Exécuter l’outil IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-141">Run the IdFix tool</span></span>

<span data-ttu-id="8eba5-142">Une fois que vous avez téléchargé et extrait IdFix, exécutez-le pour rechercher des problèmes dans votre domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="8eba5-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="8eba5-143">À l’aide d’un compte disposant d’un accès en lecture/écriture à votre domaine AD DS, connectez-vous à l’ordinateur sur lequel vous avez téléchargé IdFix.</span><span class="sxs-lookup"><span data-stu-id="8eba5-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="8eba5-144">Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez extrait IdFix.</span><span class="sxs-lookup"><span data-stu-id="8eba5-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="8eba5-145">Si vous avez choisi le dossier par défaut pendant l’extraction, accédez à `C:\Users\<your user name>\Documents\IdFix` .</span><span class="sxs-lookup"><span data-stu-id="8eba5-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="8eba5-146">Double-cliquez sur **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="8eba5-147">Par défaut, IdFix utilise l’ensemble de règles mutualisée pour tester les entrées de votre répertoire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="8eba5-148">Il s’agit de l’ensemble de règles approprié pour la plupart des clients Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8eba5-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="8eba5-149">Toutefois, si vous êtes un client Microsoft 365 dédié ou international dans le cadre des réglementations relatives aux armes (ITAR)), vous pouvez configurer IdFix pour qu’il utilise plutôt le jeu de règles dédié.</span><span class="sxs-lookup"><span data-stu-id="8eba5-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="8eba5-150">Si vous n’êtes pas sûr de votre type de client, vous pouvez en toute sécurité ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="8eba5-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="8eba5-151">Pour définir le jeu de règles sur dédié, cliquez sur l’icône d’engrenage dans la barre de menus, puis choisissez **dédié**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="8eba5-152">Sélectionnez **requête**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-152">Choose **Query**.</span></span>
    
    ![Sélectionnez requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="8eba5-154">Par défaut, IdFix recherche les erreurs dans le répertoire entier.</span><span class="sxs-lookup"><span data-stu-id="8eba5-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="8eba5-155">En fonction de la taille de votre répertoire, l’exécution de la requête peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="8eba5-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="8eba5-156">Vous pouvez suivre la progression au bas de la fenêtre principale de l’outil.</span><span class="sxs-lookup"><span data-stu-id="8eba5-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="8eba5-157">Si vous cliquez sur **Annuler**, vous devrez redémarrer depuis le début.</span><span class="sxs-lookup"><span data-stu-id="8eba5-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="8eba5-158">Une fois que IdFix a terminé la requête, vous pouvez synchroniser votre répertoire s’il n’y a pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="8eba5-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="8eba5-159">S’il existe des erreurs dans votre répertoire, il est recommandé de les résoudre avant de procéder à la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="8eba5-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="8eba5-160">Pour plus d’informations, consultez la rubrique [Prepare Directory attributes for Synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="8eba5-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="8eba5-161">Bien qu’il ne soit pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons vivement de consulter au moins toutes les erreurs renvoyées par IdFix.</span><span class="sxs-lookup"><span data-stu-id="8eba5-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="8eba5-162">Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil.</span><span class="sxs-lookup"><span data-stu-id="8eba5-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="8eba5-163">Si vous acceptez le changement suggéré dans la colonne **mettre à jour** , dans la colonne **action** , sélectionnez les actions que doit effectuer IdFix pour implémenter la modification, puis cliquez sur **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="8eba5-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="8eba5-164">Lorsque vous cliquez sur **appliquer**, l’outil effectue les modifications dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="8eba5-165">Il n’est pas nécessaire de cliquer sur **appliquer** après chaque mise à jour.</span><span class="sxs-lookup"><span data-stu-id="8eba5-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="8eba5-166">Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **appliquer** et IdFix les modifiera en même temps.</span><span class="sxs-lookup"><span data-stu-id="8eba5-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="8eba5-167">Vous pouvez trier les erreurs par type d’erreur en cliquant sur **erreur** en haut de la colonne qui répertorie les types d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8eba5-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="8eba5-168">Une stratégie consiste à corriger toutes les erreurs du même type ; par exemple, corrigez tous les doublons en premier, puis appliquez-les.</span><span class="sxs-lookup"><span data-stu-id="8eba5-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="8eba5-169">Ensuite, corrigez les erreurs de format de caractère, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8eba5-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="8eba5-170">Chaque fois que vous appliquez les modifications, l’outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8eba5-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="8eba5-171">Le [Journal des transactions](idfix-transaction-log.md) est stocké dans le dossier où vous avez extrait IdFix, ce qui est _C:\Users \<your user name> \Documents\IdFix_ par défaut.</span><span class="sxs-lookup"><span data-stu-id="8eba5-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Correction des erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="8eba5-173">Une fois que toutes les modifications ont été apportées au répertoire, exécutez à nouveau IdFix pour vous assurer que les corrections que vous avez apportées n’ont pas introduit de nouvelles erreurs.</span><span class="sxs-lookup"><span data-stu-id="8eba5-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="8eba5-174">Vous pouvez répéter ces étapes autant de fois que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8eba5-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="8eba5-175">Il est recommandé de suivre le processus quelques fois avant de procéder à la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="8eba5-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="8eba5-176">Ressources supplémentaires sur IdFix</span><span class="sxs-lookup"><span data-stu-id="8eba5-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="8eba5-177">Attributs et objets d’IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="8eba5-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="8eba5-178">Microsoft 365 IdFix journal des transactions</span><span class="sxs-lookup"><span data-stu-id="8eba5-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
