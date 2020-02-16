---
title: Déplacer un site SharePoint vers un autre emplacement géographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
f1.keywords:
- NOCSH
description: Découvrez comment déplacer un site OneDrive vers un autre emplacement géographique.
ms.openlocfilehash: 903daff5af44789774b09000ebe52a6046ffc5d3
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974853"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="50e57-103">Déplacer un site SharePoint vers un autre emplacement géographique</span><span class="sxs-lookup"><span data-stu-id="50e57-103">Move a SharePoint site to a different geo location</span></span>

<span data-ttu-id="50e57-104">La fonctionnalité de déplacement géographique de site de SharePoint vous permet de déplacer des sites SharePoint sur d’autres emplacements géographiques au sein de votre environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="50e57-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="50e57-105">Les types de sites pouvant être déplacés entre emplacements géographiques sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="50e57-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="50e57-106">Sites connectés à un groupe Office 365</span><span class="sxs-lookup"><span data-stu-id="50e57-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="50e57-107">Sites modernes non associés à un groupe Office 365</span><span class="sxs-lookup"><span data-stu-id="50e57-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="50e57-108">Sites SharePoint classiques</span><span class="sxs-lookup"><span data-stu-id="50e57-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="50e57-109">Sites de communication</span><span class="sxs-lookup"><span data-stu-id="50e57-109">Communication sites</span></span>

<span data-ttu-id="50e57-110">Pour pouvoir déplacer un site, vous devez être un administrateur général ou un administrateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="50e57-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="50e57-111">Lors du déplacement géographique de site SharePoint, il existe une fenêtre en lecture seule d’environ 4 à 6 heures, selon le contenu du site.</span><span class="sxs-lookup"><span data-stu-id="50e57-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="50e57-112">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="50e57-112">Best practices</span></span>

- <span data-ttu-id="50e57-113">Essayez d’effectuer un déplacement de site SharePoint sur un site de test pour vous familiariser avec la procédure.</span><span class="sxs-lookup"><span data-stu-id="50e57-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="50e57-114">Avant de planifier ou d’effectuer le déplacement, vérifiez si le site peut être déplacé.</span><span class="sxs-lookup"><span data-stu-id="50e57-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="50e57-115">Autant que possible, planifiez les déplacements intersites en dehors des heures d’ouverture afin de réduire l’impact sur les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="50e57-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="50e57-116">Avant de déplacer des sites, communiquez avec les utilisateurs concernés.</span><span class="sxs-lookup"><span data-stu-id="50e57-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="50e57-117">Communication avec vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="50e57-117">Communicating to your users</span></span>

