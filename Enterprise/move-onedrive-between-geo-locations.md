---
title: Déplacer un site OneDrive vers un autre emplacement géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment déplacer un site OneDrive vers un autre emplacement géographique.
ms.openlocfilehash: 1197d23bdf94fe38ba24138ddde7c1f1fb92b41f
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931823"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="1bc93-103">Déplacer un site OneDrive vers un autre emplacement géographique</span><span class="sxs-lookup"><span data-stu-id="1bc93-103">Move a SharePoint site to a different geo location (Preview)</span></span> 

<span data-ttu-id="1bc93-p101">Avec le déplacement géographique OneDrive, vous pouvez déplacer le site OneDrive d’un utilisateur vers un autre emplacement géographique. Le déplacement géographique OneDrive est effectué par l’administrateur SharePoint Online ou l’administrateur général Office 365. Avant de commencer un déplacement géographique OneDrive, veillez à informer l’utilisateur dont le site OneDrive va être déplacé et conseillez-lui de fermer tous les fichiers pendant la durée du déplacement. (Si l’utilisateur a un document ouvert à l’aide du client Office lors du déplacement, à la fin du déplacement, le document devra être enregistré dans le nouvel emplacement.) Le déplacement peut être planifié à un autre moment, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="1bc93-p102">Le service OneDrive utilise un Stockage Blob Azure pour stocker du contenu. Le blob Stockage associé au site OneDrive de l’utilisateur est déplacé de la source à l’emplacement géographique de destination dans les 40 jours qui suivent la mise à disposition du site OneDrive de destination à l’utilisateur. L’accès au site OneDrive de l’utilisateur est restauré dès que le site OneDrive de destination est disponible.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="1bc93-p103">Pendant la durée du déplacement géographique du site OneDrive (environ 2 à 6 heures), le site OneDrive de l’utilisateur est défini en lecture seule. L’utilisateur peut toujours accéder à ses fichiers via le client de synchronisation OneDrive  ou son site OneDrive dans SharePoint Online. Une fois le déplacement géographique du site OneDrive terminé, l’utilisateur est connecté automatiquement à son site OneDrive à l’emplacement géographique de destination lorsqu’il navigue vers OneDrive dans le lanceur d’applications Office 365. Le client de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="1bc93-115">Les procédures décrites dans cet article nécessitent le [module Microsoft SharePoint Online PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="1bc93-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="1bc93-116">Communication avec vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="1bc93-116">Communicating to your users</span></span>

<span data-ttu-id="1bc93-p104">Lors du déplacement de sites OneDrive entre différents emplacements géographiques, il est important de communiquer à vos utilisateurs ce à quoi ils doivent s’attendre. Cela peut vous aider à réduire la confusion des utilisateurs et diminuer le nombre d’appels à votre support technique. Prévenez vos utilisateurs par courriel avant le déplacement et faites-leur part des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1bc93-p104">When moving OneDrive sites between geo locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="1bc93-120">La date de début prévue du déplacement et la durée attendue de l’opération.</span><span class="sxs-lookup"><span data-stu-id="1bc93-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="1bc93-121">L’emplacement géographique vers lequel est déplacé leur espace OneDrive et l’URL permettant d’accéder au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="1bc93-122">Conseillez-leur de fermer leurs fichiers et de ne pas y apporter de modifications lors du déplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="1bc93-123">Le partage et les autorisations de fichiers ne sont modifiés par la migration.</span><span class="sxs-lookup"><span data-stu-id="1bc93-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="1bc93-124">Présentez-leur l’[expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="1bc93-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="1bc93-125">N’oubliez pas d’envoyer un courrier électronique à vos utilisateurs une fois le déplacement terminé pour les avertir qu’ils peuvent reprendre leur travail dans OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bc93-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-onedrive-site-moves"></a><span data-ttu-id="1bc93-126">Planification de déplacements de site OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-126">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="1bc93-p105">Vous pouvez planifier les déplacements de site OneDrive à l’avance (décrit plus loin dans cet article). Nous vous recommandons de commencer avec un petit nombre d’utilisateurs pour valider vos stratégies de communication et de flux de travail. Une fois que vous êtes habitué au processus, vous pouvez planifier des déplacements comme suit :</span><span class="sxs-lookup"><span data-stu-id="1bc93-p105">You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:</span></span>

- <span data-ttu-id="1bc93-130">Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.</span><span class="sxs-lookup"><span data-stu-id="1bc93-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="1bc93-131">Lorsque les déplacements commencent, vous pouvez planifier plus d’informations, avec un maximum de 4 000 déplacements dans la file d’attente et à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="1bc93-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
- <span data-ttu-id="1bc93-132">Nous vous recommandons de ne pas planifier plus de 4 000 déplacements par mois.</span><span class="sxs-lookup"><span data-stu-id="1bc93-132">We recommend not scheduling more than 4,000 moves per month.</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="1bc93-133">Déplacement d’un site OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-133">Moving a OneDrive site</span></span>

<span data-ttu-id="1bc93-p106">Pour effectuer un déplacement géographique OneDrive, l’administrateur client doit commencer par définir l’emplacement des données par défaut de l’utilisateur sur l’emplacement géographique approprié. Une fois que cet emplacement est défini, patientez au moins 24 heures pendant  la synchronisation de la mise à jour de l’emplacement des données par défaut sur les emplacements géographiques avant de commencer le déplacement géographique OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p106">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="1bc93-136">Lorsque vous utilisez les cmdlets de déplacement géographique, connectez-vous au service SPO à l’emplacement géographique OneDrive actuel de l’utilisateur, à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="1bc93-136">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="1bc93-137">Par exemple : pour déplacer le site OneDrive de l’utilisateur ’Matt@contosoenergy.onmicrosoft.com’, connectez-vous au centre d’administration SharePoint EUR car le site OneDrive de l’utilisateur se trouve dans l’emplacement géographique EUR :</span><span class="sxs-lookup"><span data-stu-id="1bc93-137">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![Capture d’écran d’une fenêtre PowerShell affichant la cmdlet connect-sposervice](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="1bc93-139">Validation de l’environnement</span><span class="sxs-lookup"><span data-stu-id="1bc93-139">Validating the environment</span></span>

<span data-ttu-id="1bc93-140">Avant de commencer un déplacement géographique OneDrive, nous vous recommandons de valider l’environnement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-140">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="1bc93-141">Pour vous assurer que tous les emplacements géographiques sont compatibles, exécutez :</span><span class="sxs-lookup"><span data-stu-id="1bc93-141">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCrossCompatibilityStatus`

<span data-ttu-id="1bc93-142">Une liste de vos emplacements géographiques s’affichera et le contenu que vous pourrez déplacer entre ces emplacements sera marqué « Compatible ».</span><span class="sxs-lookup"><span data-stu-id="1bc93-142">You will see a list of your geo locations and whether content can be moved between will be denoted as "Compatible".</span></span> <span data-ttu-id="1bc93-143">Si la commande renvoie « Incompatible », réessayez de valider l’état plus tard.</span><span class="sxs-lookup"><span data-stu-id="1bc93-143">If the command returns "Incompatible" please retry validating the status at a later date.</span></span>

<span data-ttu-id="1bc93-144">Si un OneDrive contient, par exemple, un sous-site, il ne peut pas être déplacé.</span><span class="sxs-lookup"><span data-stu-id="1bc93-144">If a OneDrive contains a subsite, for example, it cannot be moved.</span></span> <span data-ttu-id="1bc93-145">Vous pouvez utiliser la cmdlet Start-SPOUserAndContentMove avec le paramètre -ValidationOnly pour contrôler si le site OneDrive peut être déplacé :</span><span class="sxs-lookup"><span data-stu-id="1bc93-145">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="1bc93-p109">Ceci renvoie Opération réussie si le site OneDrive est prêt à être déplacé ou Échec s’il existe une conservation légale ou un sous-site qui empêche le déplacement. Une fois que vous avez contrôlé que le site OneDrive est prêt à être déplacé, vous pouvez commencer le déplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p109">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="1bc93-148">Démarrer un déplacement géographique OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-148">Start a OneDrive geo move</span></span>

<span data-ttu-id="1bc93-149">Pour démarrer le déplacement, exécutez :</span><span class="sxs-lookup"><span data-stu-id="1bc93-149">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="1bc93-150">À l’aide de ces paramètres :</span><span class="sxs-lookup"><span data-stu-id="1bc93-150">Using these parameters:</span></span>

-   <span data-ttu-id="1bc93-151">_UserPrincipalName_ : UPN de l’utilisateur dont le site OneDrive est déplacé.</span><span class="sxs-lookup"><span data-stu-id="1bc93-151">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="1bc93-p110">_DestinationDataLocation_ : emplacement géographique dans lequel le site OneDrive doit être déplacé. Il doit être identique à l’emplacement des données par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p110">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="1bc93-154">Nous vous recommandons d’exécuter `Get-SPOGeoMoveStateCompatibility` avec `ValidationOnly` avant de lancer le déplacement géographique du site OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bc93-154">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="1bc93-155">Par exemple, pour déplacer le site OneDrive de matt@contosoenergy.onmicrosoft.com de l’emplacement EUR à AUS, exécutez :</span><span class="sxs-lookup"><span data-stu-id="1bc93-155">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Capture d’écran de la fenêtre PowerShell affichant la cmdlet Start-SPOUserAndContentMove](media/move-onedrive-between-geo-locations-image2.png)

