---
title: Collaborer avec des invités dans un site
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Découvrez comment collaborer avec des invités sur un site SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017312"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="d9a11-103">Collaborer avec des invités dans un site</span><span class="sxs-lookup"><span data-stu-id="d9a11-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="d9a11-104">Si vous avez besoin de collaborer avec des invités dans des documents, des données et des listes, vous pouvez utiliser un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9a11-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="d9a11-105">Les sites SharePoint modernes sont connectés aux groupes Office 365 qui peuvent gérer l’appartenance à un site et fournir des outils de collaboration supplémentaires tels qu’une boîte aux lettres et un calendrier partagés.</span><span class="sxs-lookup"><span data-stu-id="d9a11-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="d9a11-106">Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer un site SharePoint en vue de la collaboration avec des invités.</span><span class="sxs-lookup"><span data-stu-id="d9a11-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="d9a11-107">Paramètres Azure de relations organisationnelles</span><span class="sxs-lookup"><span data-stu-id="d9a11-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="d9a11-108">Le partage dans Microsoft 365 est régi par les paramètres de relations organisationnelles dans Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d9a11-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="d9a11-109">Si le partage d’invités est désactivé ou restreint dans Azure AD, cela remplace tous les paramètres de partage que vous configurez dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d9a11-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="d9a11-110">Vérifiez les paramètres de relations organisationnelles pour vous assurer que le partage avec des invités n’est pas bloqué.</span><span class="sxs-lookup"><span data-stu-id="d9a11-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Capture d’écran de la page des paramètres des relations organisationnelles Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="d9a11-112">Pour définir les paramètres de relation organisationnelle</span><span class="sxs-lookup"><span data-stu-id="d9a11-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="d9a11-113">Connectez-vous à Microsoft Azure [https://portal.azure.com](https://portal.azure.com)à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="d9a11-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="d9a11-114">Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="d9a11-115">Dans le volet de **vue d’ensemble** , cliquez sur **relations organisationnelles**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="d9a11-116">Dans le volet **relations organisationnelles** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="d9a11-117">Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="d9a11-118">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="d9a11-119">Notez les paramètres dans la section **restrictions de collaboration** .</span><span class="sxs-lookup"><span data-stu-id="d9a11-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="d9a11-120">Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.</span><span class="sxs-lookup"><span data-stu-id="d9a11-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="d9a11-121">Les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="d9a11-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="d9a11-122">Les sites SharePoint modernes utilisent les groupes Office 365 pour contrôler l’accès au site.</span><span class="sxs-lookup"><span data-stu-id="d9a11-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="d9a11-123">Les paramètres invités des groupes Office 365 doivent être activés pour que l’accès invité dans les sites SharePoint fonctionne.</span><span class="sxs-lookup"><span data-stu-id="d9a11-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Capture d’écran des paramètres invités des groupes Office 365 dans le centre d’administration Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="d9a11-125">Pour définir les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="d9a11-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="d9a11-126">Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="d9a11-127">Cliquez sur **Services & compléments**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="d9a11-128">Dans la liste, cliquez sur **groupes Office 365**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="d9a11-129">Assurez-vous que les **membres de groupe Let en dehors de votre organisation accèdent au contenu de groupe** et que les **propriétaires de groupes ajoutent des personnes en dehors de votre organisation aux** cases à cocher sont activées.</span><span class="sxs-lookup"><span data-stu-id="d9a11-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="d9a11-130">Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="d9a11-131">Paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="d9a11-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="d9a11-132">Pour que les invités aient accès aux sites SharePoint, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.</span><span class="sxs-lookup"><span data-stu-id="d9a11-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="d9a11-133">Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour des sites individuels.</span><span class="sxs-lookup"><span data-stu-id="d9a11-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="d9a11-134">Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="d9a11-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="d9a11-135">Si vous souhaitez autoriser le partage de fichiers et de dossiers avec des utilisateurs anonymes, sélectionnez **tout le monde**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="d9a11-136">Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **nouveau et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="d9a11-137">Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="d9a11-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Capture d’écran des paramètres de partage au niveau de l’organisation SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="d9a11-139">Pour définir les paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="d9a11-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="d9a11-140">Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="d9a11-141">Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="d9a11-142">Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="d9a11-143">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="d9a11-144">Créer un site</span><span class="sxs-lookup"><span data-stu-id="d9a11-144">Create a site</span></span>

