---
title: Déplacer un site de OneDrive à une autre géolocalisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Découvrez comment déplacer un site de OneDrive à un emplacement géographique différent.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="9e2b4-103">Déplacer un site de OneDrive à une autre géolocalisation</span><span class="sxs-lookup"><span data-stu-id="9e2b4-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="9e2b4-p101">OneDrive geo déplacer, vous pouvez déplacer les OneDrive d’un utilisateur à un emplacement géographique différent. OneDrive geo déplacer est effectuée par l’administrateur SharePoint Online ou de l’administrateur Office 365. Avant de commencer une OneDrive geo déplacer, veillez à informer l’utilisateur, dont OneDrive est déplacé et vous recommandons de que les ferment tous les fichiers pour la durée du déplacement. (Si l’utilisateur dispose d’un document ouvert à l’aide du client Office pendant le déplacement, puis sur Déplacer achèvement le document devra être enregistré dans le nouvel emplacement.) Le déplacement peut être planifié à une date ultérieure, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="9e2b4-p102">Le service OneDrive utilise le stockage Blob Azure pour stocker le contenu. Le blob de stockage associé à OneDrive l’utilisateur est déplacé de la source à l’emplacement de destination géographique dans les quarante jours de destination OneDrive étant disponible pour l’utilisateur. L’accès à OneDrive l’utilisateur reprend dès que la destination OneDrive est disponible.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="9e2b4-p103">Au cours de la fenêtre de déplacer geo OneDrive (environ 2 à 6 heures) OneDrive de l’utilisateur a la valeur en lecture seule. L’utilisateur peut toujours accéder à leurs fichiers via le client de synchronisation de OneDrive ou de leur site de OneDrive dans SharePoint Online. Après déplacement de geo OneDrive, l’utilisateur sera automatiquement connecté à leur OneDrive à l’emplacement géographique de destination lorsqu’ils naviguent sur OneDrive dans le Lanceur d’applications Office 365. Le client de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="9e2b4-115">Les procédures décrites dans cet article requièrent le [PowerShell Module en ligne de Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="9e2b4-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="9e2b4-116">Déplacement d’un site OneDrive</span><span class="sxs-lookup"><span data-stu-id="9e2b4-116">Moving a OneDrive site</span></span>

<span data-ttu-id="9e2b4-p104">Pour effectuer une OneDrive geo déplacer, l’administrateur doit d’abord définir emplacement de données par défaut (PDL de l’utilisateur) pour l’emplacement géographique appropriée. Une fois le langage PDL, attendez au moins 24 heures pour la mise à jour PDL à synchroniser à travers les emplacements geo avant de commencer le déplacement de geo OneDrive.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="9e2b4-119">Lorsque vous déplacez à l’aide de la zone géographique des applets de commande, se connecter au Service SPO chez l’utilisateur en cours OneDrive géographique, à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="9e2b4-120">Par exemple : pour déplacer les OneDrive de l’utilisateur 'Matt@contosoenergy.onmicrosoft.com', de se connecter au centre d’administration de SharePoint euros comme OneDrive de l’utilisateur est dans l’emplacement géographique d’euros :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="9e2b4-121">Validation de l’environnement</span><span class="sxs-lookup"><span data-stu-id="9e2b4-121">Validating the environment</span></span>

<span data-ttu-id="9e2b4-122">Avant de commencer un geo OneDrive déplacer, nous vous recommandons de valider l’environnement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="9e2b4-123">Pour vous assurer que tous les emplacements de la zone géographique sont compatibles, exécutez :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="9e2b4-p105">Si un OneDrive est sous scellé ou si elle contient un sous-site, il ne peut pas être déplacé. Vous pouvez utiliser l’applet de commande Start-SPOUserAndContentMove avec le paramètre - ValidationOnly à valider si l’OneDrive est en mesure d’être déplacés :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="9e2b4-p106">Ceci renverra une réussite si l’OneDrive est prête à être déplacée ou échouer s’il existe un ordre de retenue ou d’un sous-site qui peut empêcher le déplacement. Une fois que vous avez validé que le OneDrive est prêt à passer, vous pouvez démarrer le déplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="9e2b4-128">Démarrer un déplacement de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="9e2b4-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="9e2b4-129">Pour démarrer le déplacement, exécutez :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="9e2b4-130">À l’aide de ces paramètres :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-130">Using these parameters:</span></span>

