---
title: Installer et exécuter l'outil IdFix pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Comment installer et exécuter l’outil IdFix Office 365 pour nettoyer votre Active Directory avant de le synchroniser avec Office 365.
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067290"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="917e2-103">Installer et exécuter l'outil IdFix pour Office 365</span><span class="sxs-lookup"><span data-stu-id="917e2-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="917e2-104">IdFix identifie les erreurs telles que les doublons et les problèmes de mise en forme dans votre répertoire avant la synchronisation avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="917e2-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="917e2-105">Pour terminer cette tâche, vous devez être familiarisé avec les objets utilisateur, groupe et contact dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="917e2-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="917e2-106">Si vous ne pouvez pas effectuer cette tâche, il existe deux autres opérations que vous pouvez effectuer.</span><span class="sxs-lookup"><span data-stu-id="917e2-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="917e2-107">Ces méthodes peuvent être plus faciles, mais elles peuvent également prendre plus de temps ou avoir d’autres inconvénients.</span><span class="sxs-lookup"><span data-stu-id="917e2-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="917e2-108">Ces limites sont :</span><span class="sxs-lookup"><span data-stu-id="917e2-108">They are:</span></span>
  
- <span data-ttu-id="917e2-109">**Exécutez la synchronisation d’annuaires sans exécuter IdFix.**</span><span class="sxs-lookup"><span data-stu-id="917e2-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="917e2-110">Vous pouvez synchroniser votre annuaire sans exécuter l’outil IdFix, mais il n’est pas recommandé de le faire.</span><span class="sxs-lookup"><span data-stu-id="917e2-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="917e2-111">La correction des erreurs avant la synchronisation nécessite moins de temps et permet souvent d’effectuer une transition plus fluide vers le nuage.</span><span class="sxs-lookup"><span data-stu-id="917e2-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="917e2-112">**Embaucher un consultant.**</span><span class="sxs-lookup"><span data-stu-id="917e2-112">**Hire a consultant.**</span></span> <span data-ttu-id="917e2-113">L’obtention d’une aide expert peut permettre à vos utilisateurs de fonctionner rapidement et de synchroniser votre annuaire.</span><span class="sxs-lookup"><span data-stu-id="917e2-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="917e2-114">Ce dont vous avez besoin pour exécuter IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-114">What you need to run IdFix</span></span>

<span data-ttu-id="917e2-115">Le moyen le plus simple d’obtenir IdFix et de l’exécuter est de l’installer sur un ordinateur qui est associé à votre domaine.</span><span class="sxs-lookup"><span data-stu-id="917e2-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="917e2-116">Vous pouvez l’exécuter sur le contrôleur de domaine si vous le souhaitez, mais cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="917e2-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="917e2-117">Configuration matérielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-117">IdFix hardware requirements</span></span>

<span data-ttu-id="917e2-118">L’ordinateur sur lequel vous installez IdFix doit répondre à la configuration matérielle minimale requise suivante:</span><span class="sxs-lookup"><span data-stu-id="917e2-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="917e2-119">4 Go de RAM</span><span class="sxs-lookup"><span data-stu-id="917e2-119">4 GB RAM</span></span>
- <span data-ttu-id="917e2-120">2 Go d’espace disque</span><span class="sxs-lookup"><span data-stu-id="917e2-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="917e2-121">Configuration logicielle requise pour IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-121">IdFix software requirements</span></span>

<span data-ttu-id="917e2-122">L’ordinateur sur lequel vous installez IdFix doit être joint au même domaine Active Directory que celui à partir duquel vous souhaitez synchroniser les utilisateurs avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="917e2-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="917e2-123">.NET Framework 4,0 doit également être installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="917e2-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="917e2-124">Si vous exécutez Windows Server 2008 ou Windows Server 2012, .NET Framework est probablement déjà installé.</span><span class="sxs-lookup"><span data-stu-id="917e2-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="917e2-125">Si ce n’est pas le cas, vous pouvez [Télécharger .net 4,0 à partir du centre de téléchargement](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="917e2-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="917e2-126">Exigences en matière d’autorisations IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-126">IdFix permissions requirements</span></span>

<span data-ttu-id="917e2-127">Le compte d’utilisateur que vous utilisez pour exécuter IdFix doit disposer d’un accès en lecture/écriture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="917e2-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="917e2-128">Si vous n’êtes pas certain que votre compte d’utilisateur répond à ces exigences et que vous n’êtes pas sûr de savoir comment procéder, vous pouvez toujours installer et exécuter IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="917e2-129">Si votre compte d’utilisateur ne dispose pas des autorisations appropriées, IdFix affiche simplement une erreur lorsque vous tentez de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="917e2-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="917e2-130">Installer IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-130">Install IdFix</span></span>