<span data-ttu-id="50e57-118">Lors du déplacement géographique de sites SharePoint, il est important d’indiquer aux utilisateurs des sites (généralement, toute personne ayant la possibilité de modifier le site) à quoi ils doivent s’attendre.</span><span class="sxs-lookup"><span data-stu-id="50e57-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="50e57-119">Cela peut vous aider à atténuer la confusion des utilisateurs et les appels à votre support technique.</span><span class="sxs-lookup"><span data-stu-id="50e57-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="50e57-120">Avant de déplacer des sites, envoyez un courrier électronique à leurs utilisateurs pour leur communiquer les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="50e57-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="50e57-121">date de début et durée prévues du déplacement ;</span><span class="sxs-lookup"><span data-stu-id="50e57-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="50e57-122">emplacement géographique cible du déplacement et URL permettant d’accéder à ce nouvel emplacement ;</span><span class="sxs-lookup"><span data-stu-id="50e57-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="50e57-123">nécessité de fermer les fichiers et de ne pas y apporter de modifications durant le déplacement ;</span><span class="sxs-lookup"><span data-stu-id="50e57-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="50e57-124">absence de modification des autorisations et des partages de fichiers en raison du déplacement ;</span><span class="sxs-lookup"><span data-stu-id="50e57-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="50e57-125">changement d’expérience utilisateur dans un environnement multigéographique.</span><span class="sxs-lookup"><span data-stu-id="50e57-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="50e57-126">Une fois le déplacement terminé, n’oubliez pas d’envoyer un courrier aux utilisateurs de vos sites pour les avertir qu’ils peuvent reprendre leur travail.</span><span class="sxs-lookup"><span data-stu-id="50e57-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="50e57-127">Planification des déplacements de sites SharePoint</span><span class="sxs-lookup"><span data-stu-id="50e57-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="50e57-128">Vous pouvez planifier les déplacements de sites SharePoint (voir plus loin dans cet article).</span><span class="sxs-lookup"><span data-stu-id="50e57-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="50e57-129">Vous pouvez planifier les déplacements comme suit :</span><span class="sxs-lookup"><span data-stu-id="50e57-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="50e57-130">Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.</span><span class="sxs-lookup"><span data-stu-id="50e57-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="50e57-131">Lorsque les déplacements commencent, vous pouvez planifier plus d’informations, avec un maximum de 4 000 déplacements dans la file d’attente et à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="50e57-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="50e57-132">Pour planifier un déplacement géographique de site SharePoint, lorsque vous commencez le déplacement, incluez parmi l’un des paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="50e57-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="50e57-133">`PreferredMoveBeginDate` – Le déplacement commencera probablement à l’heure indiquée.</span><span class="sxs-lookup"><span data-stu-id="50e57-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="50e57-134">`PreferredMoveEndDate` – Le déplacement devrait être terminé à l’heure indiquée.</span><span class="sxs-lookup"><span data-stu-id="50e57-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="50e57-135">L’heure doit être exprimée en Temps universel coordonné (UTC) pour les deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="50e57-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="50e57-136">Déplacement du site</span><span class="sxs-lookup"><span data-stu-id="50e57-136">Moving the site</span></span>

