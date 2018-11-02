---
title: Configuration du client OneDrive Entreprise Multi-Géo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Découvrez comment configurer OneDrive Entreprise Multi-Géo.
ms.openlocfilehash: 6c4a1012f3f26265ef88d82c55bb3ac11cc82da4
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849870"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="d9ca4-103">Configuration du client OneDrive Entreprise Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="d9ca4-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="d9ca4-p101">Avant de configurer votre client OneDrive Entreprise Multi-Géo, reportez-vous à l’article relatif à la [planification de OneDrive Entreprise Multi-Géo](plan-for-multi-geo.md). Pour suivre la procédure décrite dans cet article, vous devez disposer de la liste des emplacements géographiques que vous souhaitez activer en tant qu’emplacements satellites et des utilisateurs test que vous souhaitez configurer pour ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="d9ca4-106">Ajouter les fonctionnalités multigéographiques du plan Office 365 à votre client</span><span class="sxs-lookup"><span data-stu-id="d9ca4-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="d9ca4-p102">Pour utiliser OneDrive Entreprise Multi-Géo, vous devez disposer du plan des _fonctionnalités multigéographiques dans Office 365_. Collaborez avec votre équipe de compte pour ajouter ce plan à votre client. Votre équipe de compte vous connectera avec le spécialiste de la licence approprié et configurera votre client.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="d9ca4-p103">Notez que le plan des _fonctionnalités multigéographiques dans Office 365_ est un plan de service au niveau utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement satellite. Vous pouvez ajouter des licences supplémentaires au fur et à mesure que vous ajoutez des utilisateurs dans des emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="d9ca4-113">Une fois que votre client a été configuré avec le plan des _fonctionnalités multigéographiques dans Office 365_, l’onglet **Emplacements géographiques** devient disponible dans le [centre d’administration OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="d9ca4-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="d9ca4-114">Ajouter des emplacements satellites à votre client</span><span class="sxs-lookup"><span data-stu-id="d9ca4-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="d9ca4-p104">Vous devez ajouter un emplacement satellite pour chaque emplacement géographique où vous souhaitez utiliser OneDrive Entreprise. Les emplacements géographiques disponibles sont affichés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d9ca4-117"><strong>Emplacement</strong></span><span class="sxs-lookup"><span data-stu-id="d9ca4-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="d9ca4-118"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="d9ca4-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d9ca4-119">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="d9ca4-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-120">APC</span><span class="sxs-lookup"><span data-stu-id="d9ca4-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9ca4-121">Australie</span><span class="sxs-lookup"><span data-stu-id="d9ca4-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-122">AUS</span><span class="sxs-lookup"><span data-stu-id="d9ca4-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9ca4-123">Canada</span><span class="sxs-lookup"><span data-stu-id="d9ca4-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-124">CAN</span><span class="sxs-lookup"><span data-stu-id="d9ca4-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9ca4-125">Europe / Moyen-Orient / Afrique</span><span class="sxs-lookup"><span data-stu-id="d9ca4-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-126">EUR</span><span class="sxs-lookup"><span data-stu-id="d9ca4-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9ca4-127">France</span><span class="sxs-lookup"><span data-stu-id="d9ca4-127">France</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-128">FRA</span><span class="sxs-lookup"><span data-stu-id="d9ca4-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9ca4-129">Japon</span><span class="sxs-lookup"><span data-stu-id="d9ca4-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-130">JPN</span><span class="sxs-lookup"><span data-stu-id="d9ca4-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9ca4-131">Corée</span><span class="sxs-lookup"><span data-stu-id="d9ca4-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-132">KOR</span><span class="sxs-lookup"><span data-stu-id="d9ca4-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9ca4-133">Amérique du Nord</span><span class="sxs-lookup"><span data-stu-id="d9ca4-133">North America</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-134">NAM</span><span class="sxs-lookup"><span data-stu-id="d9ca4-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9ca4-135">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="d9ca4-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="d9ca4-136">GBR</span><span class="sxs-lookup"><span data-stu-id="d9ca4-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d9ca4-137">Pour ajouter un emplacement satellite, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d9ca4-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="d9ca4-138">Ouvrez le [centre d’administration OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="d9ca4-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="d9ca4-139">Accédez à l’onglet **Emplacements géographiques**.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="d9ca4-140">Cliquez sur **Ajouter un emplacement**.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-140">Click **Add location**.</span></span>

4. <span data-ttu-id="d9ca4-141">Sélectionnez l’emplacement à ajouter, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="d9ca4-142">Saisissez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="d9ca4-143">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-143">Click **Close**.</span></span>

<span data-ttu-id="d9ca4-p105">La configuration peut prendre jusqu’à 72 heures selon la taille de votre client. Une fois que la configuration d’un emplacement satellite est terminée, vous recevrez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte sur l’onglet **Emplacements géographiques** dans le centre d’administration OneDrive, vous pouvez définir l’emplacement des données par défaut des utilisateurs sur cet emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d9ca4-p106">Votre nouvel emplacement satellite est configuré avec des paramètres par défaut. Cela vous permettra de configurer cet emplacement satellite en fonction de vos besoins de conformité locale.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="d9ca4-149">Définition de l’emplacement des données par défaut des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d9ca4-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="d9ca4-p107">Lorsque vous activez les emplacements satellites nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données par défaut approprié. Nous vous recommandons de définir un emplacement de données par défaut pour chaque utilisateur, même si cet utilisateur reste dans l’emplacement central.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="d9ca4-152">Nous vous recommandons de commencer les validations avec un utilisateur test ou un petit groupe d’utilisateurs avant de déployer Multi-Géo sur votre organisation à plus grande échelle.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="d9ca4-p108">Dans AAD, il existe deux types d’objets utilisateur : les utilisateurs cloud uniquement et les utilisateurs synchronisés. Suivez les instructions correspondant à votre type d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="d9ca4-155">Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide d’AD Connect</span><span class="sxs-lookup"><span data-stu-id="d9ca4-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="d9ca4-p109">Si les utilisateurs de votre entreprise sont synchronisés à partir d’un système Active Directory local avec Azure Active Directory, leur PreferredDataLocation doit être renseigné dans AD et synchronisé avec AAD. Suivez le processus décrit dans l’article [Synchronisation Azure AD Connect : modifier la configuration par défaut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) pour configurer la synchronisation de l’emplacement des données par défaut à partir d’Active Directory local avec Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="d9ca4-158">Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9ca4-p110">Pour les nouveaux utilisateurs sans OneDrive configuré, patientez au moins 24 heures après la synchronisation de l’emplacement des données par défaut d’un utilisateur avec Azure Active Directory pour que les modifications se propagent avant que l’utilisateur se connecte à OneDrive Entreprise. (La définition de l’emplacement des données par défaut avant la connexion de l’utilisateur pour configurer OneDrive Entreprise garantit que le nouveau OneDrive sera configuré à l’emplacement approprié.)</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="d9ca4-161">Définition de l’emplacement des données par défaut pour les utilisateurs cloud uniquement</span><span class="sxs-lookup"><span data-stu-id="d9ca4-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="d9ca4-162">Si les utilisateurs de votre entreprise ne sont pas synchronisés à partir d’un système Active Directory local avec Azure Active Directory, ce qui signifie qu’ils sont créés dans Office 365 ou Azure Active Directory, l’emplacement des données par défaut doit être défini à l’aide d’Azure Active Directory pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="d9ca4-p111">Les procédures décrites dans cette section nécessitent le [module Microsoft Azure Active Directory Module pour Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si vous avez déjà installé Azure Active Directory pour PowerShell, vérifiez que vous effectuez la mise à jour vers la dernière version.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="d9ca4-165">Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="d9ca4-166">Exécutez `Connect-MsolService` et entrez les informations d’identification d’administrateur général pour votre client.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="d9ca4-p112">Utilisez la cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) pour définir l’emplacement des données par défaut pour chacun de vos utilisateurs. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="d9ca4-p113">Vous pouvez vérifier pour confirmer que l’emplacement des données par défaut a été correctement mis à jour à l’aide de la cmdlet Get-MsolUser. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="d9ca4-171">Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9ca4-p114">Pour les nouveaux utilisateurs sans OneDrive configuré, patientez au moins 24 heures après la définition de l’emplacement des données par défaut d’un utilisateur pour que les modifications se propagent avant que l’utilisateur se connecte à OneDrive. (La définition de l’emplacement des données par défaut avant la connexion de l’utilisateur pour configurer OneDrive Entreprise garantit que le nouveau OneDrive sera configuré à l’emplacement approprié.)</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="d9ca4-174">Configuration de OneDrive et l’effet de PDL</span><span class="sxs-lookup"><span data-stu-id="d9ca4-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="d9ca4-p115">Si l’utilisateur possède déjà un site OneDrive créé dans le client, la définition de son PDL ne déplacera pas automatiquement son OneDrive existant. Pour déplacer le site OneDrive d’un utilisateur, reportez-vous à l’article relatif au [déplacement géographique de OneDrive Entreprise](move-onedrive-between-geo-locations.md) et suivez les instructions relatives au déplacement de OneDrive entre des emplacements géographiques.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="d9ca4-177">Si l’utilisateur ne dispose pas d’un site OneDrive dans le client, OneDrive sera configuré pour lui conformément à sa valeur PDL, en supposant que le PDL pour l’utilisateur correspond à l’un des emplacements satellites de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="d9ca4-178">Configuration de la recherche Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="d9ca4-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="d9ca4-179">Votre client Multi-Géo aura des fonctionnalités de recherche regroupées permettant à une requête de recherche de renvoyer des résultats de n’importe quel endroit dans le client.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="d9ca4-180">Par défaut, les recherches effectuées à partir de ces points d’entrée renvoient des résultats regroupés, bien que chaque index de recherche se trouve dans son emplacement géographique approprié :</span><span class="sxs-lookup"><span data-stu-id="d9ca4-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="d9ca4-181">OneDrive Entreprise</span><span class="sxs-lookup"><span data-stu-id="d9ca4-181">OneDrive for business</span></span>

- <span data-ttu-id="d9ca4-182">Delve</span><span class="sxs-lookup"><span data-stu-id="d9ca4-182">Delve</span></span>

- <span data-ttu-id="d9ca4-183">Page d’accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="d9ca4-183">SharePoint Home</span></span>

- <span data-ttu-id="d9ca4-184">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="d9ca4-184">Search Center</span></span>

<span data-ttu-id="d9ca4-185">Par ailleurs, les fonctionnalités de recherche Multi-Géo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent l’API de recherche SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="d9ca4-186">Consultez [Configurer la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris des informations sur les limitations et les différences.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="d9ca4-187">Validation de la configuration de OneDrive Entreprise Multi-Géo</span><span class="sxs-lookup"><span data-stu-id="d9ca4-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="d9ca4-p116">Vous trouverez ci-dessous des cas d’utilisation de base que vous pouvez inclure dans votre plan de validation avant de déployer OneDrive Entreprise Multi-Géo à grande échelle. Une fois que vous avez terminé ces tests et les cas d’utilisation supplémentaires adaptés à votre entreprise, vous pouvez ajouter les utilisateurs dans votre groupe pilote initial.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="d9ca4-190">**OneDrive Entreprise**</span><span class="sxs-lookup"><span data-stu-id="d9ca4-190">**OneDrive for Business**</span></span>

<span data-ttu-id="d9ca4-p117">Sélectionnez OneDrive à partir du lanceur d’applications Office 365 et confirmez que vous êtes automatiquement dirigé vers l’emplacement géographique approprié pour l’utilisateur, en fonction du PDL de l’utilisateur. OneDrive Entreprise doit à présent commencer la configuration à cet emplacement. Une fois la configuration terminée, essayez de charger et télécharger certains documents.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="d9ca4-194">**Application mobile OneDrive**</span><span class="sxs-lookup"><span data-stu-id="d9ca4-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="d9ca4-p118">Connectez-vous à votre application mobile OneDrive avec vos informations d’identification de compte test. Confirmez que vous pouvez voir vos fichiers OneDrive Entreprise et que vous pouvez interagir avec eux à partir de votre appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="d9ca4-197">**Client de synchronisation OneDrive**</span><span class="sxs-lookup"><span data-stu-id="d9ca4-197">**OneDrive sync client**</span></span>

<span data-ttu-id="d9ca4-p119">Vérifiez que le client de synchronisation OneDrive détecte automatiquement l’emplacement géographique de OneDrive Entreprise dès la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **Synchroniser** dans la bibliothèque OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="d9ca4-200">**Applications Office**</span><span class="sxs-lookup"><span data-stu-id="d9ca4-200">**Office applications**</span></span>

<span data-ttu-id="d9ca4-p120">Confirmez que vous pouvez utiliser OneDrive Entreprise en vous connectant à partir d’une application Office, telle que Word. Ouvrez l’application Office, puis sélectionnez « OneDrive- <TenantName> ». Office détecte votre emplacement OneDrive et affiche les fichiers que vous pouvez ouvrir.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="d9ca4-204">**Partage**</span><span class="sxs-lookup"><span data-stu-id="d9ca4-204">**Sharing**</span></span>

<span data-ttu-id="d9ca4-p121">Essayez de partager des fichiers OneDrive. Vérifiez que le sélecteur de personnes affiche tous vos utilisateurs SharePoint en ligne indépendamment de leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="d9ca4-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