<span data-ttu-id="1bc93-157">Pour planifier un déplacement géographique à un autre moment, utilisez l’un des paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="1bc93-157">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="1bc93-p111">_PreferredMoveBeginDate_ : le déplacement commencera probablement à l’heure spécifiée. L’heure doit être spécifiée en Temps universel coordonné (UTC).</span><span class="sxs-lookup"><span data-stu-id="1bc93-p111">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="1bc93-p112">_PreferredMoveEndDate_ : le déplacement se terminera probablement d’ici l’heure spécifiée, dans la mesure du possible. L’heure doit être spécifiée en Temps universel coordonné (UTC).</span><span class="sxs-lookup"><span data-stu-id="1bc93-p112">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="1bc93-162">Annuler un déplacement géographique OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-162">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="1bc93-163">Vous pouvez arrêter le déplacement géographique du site OneDrive d’un utilisateur tant que le déplacement géographique n’est pas en cours ou terminé, en utilisant la cmdlet :</span><span class="sxs-lookup"><span data-stu-id="1bc93-163">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="1bc93-164">où _UserPrincipalName_ est l’UPN de l’utilisateur dont vous souhaitez arrêter le déplacement du site OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bc93-164">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="1bc93-165">Déterminer l’état actuel</span><span class="sxs-lookup"><span data-stu-id="1bc93-165">Determining current status</span></span>