-   <span data-ttu-id="9e2b4-131">_UserPrincipalName_ – UPN de l’utilisateur, dont OneDrive est en cours de déplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="9e2b4-p107">_DestinationDataLocation_ – emplacement géographique où le OneDrive doit être déplacé. Cette valeur doit être identique à l’emplacement de données par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2b4-134">Nous vous recommandons d’exécution `Get-SPOGeoMoveStateCompatibility` avec `ValidationOnly` avant de lancer OneDrive geo déplacer.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="9e2b4-135">Par exemple, pour déplacer le OneDrive de matt@contosoenergy.onmicrosoft.com d’euros à l’Australie, exécutez :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="9e2b4-136">Pour planifier un déplacement geo ultérieurement, utilisez un des paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="9e2b4-137">_PreferredMoveBeginDate_ – la volonté de déplacement susceptibles de commencer en ce moment spécifié.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-137">_PreferredMoveBeginDate_ – The move will likely begin at this specified time.</span></span>

-   <span data-ttu-id="9e2b4-138">_PreferredMoveEndDate_ – la volonté de déplacement susceptibles d’être terminée à cette heure spécifiée, de mieux.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-138">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis.</span></span>

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="9e2b4-139">Annuler un déplacement de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="9e2b4-139">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="9e2b4-140">Vous pouvez arrêter le déplacement géographique de, OneDrive l’utilisateur, si le déplacement n’est pas en cours ou complétés à l’aide de l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-140">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="9e2b4-141">_UserPrincipalName_ étant le nom UPN de l’utilisateur dont OneDrive déplacer que vous souhaitez arrêter.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-141">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="9e2b4-142">Détermination de l’état en cours</span><span class="sxs-lookup"><span data-stu-id="9e2b4-142">Determining current status</span></span>

<span data-ttu-id="9e2b4-143">Vous pouvez vérifier l’état d’un OneDrive geo déplacer dans ou hors le geo auquel vous êtes connecté à l’aide de l’applet de commande Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-143">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="9e2b4-144">Les statuts de déplacement sont décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-144">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9e2b4-145"><strong>État</strong></span><span class="sxs-lookup"><span data-stu-id="9e2b4-145"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="9e2b4-146"><strong>Description</strong></span><span class="sxs-lookup"><span data-stu-id="9e2b4-146"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9e2b4-147">NotStarted</span><span class="sxs-lookup"><span data-stu-id="9e2b4-147">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="9e2b4-148">Le déplacement n’a pas démarré.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-148">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9e2b4-149">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="9e2b4-149">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="9e2b4-150">Le déplacement est en cours dans un des états suivants : Validation (1/4), (2/4) de sauvegarde, restauration (3/4), nettoyage (4/4).</span><span class="sxs-lookup"><span data-stu-id="9e2b4-150">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9e2b4-151">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="9e2b4-151">Success</span></span></td>
<td align="left"><span data-ttu-id="9e2b4-152">Le déplacement a réussi.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-152">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9e2b4-153">Failed</span><span class="sxs-lookup"><span data-stu-id="9e2b4-153">Failed</span></span></td>
<td align="left"><span data-ttu-id="9e2b4-154">Le déplacement a échoué.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-154">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="9e2b4-155">Pour connaître l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre UserPrincipalName :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-155">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="9e2b4-156">Pour connaître l’état de tous les mouvements dans ou hors de l’emplacement géographique auquel vous êtes connecté, utilisez le paramètre MoveState avec l’une des valeurs suivantes : NotStarted, InProgress, réussite, échec, toutes les.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-156">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="9e2b4-157">Vous pouvez également ajouter la `-Verbose` paramètre pour obtenir une description plus détaillée de l’état du déplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-157">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="9e2b4-158">Expérience de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9e2b4-158">User Experience</span></span>

<span data-ttu-id="9e2b4-p108">Les utilisateurs de OneDrive Notez perturbant si leur OneDrive est déplacé vers un emplacement géographique différent. En plus d’un état de lecture seule brève au cours du déplacement, les autorisations et les liens existants continueront à fonctionner comme prévu une fois le déplacement terminé.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p108">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="9e2b4-161">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="9e2b4-161">OneDrive for Business</span></span>

