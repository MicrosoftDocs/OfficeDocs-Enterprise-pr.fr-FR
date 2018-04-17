---
title: OneDrive pour la configuration des clients Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Apprenez à configurer les OneDrive d’entreprise Multi-Geo.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="be165-103">OneDrive pour la configuration des clients Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="be165-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="be165-p101">Avant de configurer vos clients pour OneDrive pour entreprise Multi-Geo, veillez à ce que vous avez lu le [Plan pour OneDrive pour entreprise Multi-Geo](plan-for-multi-geo.md). Pour suivre les étapes décrites dans cet article, vous aurez besoin d’une liste des emplacements que vous souhaitez activer les utilisateurs de test que vous souhaitez configurer pour ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="be165-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="be165-106">Ajouter les fonctionnalités Multi-Geo dans Office 365 plan pour vos clients</span><span class="sxs-lookup"><span data-stu-id="be165-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="be165-p102">Pour utiliser OneDrive pour entreprise Multi-Geo, vous devez le plan de _Capacités Multi-Geo dans Office 365_ . Travailler avec votre équipe de compte à ajouter ce plan pour vos clients. Votre équipe de compte va vous connecter avec le spécialiste de la licence approprié et obtenir vos clients configurés.</span><span class="sxs-lookup"><span data-stu-id="be165-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="be165-p103">Notez que le plan _Des fonctionnalités dans Office 365 Multi-Geo_ est un plan de service au niveau de l’utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement de satellite. Vous pouvez ajouter davantage de licences lorsque vous ajoutez des utilisateurs dans des emplacements de satellite au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="be165-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="be165-113">Une fois que votre client a été configuré avec le plan de _Capacités Multi-Geo dans Office 365_ , l’onglet **emplacements de la zone géographique** devient disponible dans le [Centre d’administration OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="be165-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="be165-114">Définir les emplacements de données autorisé (ADL) à vos clients</span><span class="sxs-lookup"><span data-stu-id="be165-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="be165-p104">Vous devez définir un emplacement de données autorisées pour SharePoint pour chaque emplacement géographique où vous souhaitez utiliser OneDrive pour les entreprises. Geo-emplacements disponibles sont affichés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="be165-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="be165-117"><strong>Emplacement</strong></span><span class="sxs-lookup"><span data-stu-id="be165-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="be165-118"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="be165-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="be165-119">Amérique du Nord</span><span class="sxs-lookup"><span data-stu-id="be165-119">North America</span></span></td>
<td align="left"><span data-ttu-id="be165-120">NAM</span><span class="sxs-lookup"><span data-stu-id="be165-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="be165-121">Europe / Moyen-Orient / Afrique</span><span class="sxs-lookup"><span data-stu-id="be165-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="be165-122">EUROS</span><span class="sxs-lookup"><span data-stu-id="be165-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="be165-123">Asie-Pacifique</span><span class="sxs-lookup"><span data-stu-id="be165-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="be165-124">APC</span><span class="sxs-lookup"><span data-stu-id="be165-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="be165-125">Australie</span><span class="sxs-lookup"><span data-stu-id="be165-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="be165-126">AUSTRALIE</span><span class="sxs-lookup"><span data-stu-id="be165-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="be165-127">Japon</span><span class="sxs-lookup"><span data-stu-id="be165-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="be165-128">JPN</span><span class="sxs-lookup"><span data-stu-id="be165-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="be165-129">Canada</span><span class="sxs-lookup"><span data-stu-id="be165-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="be165-130">POUVEZ</span><span class="sxs-lookup"><span data-stu-id="be165-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="be165-131">Royaume-Uni</span><span class="sxs-lookup"><span data-stu-id="be165-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="be165-132">GBR</span><span class="sxs-lookup"><span data-stu-id="be165-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="be165-133">Corée</span><span class="sxs-lookup"><span data-stu-id="be165-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="be165-134">KOR</span><span class="sxs-lookup"><span data-stu-id="be165-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="be165-135">Pour ajouter un emplacement géographique de satellite</span><span class="sxs-lookup"><span data-stu-id="be165-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="be165-136">Ouvrir le [Centre d’administration OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="be165-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="be165-137">Accédez à l’onglet **emplacements de la zone géographique** .</span><span class="sxs-lookup"><span data-stu-id="be165-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="be165-138">Cliquez sur **Ajouter un emplacement**.</span><span class="sxs-lookup"><span data-stu-id="be165-138">Click **Add location**.</span></span>

4. <span data-ttu-id="be165-139">Sélectionnez l’emplacement où vous souhaitez ajouter, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="be165-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="be165-140">Tapez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="be165-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="be165-141">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="be165-141">Click **Close**.</span></span>

<span data-ttu-id="be165-p105">Mise en service peut prendre de quelques heures à 72 heures, en fonction de la taille de vos clients. Une fois la mise en service d’un emplacement de satellite est terminée, vous recevrez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte dans l’onglet **emplacements de la zone géographique** dans le centre d’administration OneDrive, vous pourrez définir l’emplacement de données par défaut des utilisateurs à cet emplacement-geo.</span><span class="sxs-lookup"><span data-stu-id="be165-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="be165-p106">Votre nouvel emplacement géographique de satellites est établi avec les paramètres par défaut. Cela vous permettra de configurer cet emplacement géographique en fonction de vos besoins de conformité locale.</span><span class="sxs-lookup"><span data-stu-id="be165-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="be165-147">Définition de l’emplacement par défaut des données utilisateurs</span><span class="sxs-lookup"><span data-stu-id="be165-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="be165-p107">Une fois que vous activez les emplacements de données nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données approprié. Nous vous conseillons de définir un emplacement de données par défaut pour tous les utilisateurs, même si cet utilisateur séjourne dans l’emplacement de données par défaut.</span><span class="sxs-lookup"><span data-stu-id="be165-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="be165-150">Nous vous conseillons de commencer les validations avec un petit groupe d’utilisateurs ou un utilisateur de test avant de déployer les fonctionnalités Multi-Geo à votre organisation plus large.</span><span class="sxs-lookup"><span data-stu-id="be165-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="be165-p108">Dans DAS, il existe deux types d’objets de l’utilisateur : cloud uniquement aux utilisateurs et synchronisé. Suivez les instructions correspondant à votre type d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="be165-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="be165-153">Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide de la connexion d’Active Directory</span><span class="sxs-lookup"><span data-stu-id="be165-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="be165-p109">Si les utilisateurs de votre entreprise sont synchronisées à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), leur PreferredDataLocation doit être remplie dans Active Directory et synchronisée avec DAS. Suivez le processus de [Azure Connect de AD sync : apporter une modification à la configuration par défaut](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) pour configurer par défaut synchronisation de l’emplacement des données de sur site AD pour le DAS.</span><span class="sxs-lookup"><span data-stu-id="be165-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="be165-156">Nous vous conseillons d’inclure définissant l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="be165-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be165-p110">Pour les nouveaux utilisateurs avec aucun OneDrive mis en service, attendez au moins 24 heures après que le langage PDL d’un utilisateur est synchronisé avec DAS pour que les modifications de se propager avant que l’utilisateur se connecte à OneDrive pour les entreprises. (Définition des données par défaut emplacement avant que l’utilisateur se connecte à provisionner leur OneDrive pour les entreprises ainsi que OneDrive de nouveau l’utilisateur sera déployé dans l’emplacement correct).</span><span class="sxs-lookup"><span data-stu-id="be165-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="be165-159">Définition de l’emplacement de données par défaut pour le cloud uniquement les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="be165-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="be165-160">Si les utilisateurs de votre société ne sont pas synchronisés à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), c'est-à-dire qu’ils sont créés dans Office 365 ou DAS, puis PDL doit être défini à l’aide de PowerShell de DAS.</span><span class="sxs-lookup"><span data-stu-id="be165-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="be165-p111">Les procédures de cette section nécessitent le [Microsoft Azure Active Directory pour Windows PowerShell un Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si vous avez déjà PowerShell DAS installé, vérifiez que vous mettez à jour vers la dernière version.</span><span class="sxs-lookup"><span data-stu-id="be165-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="be165-163">Ouvrez le Module de Active Directory de Microsoft Azure pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be165-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="be165-164">Exécutez `Connect-MsolService` et entrez les informations d’identification de l’administrateur global pour vos clients.</span><span class="sxs-lookup"><span data-stu-id="be165-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="be165-p112">L’applet de commande [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) permet de définir l’emplacement de données par défaut pour chacun de vos utilisateurs. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="be165-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="be165-p113">Vous pouvez vérifier pour vous assurer que l’emplacement par défaut des données a été correctement mis à jour à l’aide de l’applet de commande Get-MsolUser. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="be165-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="be165-169">Nous vous conseillons d’inclure définissant l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="be165-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be165-p114">Pour les nouveaux utilisateurs avec aucun OneDrive mis en service, attendez au moins 24 heures après que PDL l’utilisateur est défini pour que les modifications de se propager avant que l’utilisateur se connecte à SharePoint OneDrive. (Définition des données par défaut emplacement avant que l’utilisateur se connecte à provisionner leur OneDrive pour les entreprises ainsi que OneDrive de nouveau l’utilisateur sera déployé dans l’emplacement correct).</span><span class="sxs-lookup"><span data-stu-id="be165-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="be165-172">Mise en service de la OneDrive et l’effet du langage PDL</span><span class="sxs-lookup"><span data-stu-id="be165-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="be165-p115">Si l’utilisateur possède déjà un site de OneDrive créé sur le client, définissant leur PDL pas déplace automatiquement leur OneDrive existant. Pour déplacer les OneDrive d’un utilisateur, consultez [OneDrive pour déplacer de Business géo](move-onedrive-between-geo-locations.md) , suivez les instructions de OneDrive de déplacement entre les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="be165-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="be165-175">Si l’utilisateur n’a pas un site de OneDrive dans le locataire, OneDrive sera déployé pour eux conformément à leur valeur PDL, en supposant le langage PDL pour l’utilisateur correspond à un des emplacements de données autorisé de la société (ADLs).</span><span class="sxs-lookup"><span data-stu-id="be165-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="be165-176">Configuration de la recherche de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="be165-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="be165-177">Vos clients Multi-Geo aient des fonctions de recherche d’agrégation permettant à une requête de recherche pour retourner les résultats de n’importe où dans le locataire.</span><span class="sxs-lookup"><span data-stu-id="be165-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="be165-178">Par défaut, les recherches à partir de ces points d’entrée renvoie des résultats de regroupement, même si chaque index de recherche se trouve dans son emplacement géographique appropriée :</span><span class="sxs-lookup"><span data-stu-id="be165-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="be165-179">OneDrive pour les entreprises</span><span class="sxs-lookup"><span data-stu-id="be165-179">OneDrive for business</span></span>