<span data-ttu-id="1bc93-166">Vous pouvez vérifier l’état du déplacement géographique d’un site OneDrive à l’intérieur ou à l’extérieur de l’emplacement géographique auquel vous êtes connecté à l’aide de la cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="1bc93-166">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="1bc93-167">Ces états de déplacement sont décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1bc93-167">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1bc93-168"><strong>État</strong></span><span class="sxs-lookup"><span data-stu-id="1bc93-168"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="1bc93-169"><strong>Description</strong></span><span class="sxs-lookup"><span data-stu-id="1bc93-169"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="1bc93-170">NotStarted</span><span class="sxs-lookup"><span data-stu-id="1bc93-170">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="1bc93-171">Le déplacement n’a pas commencé.</span><span class="sxs-lookup"><span data-stu-id="1bc93-171">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bc93-172">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="1bc93-172">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="1bc93-173">Le déplacement est en cours dans l’un des états suivants : Validation (1/4), Sauvegarde (2/4), Restauration (3/4), Nettoyage (4/4).</span><span class="sxs-lookup"><span data-stu-id="1bc93-173">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1bc93-174">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="1bc93-174">Success</span></span></td>
<td align="left"><span data-ttu-id="1bc93-175">Le déplacement a réussi.</span><span class="sxs-lookup"><span data-stu-id="1bc93-175">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bc93-176">Échec</span><span class="sxs-lookup"><span data-stu-id="1bc93-176">Failed</span></span></td>
<td align="left"><span data-ttu-id="1bc93-177">Le déplacement a échoué.</span><span class="sxs-lookup"><span data-stu-id="1bc93-177">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="1bc93-178">Pour rechercher l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre UserPrincipalName :</span><span class="sxs-lookup"><span data-stu-id="1bc93-178">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="1bc93-179">Pour rechercher l’état de tous les déplacements à l’intérieur ou à l’extérieur de l’emplacement géographique auquel vous êtes connecté, utilisez le paramètre MoveState avec l’une des valeurs suivantes : NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="1bc93-179">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="1bc93-180">Vous pouvez également ajouter le paramètre `-Verbose` pour des descriptions plus détaillées de l’état de déplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-180">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="1bc93-181">Expérience de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="1bc93-181">User Experience</span></span>