<span data-ttu-id="50e57-137">Un déplacement géographique de site SharePoint nécessite que vous vous connectiez et opériez le déplacement de l’URL d’administration SharePoint vers l’emplacement géographique du site.</span><span class="sxs-lookup"><span data-stu-id="50e57-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="50e57-138">Par exemple, si l’URL du site est https://contosohealthcare.sharepoint.com/sites/Turbines, connectez-vous à l’URL d’administration SharePoint https://contosohealthcare-admin.sharepoint.com:</span><span class="sxs-lookup"><span data-stu-id="50e57-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`Connect-SPOService -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="50e57-139">Validation de l’environnement</span><span class="sxs-lookup"><span data-stu-id="50e57-139">Validating the environment</span></span>

<span data-ttu-id="50e57-140">Avant de planifier le déplacement d’un site, nous vous recommandons de vérifier que celui-ci peut être déplacé.</span><span class="sxs-lookup"><span data-stu-id="50e57-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="50e57-141">Il n’est pas possible de déplacer des sites avec :</span><span class="sxs-lookup"><span data-stu-id="50e57-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="50e57-142">Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="50e57-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="50e57-143">InfoPath Forms</span><span class="sxs-lookup"><span data-stu-id="50e57-143">InfoPath forms</span></span> 

<span data-ttu-id="50e57-144">Pour vous assurer que tous les emplacements géographiques sont compatibles, exécutez la cmdlet `Get-SPOGeoMoveCrossCompatibilityStatus`.</span><span class="sxs-lookup"><span data-stu-id="50e57-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="50e57-145">Cela a pour effet d’afficher les emplacements géographiques et d’indiquer si leur environnement est compatible avec l’emplacement géographique cible.</span><span class="sxs-lookup"><span data-stu-id="50e57-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="50e57-146">Pour vérifier si votre site peut être déplacé, utilisez la cmdlet `Start-SPOSiteContentMove` avec le paramètre `-ValidationOnly`.</span><span class="sxs-lookup"><span data-stu-id="50e57-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="50e57-147">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="50e57-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="50e57-148">Cette cmdlet retourne *Success* si le site peut être déplacé, ou *Fail* en cas de blocage du déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="50e57-149">Démarrer un déplacement géographique de site SharePoint sans groupe Office 365 associé</span><span class="sxs-lookup"><span data-stu-id="50e57-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="50e57-150">Par défaut, l’URL initiale du site est remplacée par l’URL de l’emplacement géographique cible.</span><span class="sxs-lookup"><span data-stu-id="50e57-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="50e57-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="50e57-151">For example:</span></span>

<span data-ttu-id="50e57-152">https://Contoso.sharepoint.com/sites/projectx devient https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="50e57-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="50e57-153">Quand un site est dépourvu d’association de groupe Office 365, vous pouvez également le renommer à l’aide du paramètre `-DestinationUrl`.</span><span class="sxs-lookup"><span data-stu-id="50e57-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="50e57-154">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="50e57-154">For example:</span></span>

<span data-ttu-id="50e57-155">https://Contoso.sharepoint.com/sites/projectx devient https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="50e57-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="50e57-156">Pour commencer à déplacer le site, exécutez la cmdlet suivante :</span><span class="sxs-lookup"><span data-stu-id="50e57-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Capture d’écran de la fenêtre de PowerShell affichant la cmdlet Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="50e57-158">Démarrer un déplacement géographique de site SharePoint connecté à un groupe Office 365</span><span class="sxs-lookup"><span data-stu-id="50e57-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="50e57-159">Pour déplacer un site connecté à un groupe Office 365, l’administrateur général doit commencer par modifier l’attribut d’emplacement par défaut des données pour le groupe Office 365.</span><span class="sxs-lookup"><span data-stu-id="50e57-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="50e57-160">Pour définir l’emplacement par défaut des données pour un groupe Office 365 :</span><span class="sxs-lookup"><span data-stu-id="50e57-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="50e57-161">Une fois l’emplacement par défaut des données mis à jour, vous pouvez commencer à déplacer le site :</span><span class="sxs-lookup"><span data-stu-id="50e57-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="50e57-162">Annuler un déplacement géographique de site SharePoint</span><span class="sxs-lookup"><span data-stu-id="50e57-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="50e57-163">Vous pouvez arrêter un déplacement géographique de site OneDrive, à la condition que ce déplacement ne soit pas en cours ou terminé, en utilisant la cmdlet `Stop-SPOSiteContentMove` :</span><span class="sxs-lookup"><span data-stu-id="50e57-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="50e57-164">Détermination de l’état d’un déplacement géographique de site SharePoint</span><span class="sxs-lookup"><span data-stu-id="50e57-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="50e57-165">Vous pouvez déterminer l’état d’un déplacement de site hors de la zone géographique à laquelle vous êtes connecté à l’aide des cmdlets suivantes :</span><span class="sxs-lookup"><span data-stu-id="50e57-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="50e57-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (sites non connectés à un groupe)</span><span class="sxs-lookup"><span data-stu-id="50e57-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="50e57-167">Get-SPOUnifiedGroupMoveState (sites connectés à un groupe)</span><span class="sxs-lookup"><span data-stu-id="50e57-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="50e57-168">Pour spécifier le site dont vous voulez voir l’état de déplacement, utilisez le paramètre `-SourceSiteUrl`.</span><span class="sxs-lookup"><span data-stu-id="50e57-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="50e57-169">Les états de déplacement sont décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="50e57-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="50e57-170">Statut</span><span class="sxs-lookup"><span data-stu-id="50e57-170">Status</span></span>|<span data-ttu-id="50e57-171">Description</span><span class="sxs-lookup"><span data-stu-id="50e57-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="50e57-172">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="50e57-172">Ready to Trigger</span></span>|<span data-ttu-id="50e57-173">Le déplacement n’a pas commencé.</span><span class="sxs-lookup"><span data-stu-id="50e57-173">The move has not started.</span></span>|
|<span data-ttu-id="50e57-174">Scheduled</span><span class="sxs-lookup"><span data-stu-id="50e57-174">Scheduled</span></span>|<span data-ttu-id="50e57-175">Le déplacement est en file d’attente mais n’a pas encore commencé.</span><span class="sxs-lookup"><span data-stu-id="50e57-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="50e57-176">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="50e57-176">InProgress (n/4)</span></span>|<span data-ttu-id="50e57-177">Le déplacement est en cours dans l’un des états suivants : Validation (1/4), Sauvegarde (2/4), Restauration (3/4), Nettoyage (4/4).</span><span class="sxs-lookup"><span data-stu-id="50e57-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="50e57-178">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="50e57-178">Success</span></span>|<span data-ttu-id="50e57-179">Le déplacement a réussi.</span><span class="sxs-lookup"><span data-stu-id="50e57-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="50e57-180">Échec</span><span class="sxs-lookup"><span data-stu-id="50e57-180">Failed</span></span>|<span data-ttu-id="50e57-181">Le déplacement a échoué.</span><span class="sxs-lookup"><span data-stu-id="50e57-181">The move failed.</span></span>|

<span data-ttu-id="50e57-182">Vous pouvez également appliquer l’option `-Verbose` pour voir des informations supplémentaires sur le déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="50e57-183">Expérience utilisateur</span><span class="sxs-lookup"><span data-stu-id="50e57-183">User experience</span></span>

<span data-ttu-id="50e57-184">Les utilisateurs du site devraient constater une perturbation minimale lors du déplacement géographique du site.</span><span class="sxs-lookup"><span data-stu-id="50e57-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="50e57-185">À l’exception d’un bref état en lecture seule lors du déplacement, les liens et autorisations existants continuent de fonctionner comme prévu après le déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="50e57-186">Site</span><span class="sxs-lookup"><span data-stu-id="50e57-186">Site</span></span>

<span data-ttu-id="50e57-187">Durant le déplacement, le site est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="50e57-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="50e57-188">Une fois le déplacement terminé, l’utilisateur est redirigé vers le nouveau site dans le nouvel emplacement géographique quand il clique sur des signets ou d’autres liens pointant sur le site.</span><span class="sxs-lookup"><span data-stu-id="50e57-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="50e57-189">Autorisations</span><span class="sxs-lookup"><span data-stu-id="50e57-189">Permissions</span></span>

<span data-ttu-id="50e57-190">Les utilisateurs disposant d’autorisations d’accès au site continuent de pouvoir y accéder durant et après le déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="50e57-191">Client de synchronisation</span><span class="sxs-lookup"><span data-stu-id="50e57-191">Sync Client</span></span>

<span data-ttu-id="50e57-192">Le client de synchronisation détecte et transfère automatiquement la synchronisation vers le nouvel emplacement du site une fois celui-ci déplacé.</span><span class="sxs-lookup"><span data-stu-id="50e57-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="50e57-193">L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer un autre action</span><span class="sxs-lookup"><span data-stu-id="50e57-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="50e57-194">(version 17.3.6943.0625 ou une version ultérieure du client de synchronisation requise).</span><span class="sxs-lookup"><span data-stu-id="50e57-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="50e57-195">Si un utilisateur met à jour un fichier pendant le déplacement, le client de synchronisation l’informe que les chargements de fichiers sont mis en attente pendant le déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="50e57-196">Partage des liens</span><span class="sxs-lookup"><span data-stu-id="50e57-196">Sharing links</span></span>

<span data-ttu-id="50e57-197">Une fois le déplacement géographique de site OneDrive terminé, les liens partagés existants vers les fichiers déplacés redirigent automatiquement vers le nouvel emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="50e57-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="50e57-198">Fichiers récents dans Office</span><span class="sxs-lookup"><span data-stu-id="50e57-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="50e57-199">Une fois le déplacement terminé, le service Fichiers récents est mis à jour avec l’URL du site et les URL de son contenu.</span><span class="sxs-lookup"><span data-stu-id="50e57-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="50e57-200">Cela vaut pour Word, Excel et PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="50e57-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="50e57-201">Expérience OneNote</span><span class="sxs-lookup"><span data-stu-id="50e57-201">OneNote experience</span></span>

<span data-ttu-id="50e57-202">Le client OneNote Win32 et l’application UWP (plateforme Windows universelle) détectent et synchronisent automatiquement et sans difficulté les blocs-notes sur le nouvel emplacement du site une fois celui-ci déplacé.</span><span class="sxs-lookup"><span data-stu-id="50e57-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="50e57-203">L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer un autre action.</span><span class="sxs-lookup"><span data-stu-id="50e57-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="50e57-204">Le seul indicateur pour l’utilisateur est un échec éventuel de synchronisation de bloc-notes durant le déplacement du site.</span><span class="sxs-lookup"><span data-stu-id="50e57-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="50e57-205">Cette expérience est disponible sur les versions suivantes du client OneNote :</span><span class="sxs-lookup"><span data-stu-id="50e57-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="50e57-206">OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="50e57-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="50e57-207">OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="50e57-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="50e57-208">Application mobile OneNote : Version 16.0.8431.1011 (et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="50e57-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="50e57-209">Microsoft Teams (applicable aux sites connectés à un groupe Office 365)</span><span class="sxs-lookup"><span data-stu-id="50e57-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="50e57-210">Une fois le déplacement géographique de site SharePoint terminé, les utilisateurs ont accès aux fichiers du site de groupe Office 365 sur leur application Teams.</span><span class="sxs-lookup"><span data-stu-id="50e57-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="50e57-211">Par ailleurs, les fichiers partagés via une conversation Teams à partir de leur site avant le déplacement géographique continuent également de fonctionner après le déplacement.</span><span class="sxs-lookup"><span data-stu-id="50e57-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="50e57-212">Application SharePoint Mobile (iOS/Android)</span><span class="sxs-lookup"><span data-stu-id="50e57-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="50e57-213">L’application SharePoint Mobile étant inter-géographique, elle est capable de détecter le nouvel emplacement géographique du site.</span><span class="sxs-lookup"><span data-stu-id="50e57-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="50e57-214">Flux de travail SharePoint</span><span class="sxs-lookup"><span data-stu-id="50e57-214">SharePoint workflows</span></span>

<span data-ttu-id="50e57-215">Les flux de travail SharePoint 2013 doivent être republiés une fois le site déplacé.</span><span class="sxs-lookup"><span data-stu-id="50e57-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="50e57-216">Les flux de travail SharePoint 2010 devraient continuer de fonctionner normalement.</span><span class="sxs-lookup"><span data-stu-id="50e57-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="50e57-217">Applications</span><span class="sxs-lookup"><span data-stu-id="50e57-217">Apps</span></span>

<span data-ttu-id="50e57-218">Si vous migrez un site comportant des applications, vous devez ré-instancier celles-ci dans le nouvel emplacement géographique du site, car les applications et leurs liens pourraient ne pas être disponibles dans l’emplacement géographique cible.</span><span class="sxs-lookup"><span data-stu-id="50e57-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="50e57-219">Flux</span><span class="sxs-lookup"><span data-stu-id="50e57-219">Flow</span></span>

<span data-ttu-id="50e57-220">Dans la plupart des cas, les flux continueront de fonctionner après un déplacement géographique de site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="50e57-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="50e57-221">Nous vous conseillons de les tester une fois le déplacement terminé.</span><span class="sxs-lookup"><span data-stu-id="50e57-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="50e57-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="50e57-222">PowerApps</span></span>

<span data-ttu-id="50e57-223">Les applications PowerApps doivent être recréées dans l’emplacement cible.</span><span class="sxs-lookup"><span data-stu-id="50e57-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="50e57-224">Déplacement de données entre emplacements géographiques</span><span class="sxs-lookup"><span data-stu-id="50e57-224">Data movement between geo locations</span></span>

<span data-ttu-id="50e57-225">SharePoint utilise Stockage Blob Azure pour son contenu, tandis que les métadonnées associés à des sites et à ses fichiers sont stockées dans SharePoint.</span><span class="sxs-lookup"><span data-stu-id="50e57-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="50e57-226">Le déplacement du site de son emplacement géographique source vers son emplacement géographique cible implique également le déplacement de son Stockage Blob.</span><span class="sxs-lookup"><span data-stu-id="50e57-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="50e57-227">Le déplacement du Stockage Blob prend environ 40 jours.</span><span class="sxs-lookup"><span data-stu-id="50e57-227">Blob Storage moves complete in approximately 40 days.</span></span> 
