---
title: Télécharger et exécuter l’outil IdFix Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
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
description: Télécharger et exécuter l’outil IdFix Microsoft 365 pour vous aider à nettoyer vos services de domaine Active Directory (AD DS) avant de le synchroniser avec Microsoft 365.
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502659"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="97e6e-103">Télécharger et exécuter l’outil IdFix Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="97e6e-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="97e6e-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="97e6e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="97e6e-105">IdFix identifie les erreurs telles que les problèmes de doublons et de mise en forme dans votre domaine des services de domaine Active Directory (AD DS) avant la synchronisation avec Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="97e6e-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="97e6e-106">Pour pouvoir exécuter cette tâche, vous devez savoir utiliser des objets utilisateur, groupe et contact dans AD DS.</span><span class="sxs-lookup"><span data-stu-id="97e6e-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="97e6e-107">Si vous ne parvenez pas à réaliser cette tâche, vous pouvez suivre d’autres procédures.</span><span class="sxs-lookup"><span data-stu-id="97e6e-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="97e6e-108">Ces méthodes sont peut-être plus faciles, mais elles peuvent aussi prendre plus de temps ou présenter d’autres inconvénients.</span><span class="sxs-lookup"><span data-stu-id="97e6e-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="97e6e-109">Ce sont :</span><span class="sxs-lookup"><span data-stu-id="97e6e-109">They are:</span></span>
  
- <span data-ttu-id="97e6e-110">**Exécuter la synchronisation d'annuaires sans exécuter IdFix**</span><span class="sxs-lookup"><span data-stu-id="97e6e-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="97e6e-111">Vous pouvez synchroniser votre annuaire sans utiliser l’outil IdFix, mais nous ne le recommandons pas.</span><span class="sxs-lookup"><span data-stu-id="97e6e-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="97e6e-112">Corriger les erreurs avant la synchronisation prend moins de temps et fournit souvent une transition plus facile vers le cloud.</span><span class="sxs-lookup"><span data-stu-id="97e6e-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="97e6e-113">**Faire appel à un consultant**</span><span class="sxs-lookup"><span data-stu-id="97e6e-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="97e6e-114">Obtenir de l’aide d’un expert peut permettre à vos utilisateurs d’être rapidement opérationnels et de synchroniser votre annuaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="97e6e-115">Ce dont vous avez besoin pour exécuter IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-115">What you need to run IdFix</span></span>

<span data-ttu-id="97e6e-116">La façon la plus simple d’utiliser IdFix est de le télécharger sur un ordinateur joint à votre domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="97e6e-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="97e6e-117">Vous pouvez l'exécuter sur le contrôleur de domaine mais ce n'est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="97e6e-118">Configuration matérielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-118">IdFix hardware requirements</span></span>

<span data-ttu-id="97e6e-119">L’ordinateur sur lequel vous téléchargez IdFix doit respecter la configuration matérielle minimale requise suivante :</span><span class="sxs-lookup"><span data-stu-id="97e6e-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="97e6e-120">4 Go de RAM</span><span class="sxs-lookup"><span data-stu-id="97e6e-120">4 GB RAM</span></span>
- <span data-ttu-id="97e6e-121">2 Go d’espace disque dur</span><span class="sxs-lookup"><span data-stu-id="97e6e-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="97e6e-122">Configuration logicielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-122">IdFix software requirements</span></span>

<span data-ttu-id="97e6e-123">L’ordinateur sur lequel vous téléchargez IdFix doit être joint au même domaine AD DS que celui à partir duquel vous voulez synchroniser les utilisateurs avec Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="97e6e-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="97e6e-124">.NET Framework 4.0 doit également être installé sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="97e6e-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="97e6e-125">Si vous exécutez Windows Server 2008 ou version ultérieure, le .NET Framework est probablement déjà installé.</span><span class="sxs-lookup"><span data-stu-id="97e6e-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="97e6e-126">Sinon, vous pouvez [télécharger .NET 4.0 à partir du Centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou avec Windows Update.</span><span class="sxs-lookup"><span data-stu-id="97e6e-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="97e6e-127">Conditions requises d'autorisations IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-127">IdFix permissions requirements</span></span>