- <span data-ttu-id="be165-180">Delve</span><span class="sxs-lookup"><span data-stu-id="be165-180">Delve</span></span>

- <span data-ttu-id="be165-181">Accueil SharePoint</span><span class="sxs-lookup"><span data-stu-id="be165-181">SharePoint Home</span></span>

- <span data-ttu-id="be165-182">Centre de recherche</span><span class="sxs-lookup"><span data-stu-id="be165-182">Search Center</span></span>

<span data-ttu-id="be165-183">En outre, les fonctionnalités de recherche Multi-Geo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent le API de recherche de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="be165-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="be165-184">Consultez [Configurer la recherche de OneDrive de professionnels Multi-Geo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris les limitations et les différences.</span><span class="sxs-lookup"><span data-stu-id="be165-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="be165-185">Validation de l’OneDrive pour la configuration de Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="be165-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="be165-p116">Vous trouverez ci-dessous quelques exemples d’utilisation de base que vous voudrez peut-être inclure dans votre plan de validation avant le large déploiement OneDrive pour entreprise Multi-Geo à votre société. Une fois que vous avez terminé ces tests et les cas d’usage supplémentaires qui sont pertinentes pour votre société, vous pouvez choisir passer à l’ajout d’utilisateurs dans votre groupe pilote initial.</span><span class="sxs-lookup"><span data-stu-id="be165-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="be165-188">**OneDrive pour les entreprises**</span><span class="sxs-lookup"><span data-stu-id="be165-188">**OneDrive for Business**</span></span>