<span data-ttu-id="1bc93-p113">Les utilisateurs de OneDrive devraient observer des perturbations minimales si leur site OneDrive est déplacé vers un autre emplacement géographique. Excepté un état de lecture seule bref lors du déplacement, les autorisations et liens existants continueront à fonctionner comme prévu une fois le déplacement terminé.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p113">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="1bc93-184">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="1bc93-184">OneDrive for Business</span></span>

<span data-ttu-id="1bc93-p114">Lorsque le déplacement est en cours, le site OneDrive de l’utilisateur est défini en lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers son site OneDrive dans le nouvel emplacement géographique lorsqu’il navigue vers OneDrive dans le lanceur d’applications Office 365 ou un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p114">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="1bc93-187">Autorisations sur le contenu OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-187">Permissions on OneDrive content</span></span>

<span data-ttu-id="1bc93-188">Les utilisateurs disposant d’autorisations sur le contenu OneDrive auront toujours accès au contenu pendant le déplacement et une fois qu’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="1bc93-188">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="1bc93-189">Client de synchronisation OneDrive</span><span class="sxs-lookup"><span data-stu-id="1bc93-189">OneDrive Sync Client</span></span> 

<span data-ttu-id="1bc93-p115">Le client de synchronisation OneDrive détecte automatiquement la synchronisation avec le nouvel emplacement OneDrive et la transfère en toute transparence une fois le déplacement géographique de OneDrive terminé. L’utilisateur n’a pas besoin de se connecter à nouveau, ni d’effectuer une autre action. (Version 17.3.6943.0625 ou ultérieure du client de synchronisation requise.)</span><span class="sxs-lookup"><span data-stu-id="1bc93-p115">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="1bc93-193">Si un utilisateur met à jour un fichier pendant le déplacement géographique de OneDrive, le client de synchronisation l’informe que des téléchargements de fichiers sont en attente pendant le déplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-193">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="1bc93-194">Liens de partage</span><span class="sxs-lookup"><span data-stu-id="1bc93-194">Sharing links</span></span> 

<span data-ttu-id="1bc93-195">Lorsque le déplacement géographique de OneDrive est terminé, les liens partagés existants pour les fichiers qui ont été déplacés redirigent automatiquement vers le nouvel emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="1bc93-195">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="1bc93-196">Expérience OneNote</span><span class="sxs-lookup"><span data-stu-id="1bc93-196">OneNote Experience</span></span> 

<span data-ttu-id="1bc93-p116">Le client OneNote win32 client et l’application UWP (universelle) détecteront automatiquement et synchroniseront en toute transparence les blocs-notes avec le nouvel emplacement OneDrive à la fin du déplacement géographique de OneDrive. L’utilisateur n’a pas besoin de se connecter à nouveau ou d’effectuer une autre action. Le seul indicateur visible pour l’utilisateur est l’échec de la synchronisation des blocs-notes lorsque le déplacement géographique de OneDrive est en cours. Cette expérience est disponible sur les versions de client OneNote suivantes :</span><span class="sxs-lookup"><span data-stu-id="1bc93-p116">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="1bc93-201">OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="1bc93-201">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="1bc93-202">OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="1bc93-202">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="1bc93-203">Application mobile OneNote : Version 16.0.8431.1011 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="1bc93-203">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="1bc93-204">Application Teams</span><span class="sxs-lookup"><span data-stu-id="1bc93-204">Teams app</span></span>

<span data-ttu-id="1bc93-p117">Lorsque le déplacement géographique de OneDrive est terminé, les utilisateurs ont accès à leurs fichiers OneDrive sur l’application Teams. En outre, les fichiers partagés via la conversation Teams de leur site OneDrive avant le déplacement géographique continuent à fonctionner après le déplacement.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p117">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="1bc93-207">Application mobile OneDrive Entreprise (iOS)</span><span class="sxs-lookup"><span data-stu-id="1bc93-207">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="1bc93-208">Lorsque le déplacement géographique de OneDrive est terminé, l’utilisateur doit se déconnecter et se reconnecter sur l’application mobile iOS pour réaliser la synchronisation avec le nouvel emplacement OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bc93-208">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="1bc93-209">Sites et groupes suivis existants</span><span class="sxs-lookup"><span data-stu-id="1bc93-209">Existing followed groups and sites</span></span>

<span data-ttu-id="1bc93-p118">Les sites et groupes suivis apparaissent dans OneDrive Entreprise de l’utilisateur indépendamment de leur emplacement géographique. Les sites et groupes hébergés dans un autre emplacement géographique s’ouvrent dans un onglet distinct.</span><span class="sxs-lookup"><span data-stu-id="1bc93-p118">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