<span data-ttu-id="97e6e-128">Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture et en écriture au domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="97e6e-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="97e6e-129">Si vous n'êtes pas sûr que votre compte d'utilisateur répond à ces exigences, et si vous n'êtes pas sûr de la façon de le vérifier, vous pouvez télécharger et exécuter IdFix.</span><span class="sxs-lookup"><span data-stu-id="97e6e-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="97e6e-130">Si votre compte d'utilisateur ne dispose pas des autorisations appropriées, IdFix affichera simplement une erreur lorsque vous essaierez de l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="97e6e-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="97e6e-131">Télécharger et extraire IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-131">Download and extract IdFix</span></span>

<span data-ttu-id="97e6e-132">Suivez ces instructions.</span><span class="sxs-lookup"><span data-stu-id="97e6e-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="97e6e-133">Connectez-vous à l’ordinateur sur lequel vous voulez exécuter l’outil IdFix.</span><span class="sxs-lookup"><span data-stu-id="97e6e-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="97e6e-134">Accédez au [Outil de reconversion d’erreur IdFix DirSync](https://github.com/microsoft/idfix) site.</span><span class="sxs-lookup"><span data-stu-id="97e6e-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="97e6e-135">Cliquez sur **lancer** dans la section **lancement de ClickOnce** pour télécharger le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="97e6e-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="97e6e-136">Ouvrez le fichier zip.</span><span class="sxs-lookup"><span data-stu-id="97e6e-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="97e6e-137">Dans la fenêtre **IdFix**, sélectionnez **Extraire**, puis **Extraire toutes les**.</span><span class="sxs-lookup"><span data-stu-id="97e6e-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="97e6e-138">Par défaut, IdFix est extrait pour `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="97e6e-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="97e6e-139">Sélectionnez **extraire**.</span><span class="sxs-lookup"><span data-stu-id="97e6e-139">Choose **Extract**.</span></span>

<span data-ttu-id="97e6e-140">Votre procédure peut varier en fonction de votre version de Windows et de votre navigateur Internet.</span><span class="sxs-lookup"><span data-stu-id="97e6e-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="97e6e-141">Exécution de l'outil IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-141">Run the IdFix tool</span></span>

<span data-ttu-id="97e6e-142">Une fois que vous avez téléchargé et extrait IdFix, exécutez-le pour rechercher les problèmes dans votre domaine AD DS.</span><span class="sxs-lookup"><span data-stu-id="97e6e-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="97e6e-143">À l’aide d’un compte qui dispose d’un accès en lecture/écriture à votre domaine AD DS, connectez-vous à l’ordinateur sur lequel vous avez téléchargé IdFix.</span><span class="sxs-lookup"><span data-stu-id="97e6e-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="97e6e-144">Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez extrait IdFix.</span><span class="sxs-lookup"><span data-stu-id="97e6e-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="97e6e-145">Si vous avez choisi le dossier par défaut lors de l’extraction, accédez à `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="97e6e-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="97e6e-146">Double-cliquez sur **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="97e6e-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="97e6e-147">Par défaut, IdFix utilise le jeu de règles multiclients pour tester les entrées dans votre annuaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="97e6e-148">Il s’agit de l’entité de règle appropriée pour la plupart des clients Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="97e6e-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="97e6e-149">Toutefois, si vous êtes un client Microsoft 365 dédié ou international en matière de réglementations sur les armements (ITAR)), vous pouvez configurer IdFix pour utiliser le groupe de règles dédié à la place.</span><span class="sxs-lookup"><span data-stu-id="97e6e-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="97e6e-150">Si vous n'êtes pas sûr de votre type de client, vous pouvez ignorer cette étape en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="97e6e-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="97e6e-151">Pour définir le jeu de règles sur Dédié, cliquez sur l’icône en forme d’engrenage dans la barre de menu, puis cliquez sur **Dédié**.</span><span class="sxs-lookup"><span data-stu-id="97e6e-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="97e6e-152">Cliquez sur **Requête**.</span><span class="sxs-lookup"><span data-stu-id="97e6e-152">Choose **Query**.</span></span>
    
    ![Choisissez la requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="97e6e-154">Par défaut, IdFix recherche des erreurs dans l'intégralité de l'annuaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="97e6e-155">En fonction de la taille de votre annuaire, l'exécution de la requête peut prendre du temps.</span><span class="sxs-lookup"><span data-stu-id="97e6e-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="97e6e-156">Vous pouvez surveiller la progression au bas de la fenêtre principale de l'outil.</span><span class="sxs-lookup"><span data-stu-id="97e6e-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="97e6e-157">Si vous cliquez sur **Annuler**, vous devez reprendre l'opération au début.</span><span class="sxs-lookup"><span data-stu-id="97e6e-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="97e6e-158">Une fois que IdFix a terminé la requête, vous pouvez synchroniser votre annuaire s’il n’y a pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="97e6e-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="97e6e-159">S'il y a des erreurs dans votre annuaire, nous vous recommandons de les corriger avant de procéder à la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="97e6e-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="97e6e-160">Pour plus d’informations, voir [préparer les attributs d’annuaire pour la synchronisation avec ](prepare-directory-attributes-for-synch-with-idfix.md) Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="97e6e-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="97e6e-161">Même s'il n'est pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons fortement de consulter au moins toutes les erreurs renvoyées par IdFix.</span><span class="sxs-lookup"><span data-stu-id="97e6e-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="97e6e-162">Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil.</span><span class="sxs-lookup"><span data-stu-id="97e6e-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="97e6e-163">Si vous êtes d’accord avec la modification recommandée dans la colonne **UPDATE**, sélectionnez l’action qu’IdFix doit effectuer dans la colonne **ACTION** pour appliquer le changement, puis cliquez sur **Appliquer**. </span><span class="sxs-lookup"><span data-stu-id="97e6e-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="97e6e-164">Lorsque vous cliquez sur **Apply**, l’outil apporte les modifications dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="97e6e-165">Vous n'êtes pas obligé de cliquer sur **Appliquer** après chaque mise à jour.</span><span class="sxs-lookup"><span data-stu-id="97e6e-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="97e6e-166">Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **Appliquer** et IdFix les modifie toutes simultanément.</span><span class="sxs-lookup"><span data-stu-id="97e6e-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="97e6e-167">Vous pouvez les trier par type en cliquant sur **ERROR** (erreur) en haut de la colonne répertoriant les types d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="97e6e-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="97e6e-168">Vous pouvez aussi corriger toutes les erreurs du même type ; par exemple, corrigez d'abord tous les doublons, puis appliquez les corrections.</span><span class="sxs-lookup"><span data-stu-id="97e6e-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="97e6e-169">Corrigez ensuite les erreurs de format de caractère, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="97e6e-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="97e6e-170">Chaque fois que vous appliquez les modifications, l'outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="97e6e-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="97e6e-171">Le [journal des transactions](idfix-transaction-log.md) est stocké dans le dossier dans lequel vous avez extrait IdFix, _C:\Users\<your user name>\Documents\IdFix_ par défaut.</span><span class="sxs-lookup"><span data-stu-id="97e6e-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Correction d’erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="97e6e-173">Une fois que toutes vos modifications sont apportées à l'annuaire, exécutez IdFix à nouveau pour vous assurer que les corrections que vous avez effectuées n'ont pas introduit de nouvelles erreurs.</span><span class="sxs-lookup"><span data-stu-id="97e6e-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="97e6e-174">Vous pouvez répéter ces étapes autant de fois que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="97e6e-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="97e6e-175">Il est conseillé de répéter cette procédure plusieurs fois avant la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="97e6e-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="97e6e-176">Ressources supplémentaires sur IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="97e6e-177">Attributs et objets d’IdFix pris en charge et exclus</span><span class="sxs-lookup"><span data-stu-id="97e6e-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="97e6e-178">Microsoft 365 journal des transactions IdFix</span><span class="sxs-lookup"><span data-stu-id="97e6e-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