<span data-ttu-id="be165-p117">Sélectionnez OneDrive à partir du Lanceur d’applications Office 365 et de confirmer que vous êtes automatiquement redirigé vers l’emplacement approprié du géographique de l’utilisateur, en fonction de PDL l’utilisateur. OneDrive pour l’entreprise doit maintenant commencer la mise en service à cet emplacement. Essayez une fois configuré, de transfert et le téléchargement de certains documents.</span><span class="sxs-lookup"><span data-stu-id="be165-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="be165-192">**Application de OneDrive Mobile**</span><span class="sxs-lookup"><span data-stu-id="be165-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="be165-p118">Ouvrez une session dans votre application mobile de OneDrive avec vos informations d’identification du compte de test. Vérifiez que vous pouvez voir votre OneDrive pour les fichiers de l’entreprise et pouvez interagir avec eux à partir de votre appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="be165-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="be165-195">**Client de synchronisation OneDrive**</span><span class="sxs-lookup"><span data-stu-id="be165-195">**OneDrive sync client**</span></span>

<span data-ttu-id="be165-p119">Vérifiez que le client de synchronisation OneDrive détecte automatiquement votre OneDrive de géolocalisation métier lors de la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **synchroniser** dans la bibliothèque OneDrive.</span><span class="sxs-lookup"><span data-stu-id="be165-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="be165-198">**Applications Office**</span><span class="sxs-lookup"><span data-stu-id="be165-198">**Office applications**</span></span>

<span data-ttu-id="be165-p120">Vérifiez que vous pouvez accéder à OneDrive pour l’entreprise en vous connectant à partir d’une application Office, tels que Word. Ouvrir l’Office application et sélectionnez « OneDrive – <TenantName>». Office détecte votre emplacement de OneDrive et vous montrer que vous pouvez ouvrir les fichiers.</span><span class="sxs-lookup"><span data-stu-id="be165-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="be165-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="be165-202">**Sharing**</span></span>

<span data-ttu-id="be165-p121">Essayez de partager des fichiers de OneDrive. Vérifiez que le sélecteur de personnes contient tous vos utilisateurs d’en ligne SharePoint, quel que soit leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="be165-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