<span data-ttu-id="d9a11-145">L’étape suivante consiste à créer le site que vous envisagez d’utiliser pour collaborer avec des invités.</span><span class="sxs-lookup"><span data-stu-id="d9a11-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="d9a11-146">Pour créer un site</span><span class="sxs-lookup"><span data-stu-id="d9a11-146">To create a site</span></span>
1. <span data-ttu-id="d9a11-147">Dans le centre d’administration SharePoint, sous **sites**, cliquez sur **sites actifs**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="d9a11-148">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-148">Click **Create**.</span></span>
3. <span data-ttu-id="d9a11-149">Cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-149">Click **Team site**.</span></span>
4. <span data-ttu-id="d9a11-150">Tapez un nom de site et entrez un nom pour le propriétaire du groupe (propriétaire du site).</span><span class="sxs-lookup"><span data-stu-id="d9a11-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="d9a11-151">Sous **Paramètres avancés**, choisissez si vous souhaitez qu’il s’agit d’un site public ou privé.</span><span class="sxs-lookup"><span data-stu-id="d9a11-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="d9a11-152">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-152">Click **Next**.</span></span>
7. <span data-ttu-id="d9a11-153">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-153">Click **Finish**.</span></span>

<span data-ttu-id="d9a11-154">Nous allons inviter les utilisateurs ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d9a11-154">We'll invite users later.</span></span> <span data-ttu-id="d9a11-155">Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour ce site.</span><span class="sxs-lookup"><span data-stu-id="d9a11-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="d9a11-156">Paramètres de partage au niveau du site SharePoint</span><span class="sxs-lookup"><span data-stu-id="d9a11-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="d9a11-157">Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès souhaité pour ce site.</span><span class="sxs-lookup"><span data-stu-id="d9a11-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="d9a11-158">Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs**, mais que vous souhaitez que tous les invités s’authentifient pour ce site, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="d9a11-159">Notez que le site ne peut pas être partagé avec des utilisateurs anonymes (paramètre**tout le monde** ), mais avec des fichiers et des dossiers individuels.</span><span class="sxs-lookup"><span data-stu-id="d9a11-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Capture d’écran des paramètres de partage externe du site SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="d9a11-161">Pour définir les paramètres de partage au niveau du site</span><span class="sxs-lookup"><span data-stu-id="d9a11-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="d9a11-162">Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **sites** , puis cliquez sur **sites actifs**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="d9a11-163">Sélectionnez le site que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="d9a11-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="d9a11-164">Dans le ruban, cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="d9a11-165">Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="d9a11-166">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="d9a11-167">Inviter des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d9a11-167">Invite users</span></span>

<span data-ttu-id="d9a11-168">Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre site.</span><span class="sxs-lookup"><span data-stu-id="d9a11-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="d9a11-169">L’accès au site est contrôlé par le biais du groupe Office 365 associé, c’est pourquoi nous allons y ajouter des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d9a11-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="d9a11-170">Pour inviter des utilisateurs internes à un groupe</span><span class="sxs-lookup"><span data-stu-id="d9a11-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="d9a11-171">Accédez au site où vous souhaitez ajouter des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d9a11-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="d9a11-172">Cliquez sur **membres** dans le coin supérieur droit.</span><span class="sxs-lookup"><span data-stu-id="d9a11-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="d9a11-173">Cliquez sur **Ajouter des membres**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-173">Click **Add members**.</span></span>
4. <span data-ttu-id="d9a11-174">Tapez les noms ou les adresses de messagerie des utilisateurs que vous souhaitez inviter sur le site, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="d9a11-175">Les utilisateurs invités ne peuvent pas être ajoutés à partir du site.</span><span class="sxs-lookup"><span data-stu-id="d9a11-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="d9a11-176">Vous devez les ajouter à l’aide d’Outlook sur le Web.</span><span class="sxs-lookup"><span data-stu-id="d9a11-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="d9a11-177">Pour inviter des invités à un site</span><span class="sxs-lookup"><span data-stu-id="d9a11-177">To invite guests to a site</span></span>
1. <span data-ttu-id="d9a11-178">Dans Outlook sur le Web, sous **groupes**, cliquez sur le groupe dans lequel vous souhaitez ajouter des membres.</span><span class="sxs-lookup"><span data-stu-id="d9a11-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="d9a11-179">Ouvrez la carte de visite de groupe, puis, sous **autres options** (...), cliquez sur **Ajouter des membres**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="d9a11-180">Tapez les adresses de messagerie des invités que vous souhaitez inviter, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="d9a11-181">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="d9a11-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9a11-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9a11-182">See Also</span></span>