<span data-ttu-id="9e2b4-p109">Pendant le déplacement OneDrive de l’utilisateur a la valeur en lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers leur OneDrive dans le nouvel emplacement géographique lorsqu’ils naviguent pour OneDrive le Lanceur d’applications Office 365 ou un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p109">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="9e2b4-164">Autorisations sur le contenu de OneDrive</span><span class="sxs-lookup"><span data-stu-id="9e2b4-164">Permissions on OneDrive content</span></span>

<span data-ttu-id="9e2b4-165">Les utilisateurs disposant d’autorisations sur le contenu de OneDrive continueront d’avoir accès au contenu au cours du déplacement, et une fois celle-ci terminée.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-165">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="9e2b4-166">Client de synchronisation OneDrive</span><span class="sxs-lookup"><span data-stu-id="9e2b4-166">OneDrive Sync Client</span></span> 

<span data-ttu-id="9e2b4-p110">Le client de synchronisation OneDrive détecte automatiquement et transférer en toute transparence la synchronisation vers le nouvel emplacement de OneDrive une fois le déplacement de geo OneDrive est terminé. L’utilisateur n’a pas besoin de signer de nouveau ou exécuter toute autre action.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p110">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="9e2b4-169">Si un utilisateur met à jour un fichier alors que le déplacement de geo OneDrive est en cours, le client de synchronisation avertit les que les téléchargements de fichiers sont en attente pendant le déplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-169">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="9e2b4-170">Partage des liaisons</span><span class="sxs-lookup"><span data-stu-id="9e2b4-170">Sharing links</span></span> 

<span data-ttu-id="9e2b4-171">Lors de la OneDrive geo déplacer achèvement, redirige automatiquement les liens partagés existants pour les fichiers qui ont été déplacés vers le nouvel emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-171">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="9e2b4-172">Expérience de OneNote</span><span class="sxs-lookup"><span data-stu-id="9e2b4-172">OneNote Experience</span></span> 

<span data-ttu-id="9e2b4-p111">Client win32 de OneNote et UWP App (universel) détecte automatiquement et OneDrive geo déplacement en toute transparence de synchronisation portables vers le nouvel emplacement de OneDrive. L’utilisateur n’a pas besoin de signer de nouveau ou exécuter toute autre action. L’indicateur visible uniquement à l’utilisateur est la synchronisation de l’ordinateur portable échouent lorsque OneDrive geo déplacement est en cours. Cette expérience est disponible sur les versions de client OneNote suivantes :</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p111">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="9e2b4-177">OneNote win32 : Version 16.0.8326.2096 (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="9e2b4-177">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="9e2b4-178">OneNote UWP – Version 16.0.8431.1006 (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="9e2b4-178">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="9e2b4-179">OneNote Mobile Application – Version 16.0.8431.1011 (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="9e2b4-179">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="9e2b4-180">Application des équipes</span><span class="sxs-lookup"><span data-stu-id="9e2b4-180">Teams app</span></span>

<span data-ttu-id="9e2b4-p112">Lors de la OneDrive geo déplacer l’achèvement, les utilisateurs auront plus accès à leurs fichiers de OneDrive sur les équipes App, fichiers partagés via le chat d’équipes à partir de leur OneDrive avant le déplacement de geo continue de fonctionner après déplacement.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p112">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="9e2b4-183">OneDrive pour l’entreprise Mobile application (iOS)</span><span class="sxs-lookup"><span data-stu-id="9e2b4-183">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="9e2b4-184">Lors de la OneDrive geo déplacer l’achèvement, l’utilisateur devra se déconnecter et reconnecter sur iOS application Mobile à synchroniser avec le nouvel emplacement de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-184">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="9e2b4-185">Existant suivi des sites et des groupes</span><span class="sxs-lookup"><span data-stu-id="9e2b4-185">Existing followed groups and sites</span></span>

<span data-ttu-id="9e2b4-p113">Groupes et des sites visités seront afficheront dans la OneDrive de l’utilisateur pour les entreprises, quel que soit leur emplacement géographique. Sites et groupes hébergés dans un autre emplacement géographique seront ouvre dans un onglet séparé.</span><span class="sxs-lookup"><span data-stu-id="9e2b4-p113">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
