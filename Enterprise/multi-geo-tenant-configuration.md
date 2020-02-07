---
title: Configuration du client Office 365 multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Découvrez la procédure de configuration d’Office 365 multigéographique.
ms.openlocfilehash: 6768aaa552ee75bb5dad523df0efc2384f0241ee
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844605"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="22aaf-103">Configuration du client Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="22aaf-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="22aaf-104">Avant de configurer votre client pour Office 365 multigéographique, veillez à consulter l’[Offre pour Office 365 multigéographique](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="22aaf-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="22aaf-105">Pour suivre la procédure décrite dans cet article, vous devez posséder la liste des emplacements géographiques que vous voulez activer en tant qu’emplacements satellites, ainsi que la liste des utilisateurs de test que vous désirez approvisionner à ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="22aaf-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="22aaf-106">Ajouter les fonctionnalités multigéographiques de l’offre Office 365 à votre client</span><span class="sxs-lookup"><span data-stu-id="22aaf-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="22aaf-107">Pour utiliser Office 365 multigéographique, vous devez posséder l’offre _Fonctionnalités multigéographiques dans Office 365_.</span><span class="sxs-lookup"><span data-stu-id="22aaf-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="22aaf-108">Travaillez avec votre équipe des comptes pour ajouter cette offre à votre client.</span><span class="sxs-lookup"><span data-stu-id="22aaf-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="22aaf-109">Votre équipe des comptes vous mettra en contact avec le spécialiste en gestion des licences approprié et votre client sera configuré.</span><span class="sxs-lookup"><span data-stu-id="22aaf-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="22aaf-p103">Notez que le plan des _fonctionnalités multigéographiques dans Office 365_ est un plan de service au niveau utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement satellite. Vous pouvez ajouter des licences supplémentaires au fur et à mesure que vous ajoutez des utilisateurs dans des emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="22aaf-113">Une fois que votre client a été approvisionné avec l’offre _Fonctionnalités multigéographiques dans Office 365_, l’onglet **Emplacements géographiques** est disponible dans les centres d’administration OneDrive et SharePoint.</span><span class="sxs-lookup"><span data-stu-id="22aaf-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="22aaf-114">Ajouter des emplacements satellites à votre client</span><span class="sxs-lookup"><span data-stu-id="22aaf-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="22aaf-115">Vous devez ajouter un emplacement satellite à chaque emplacement géographique où vous souhaitez stocker des données.</span><span class="sxs-lookup"><span data-stu-id="22aaf-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="22aaf-116">Le tableau suivant présente les emplacements géographiques disponibles :</span><span class="sxs-lookup"><span data-stu-id="22aaf-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Capture d’écran de la page des emplacements géographiques dans le Centre d’administration SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="22aaf-118">Pour ajouter un emplacement satellite</span><span class="sxs-lookup"><span data-stu-id="22aaf-118">To add a satellite location</span></span>

1. <span data-ttu-id="22aaf-119">Ouvrez le Centre d’administration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="22aaf-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="22aaf-120">Accédez à l’onglet **Emplacements géographiques**.</span><span class="sxs-lookup"><span data-stu-id="22aaf-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="22aaf-121">Cliquez sur **Ajouter un emplacement**.</span><span class="sxs-lookup"><span data-stu-id="22aaf-121">Click **Add location**.</span></span>

4. <span data-ttu-id="22aaf-122">Sélectionnez l’emplacement à ajouter, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22aaf-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="22aaf-123">Saisissez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="22aaf-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="22aaf-124">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="22aaf-124">Click **Close**.</span></span>

<span data-ttu-id="22aaf-p105">La configuration peut prendre jusqu’à 72 heures selon la taille de votre client. Une fois que la configuration d’un emplacement satellite est terminée, vous recevez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte sur l’onglet **Emplacements géographiques** dans le centre d’administration OneDrive, vous pouvez définir l’emplacement des données par défaut des utilisateurs sur cet emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="22aaf-p106">Votre nouvel emplacement satellite est configuré avec des paramètres par défaut. Cela vous permettra de configurer cet emplacement satellite en fonction de vos besoins de conformité locale.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="22aaf-130">Configuration de l’emplacement des données par défaut des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="22aaf-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="22aaf-p107">Lorsque vous activez les emplacements satellites nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données par défaut approprié. Nous vous recommandons de définir un emplacement de données par défaut pour chaque utilisateur, même si cet utilisateur reste dans l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22aaf-133">Si l’emplacement des données par défaut d’un utilisateur est défini sur un emplacement qui n’a pas été configuré en tant qu’emplacement satellite ou emplacement central, le système envoie les données par défaut vers l’emplacement central lorsqu’il approvisionne les sites OneDrive et SharePoint, ainsi que les boîtes aux lettres de groupe.</span><span class="sxs-lookup"><span data-stu-id="22aaf-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="22aaf-134">Nous vous recommandons de commencer les validations avec un utilisateur de test ou un petit groupe d’utilisateurs avant de déployer à plus grande échelle les fonctionnalités multigéographiques dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="22aaf-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="22aaf-135">Deux types d’objets utilisateur sont disponibles dans Azure Active Directory : les utilisateurs cloud uniquement et les utilisateurs synchronisés.</span><span class="sxs-lookup"><span data-stu-id="22aaf-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="22aaf-136">Suivez les instructions appropriées pour votre type d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="22aaf-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="22aaf-137">Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide d’Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="22aaf-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="22aaf-p109">Si les utilisateurs de votre entreprise sont synchronisés à partir d’un système Active Directory local avec Azure Active Directory, leur PreferredDataLocation doit être renseigné dans AD et synchronisé avec AAD. Suivez le processus décrit dans l’article [Synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) pour configurer la synchronisation de l’emplacement des données par défaut à partir d’Active Directory local avec Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="22aaf-140">Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="22aaf-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22aaf-141">Pour les nouveaux utilisateurs sans approvisionnement OneDrive, attendez au moins 24 heures après la synchronisation d’un emplacement des données par défaut de l’utilisateur avec Azure Active Directory pour que les changements soient appliqués avant que l’utilisateur ne se connecte à OneDrive Entreprise.</span><span class="sxs-lookup"><span data-stu-id="22aaf-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="22aaf-142">(Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)</span><span class="sxs-lookup"><span data-stu-id="22aaf-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="22aaf-143">Configurer l’emplacement des données par défaut pour les utilisateurs cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="22aaf-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="22aaf-144">Si les utilisateurs de votre entreprise ne sont pas synchronisés à partir d’un système Active Directory local avec Azure Active Directory, ce qui signifie qu’ils sont créés dans Office 365 ou Azure Active Directory, l’emplacement des données par défaut doit être défini à l’aide d’Azure Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22aaf-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="22aaf-p111">Les procédures décrites dans cette section nécessitent le [module Microsoft Azure Active Directory Module pour Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si vous avez déjà installé Azure Active Directory pour PowerShell, vérifiez que vous effectuez la mise à jour vers la dernière version.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="22aaf-147">Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22aaf-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="22aaf-148">Exécutez `Connect-MsolService` et entrez les informations d’identification d’administrateur général pour votre client.</span><span class="sxs-lookup"><span data-stu-id="22aaf-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="22aaf-p112">Utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) pour définir l’emplacement des données par défaut pour chacun de vos utilisateurs. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="22aaf-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="22aaf-p113">Vous pouvez vérifier pour confirmer que l’emplacement des données par défaut a été correctement mis à jour à l’aide de la cmdlet Get-MsolUser. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="22aaf-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Capture d’écran d’une fenêtre PowerShell affichant set-msoluser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="22aaf-154">Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="22aaf-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22aaf-155">Pour les nouveaux utilisateurs sans approvisionnement OneDrive, attendez au moins 24 heures après la configuration d’un emplacement des données par défaut de l’utilisateur pour que les changements soient appliqués avant que l’utilisateur ne se connecte à OneDrive.</span><span class="sxs-lookup"><span data-stu-id="22aaf-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="22aaf-156">(Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)</span><span class="sxs-lookup"><span data-stu-id="22aaf-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="22aaf-157">Configuration de OneDrive et l’effet de PDL</span><span class="sxs-lookup"><span data-stu-id="22aaf-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="22aaf-158">Si l’utilisateur possède déjà un site OneDrive créé dans le client, configurer son emplacement des données par défaut ne déplace pas automatiquement son OneDrive existant.</span><span class="sxs-lookup"><span data-stu-id="22aaf-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="22aaf-159">Pour déplacer le OneDrive d’un utilisateur, consultez [Déplacement de OneDrive Entreprise multigéographique](move-onedrive-between-geo-locations.md) et suivez les instructions permettant de déplacer OneDrive entre deux emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="22aaf-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="22aaf-160">(Notez que la boîte aux lettres Exchange de l’utilisateur ne se déplace automatiquement que lorsque vous configurez l’emplacement des données par défaut de l’utilisateur.)</span><span class="sxs-lookup"><span data-stu-id="22aaf-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="22aaf-161">Si l’utilisateur ne dispose pas d’un site OneDrive dans le client, OneDrive est approvisionné pour lui conformément à la valeur de son emplacement des données par défaut en supposant que ce dernier correspond à l’un des emplacements satellites de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="22aaf-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="22aaf-162">Configuration de la recherche Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="22aaf-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="22aaf-163">Votre client Multi-Géo aura des fonctionnalités de recherche regroupées permettant à une requête de recherche de renvoyer des résultats de n’importe quel endroit dans le client.</span><span class="sxs-lookup"><span data-stu-id="22aaf-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="22aaf-164">Par défaut, les recherches effectuées à partir de ces points d’entrée renvoient des résultats regroupés, bien que chaque index de recherche se trouve dans son emplacement géographique approprié :</span><span class="sxs-lookup"><span data-stu-id="22aaf-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="22aaf-165">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="22aaf-165">OneDrive for business</span></span>

- <span data-ttu-id="22aaf-166">Delve</span><span class="sxs-lookup"><span data-stu-id="22aaf-166">Delve</span></span>

- <span data-ttu-id="22aaf-167">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="22aaf-167">SharePoint Home</span></span>

- <span data-ttu-id="22aaf-168">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="22aaf-168">Search Center</span></span>

<span data-ttu-id="22aaf-169">Par ailleurs, les fonctionnalités de recherche Multi-Géo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent l’API de recherche SharePoint.</span><span class="sxs-lookup"><span data-stu-id="22aaf-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="22aaf-170">Consultez [Configurer la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris des informations sur les limitations et les différences.</span><span class="sxs-lookup"><span data-stu-id="22aaf-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="22aaf-171">Validation de la configuration d’Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="22aaf-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="22aaf-172">Voici certains cas d’utilisation de base que vous pourriez vouloir inclure dans votre plan de validation avant de déployer à grande échelle Office 365 multigéographique dans votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="22aaf-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="22aaf-173">Une fois que vous avez terminé ces tests et les cas d’utilisation supplémentaires éventuels et pertinents pour votre entreprise, vous pouvez choisir de commencer à ajouter des utilisateurs à votre groupe pilote initial.</span><span class="sxs-lookup"><span data-stu-id="22aaf-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="22aaf-174">**OneDrive Entreprise**</span><span class="sxs-lookup"><span data-stu-id="22aaf-174">**OneDrive for Business**</span></span>

<span data-ttu-id="22aaf-175">Sélectionnez OneDrive à partir du lanceur d’applications d’Office 365 et vérifiez que vous êtes automatiquement redirigé vers l’emplacement géographique approprié de l’utilisateur, conformément à l’emplacement des données par défaut de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="22aaf-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="22aaf-176">OneDrive Entreprise doit maintenant commencer à être approvisionné à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="22aaf-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="22aaf-177">Après l’approvisionnement, essayez de charger et de télécharger quelques documents.</span><span class="sxs-lookup"><span data-stu-id="22aaf-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="22aaf-178">**Application mobile OneDrive**</span><span class="sxs-lookup"><span data-stu-id="22aaf-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="22aaf-p118">Connectez-vous à votre application mobile OneDrive avec vos informations d’identification de compte test. Confirmez que vous pouvez voir vos fichiers OneDrive Entreprise et que vous pouvez interagir avec eux à partir de votre appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="22aaf-181">**Client de synchronisation OneDrive**</span><span class="sxs-lookup"><span data-stu-id="22aaf-181">**OneDrive sync client**</span></span>

<span data-ttu-id="22aaf-p119">Vérifiez que le client de synchronisation OneDrive détecte automatiquement l’emplacement géographique de OneDrive Entreprise dès la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **Synchroniser** dans la bibliothèque OneDrive.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="22aaf-184">**Applications Office**</span><span class="sxs-lookup"><span data-stu-id="22aaf-184">**Office applications**</span></span>

<span data-ttu-id="22aaf-p120">Confirmez que vous pouvez utiliser OneDrive Entreprise en vous connectant à partir d’une application Office, telle que Word. Ouvrez l’application Office, puis sélectionnez « OneDrive- <TenantName> ». Office détecte votre emplacement OneDrive et affiche les fichiers que vous pouvez ouvrir.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="22aaf-188">**Partage**</span><span class="sxs-lookup"><span data-stu-id="22aaf-188">**Sharing**</span></span>

<span data-ttu-id="22aaf-p121">Essayez de partager des fichiers OneDrive. Vérifiez que le sélecteur de personnes affiche tous vos utilisateurs SharePoint en ligne indépendamment de leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="22aaf-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