<span data-ttu-id="917e2-131">Pour installer IdFix, téléchargez et décompressez **IdFix. exe**:</span><span class="sxs-lookup"><span data-stu-id="917e2-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="917e2-132">Ouvrez une session sur l’ordinateur sur lequel vous souhaitez installer l’outil IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="917e2-133">Accédez au site de téléchargement Microsoft pour l' [outil de correction d’erreur DirSync IdFix](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="917e2-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="917e2-134">Choisissez **Download** (Télécharger).</span><span class="sxs-lookup"><span data-stu-id="917e2-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="917e2-135">Lorsque vous y êtes invité, choisissez **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="917e2-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="917e2-136">Dans la boîte de dialogue **WinZip Self-Extractor** , dans la zone de texte **Unzip to Folder** (décompresser dans le dossier), tapez ou accédez à l’emplacement où vous souhaitez installer l’outil IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="917e2-137">Par défaut, IdFix est installé dans `C:\Deployment Tools\`.</span><span class="sxs-lookup"><span data-stu-id="917e2-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="917e2-138">Sélectionnez **Unzip**.</span><span class="sxs-lookup"><span data-stu-id="917e2-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="917e2-139">Exécuter l’outil IdFix</span><span class="sxs-lookup"><span data-stu-id="917e2-139">Run the IdFix tool</span></span>

<span data-ttu-id="917e2-140">Une fois que vous avez installé IdFix, exécutez l’outil pour rechercher des problèmes dans votre répertoire:</span><span class="sxs-lookup"><span data-stu-id="917e2-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="917e2-141">À l’aide d’un compte disposant d’un accès en lecture/écriture à l’annuaire, ouvrez une session sur l’ordinateur sur lequel vous avez installé IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="917e2-142">Dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez installé IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="917e2-143">Si vous avez choisi le dossier par défaut lors de l' `C:\Deployment Tools\IdFix`installation, accédez à.</span><span class="sxs-lookup"><span data-stu-id="917e2-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="917e2-144">Double-cliquez sur **IdFix. exe**.</span><span class="sxs-lookup"><span data-stu-id="917e2-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Choisissez le fichier IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="917e2-146">Par défaut, IdFix utilise l’ensemble de règles mutualisée pour tester les entrées de votre répertoire.</span><span class="sxs-lookup"><span data-stu-id="917e2-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="917e2-147">Il s’agit de l’ensemble de règles approprié pour la plupart des clients Office 365.</span><span class="sxs-lookup"><span data-stu-id="917e2-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="917e2-148">Toutefois, si vous êtes un client Office 365 dédié ou ITAR (trafic international dans les réglementations sur les armes), vous pouvez configurer IdFix pour qu’il utilise le jeu de règles dédié à la place.</span><span class="sxs-lookup"><span data-stu-id="917e2-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="917e2-149">Si vous n’êtes pas sûr de votre type de client, vous pouvez en toute sécurité ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="917e2-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="917e2-150">Pour définir le jeu de règles sur dédié, cliquez sur l’icône d’engrenage dans la barre de menus, puis choisissez **dédié**.</span><span class="sxs-lookup"><span data-stu-id="917e2-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="917e2-151">Sélectionnez **requête**.</span><span class="sxs-lookup"><span data-stu-id="917e2-151">Choose **Query**.</span></span>
    
    ![Sélectionnez requête dans IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="917e2-153">Par défaut, IdFix recherche les erreurs dans le répertoire entier.</span><span class="sxs-lookup"><span data-stu-id="917e2-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="917e2-154">En fonction de la taille de votre répertoire, l’exécution de la requête peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="917e2-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="917e2-155">Vous pouvez suivre la progression au bas de la fenêtre principale de l’outil.</span><span class="sxs-lookup"><span data-stu-id="917e2-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="917e2-156">Si vous cliquez sur **Annuler**, vous devrez redémarrer depuis le début.</span><span class="sxs-lookup"><span data-stu-id="917e2-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Requête IdFix et nombre d’erreurs.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="917e2-158">Une fois que IdFix a terminé la requête, vous pouvez continuer et synchroniser votre annuaire s’il n’y a pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="917e2-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="917e2-159">S’il existe des erreurs dans votre répertoire, il est recommandé de les résoudre avant de procéder à la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="917e2-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="917e2-160">Si vous souhaitez obtenir des informations plus spécifiques sur les types d’erreurs et des recommandations sur la meilleure façon de corriger chacune d’elles, consultez les liens à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="917e2-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="917e2-161">Bien qu’il ne soit pas obligatoire de corriger les erreurs avant la synchronisation, nous vous recommandons vivement de consulter au moins toutes les erreurs renvoyées par IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="917e2-162">Chaque erreur est affichée sur une ligne distincte dans la fenêtre principale de l’outil.</span><span class="sxs-lookup"><span data-stu-id="917e2-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="917e2-163">Si vous acceptez le changement suggéré dans la colonne **mettre à jour** , dans la colonne **action** , sélectionnez les actions que doit effectuer IdFix pour implémenter la modification, puis cliquez sur **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="917e2-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="917e2-164">Lorsque vous cliquez sur **appliquer**, l’outil effectue les modifications dans l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="917e2-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="917e2-165">Il n’est pas nécessaire de cliquer sur **appliquer** après chaque mise à jour.</span><span class="sxs-lookup"><span data-stu-id="917e2-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="917e2-166">Au lieu de cela, vous pouvez corriger plusieurs erreurs avant de cliquer sur **appliquer** et IdFix les modifiera en même temps.</span><span class="sxs-lookup"><span data-stu-id="917e2-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="917e2-167">Vous pouvez trier les erreurs par type d’erreur en cliquant sur **erreur** en haut de la colonne qui répertorie les types d’erreur.</span><span class="sxs-lookup"><span data-stu-id="917e2-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="917e2-168">Une stratégie consiste à corriger toutes les erreurs du même type; par exemple, corrigez tous les doublons en premier, puis appliquez-les.</span><span class="sxs-lookup"><span data-stu-id="917e2-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="917e2-169">Ensuite, corrigez les erreurs de format de caractère, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="917e2-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="917e2-170">Chaque fois que vous appliquez les modifications, l’outil IdFix crée un fichier journal distinct que vous pouvez utiliser pour annuler vos modifications en cas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="917e2-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="917e2-171">Le [Journal des transactions](idfix-transaction-log.md) est stocké dans le dossier dans lequel vous avez installé IdFix.</span><span class="sxs-lookup"><span data-stu-id="917e2-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="917e2-172">_C:\Deployment Tools\IdFix_ par défaut.</span><span class="sxs-lookup"><span data-stu-id="917e2-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Correction des erreurs dans IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="917e2-174">Une fois que toutes les modifications ont été apportées au répertoire, exécutez à nouveau IdFix pour vous assurer que les corrections que vous avez apportées n’ont pas introduit de nouvelles erreurs.</span><span class="sxs-lookup"><span data-stu-id="917e2-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="917e2-175">Vous pouvez répéter ces étapes autant de fois que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="917e2-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="917e2-176">Il est recommandé de suivre le processus quelques fois avant de procéder à la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="917e2-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="917e2-177">Je souhaite affiner ma recherche ou approfondir les erreurs, que puis-je faire avec IdFix?</span><span class="sxs-lookup"><span data-stu-id="917e2-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="917e2-178">Des informations plus détaillées sont disponibles dans les rubriques suivantes:</span><span class="sxs-lookup"><span data-stu-id="917e2-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="917e2-179">[Préparez les attributs d’annuaire pour la synchronisation avec Office 365 à l’aide de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="917e2-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="917e2-180">Une fois que vous avez installé l’outil, accédez à cette rubrique pour obtenir des instructions plus détaillées sur l’exécution de l’outil, les erreurs courantes que vous rencontrez, les corrections suggérées, les exemples et les meilleures pratiques à suivre lorsque vous avez un grand nombre d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="917e2-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="917e2-181">Reference: IdFix excluded and supported objects and attributes</span><span class="sxs-lookup"><span data-stu-id="917e2-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="917e2-182">Référence : Journal des transactions IdFix d'Office 365</span><span class="sxs-lookup"><span data-stu-id="917e2-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="917e2-183">Vidéo de formation</span><span class="sxs-lookup"><span data-stu-id="917e2-183">Video training</span></span>

<span data-ttu-id="917e2-184">Pour plus d’informations, consultez la leçon [installer et utiliser l’outil IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), qui vous est proposée par LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="917e2-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

