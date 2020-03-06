---
title: Collaborer avec des invités sur un site
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: Découvrez comment collaborer avec des invités sur un site SharePoint.
ms.openlocfilehash: 8c1c34fded910701275a80aa0740a746a2458156
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549113"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="a0456-103">Collaborer avec des invités sur un site</span><span class="sxs-lookup"><span data-stu-id="a0456-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="a0456-104">Si vous avez besoin de collaborer avec des invités dans des documents, des données et des listes, vous pouvez utiliser un site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a0456-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="a0456-105">Les sites SharePoint modernes sont connectés aux groupes Office 365 qui peuvent gérer l’appartenance à un site et fournir des outils de collaboration supplémentaires tels qu’une boîte aux lettres et un calendrier partagés.</span><span class="sxs-lookup"><span data-stu-id="a0456-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="a0456-106">Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer un site SharePoint en vue de la collaboration avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a0456-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="a0456-107">Démonstration vidéo</span><span class="sxs-lookup"><span data-stu-id="a0456-107">Video demonstration</span></span>

<span data-ttu-id="a0456-108">Cette vidéo présente les étapes de configuration décrites dans ce document.</span><span class="sxs-lookup"><span data-stu-id="a0456-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="a0456-109">Paramètres Azure de relations organisationnelles</span><span class="sxs-lookup"><span data-stu-id="a0456-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="a0456-110">Le partage dans Microsoft 365 est régi par les paramètres de relations organisationnelles dans Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a0456-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="a0456-111">Si le partage d’invités est désactivé ou restreint dans Azure AD, cela remplace tous les paramètres de partage que vous configurez dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a0456-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="a0456-112">Vérifiez les paramètres de relations organisationnelles pour vous assurer que le partage avec des invités n’est pas bloqué.</span><span class="sxs-lookup"><span data-stu-id="a0456-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Capture d’écran de la page des paramètres de relations organisationnelles d’Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="a0456-114">Pour définir les paramètres de relation organisationnelle</span><span class="sxs-lookup"><span data-stu-id="a0456-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="a0456-115">Connectez-vous à Microsoft Azure [https://portal.azure.com](https://portal.azure.com)à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="a0456-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="a0456-116">Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="a0456-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="a0456-117">Dans le volet de **vue d’ensemble** , cliquez sur **relations organisationnelles**.</span><span class="sxs-lookup"><span data-stu-id="a0456-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="a0456-118">Dans le volet **relations organisationnelles** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="a0456-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="a0456-119">Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="a0456-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="a0456-120">Si vous avez effectué des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="a0456-121">Notez les paramètres dans la section **restrictions de collaboration** .</span><span class="sxs-lookup"><span data-stu-id="a0456-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="a0456-122">Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.</span><span class="sxs-lookup"><span data-stu-id="a0456-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="a0456-123">Les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="a0456-123">Office 365 Groups guest settings</span></span>

<span data-ttu-id="a0456-124">Les sites SharePoint modernes utilisent les groupes Office 365 pour contrôler l’accès au site.</span><span class="sxs-lookup"><span data-stu-id="a0456-124">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="a0456-125">Les paramètres invités des groupes Office 365 doivent être activés pour que l’accès invité dans les sites SharePoint fonctionne.</span><span class="sxs-lookup"><span data-stu-id="a0456-125">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Capture d’écran des paramètres d’invité des Groupes Office 365 dans le Centre d’administration Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="a0456-127">Pour définir les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="a0456-127">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="a0456-128">Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="a0456-128">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="a0456-129">Cliquez sur **Services & compléments**.</span><span class="sxs-lookup"><span data-stu-id="a0456-129">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="a0456-130">Dans la liste, cliquez sur **groupes Office 365**.</span><span class="sxs-lookup"><span data-stu-id="a0456-130">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="a0456-131">Assurez-vous que les **membres de groupe Let en dehors de votre organisation accèdent au contenu de groupe** et que les **propriétaires de groupes ajoutent des personnes en dehors de votre organisation aux** cases à cocher sont activées.</span><span class="sxs-lookup"><span data-stu-id="a0456-131">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="a0456-132">Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.</span><span class="sxs-lookup"><span data-stu-id="a0456-132">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="a0456-133">Paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0456-133">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="a0456-134">Pour que les invités aient accès aux sites SharePoint, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a0456-134">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="a0456-135">Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour des sites individuels.</span><span class="sxs-lookup"><span data-stu-id="a0456-135">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="a0456-136">Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="a0456-136">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="a0456-137">Si vous souhaitez autoriser le partage de fichiers et de dossiers non authentifié, sélectionnez **tout le monde**.</span><span class="sxs-lookup"><span data-stu-id="a0456-137">If you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="a0456-138">Si vous souhaitez vous assurer que toutes les personnes extérieures à votre organisation doivent s’authentifier, choisissez **nouveau et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="a0456-138">If you want to ensure that all people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="a0456-139">Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a0456-139">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="a0456-141">Pour définir les paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0456-141">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="a0456-142">Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a0456-142">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="a0456-143">Dans le centre d’administration SharePoint, dans le volet de gauche, cliquez sur **Partage**.</span><span class="sxs-lookup"><span data-stu-id="a0456-143">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="a0456-144">Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="a0456-144">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="a0456-145">Si vous avez effectué des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-145">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="a0456-146">Créer un site</span><span class="sxs-lookup"><span data-stu-id="a0456-146">Create a site</span></span>

<span data-ttu-id="a0456-147">L’étape suivante consiste à créer le site que vous envisagez d’utiliser pour collaborer avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a0456-147">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="a0456-148">Pour créer un site</span><span class="sxs-lookup"><span data-stu-id="a0456-148">To create a site</span></span>
1. <span data-ttu-id="a0456-149">Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.</span><span class="sxs-lookup"><span data-stu-id="a0456-149">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="a0456-150">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-150">Click **Create**.</span></span>
3. <span data-ttu-id="a0456-151">Cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="a0456-151">Click **Team site**.</span></span>
4. <span data-ttu-id="a0456-152">Tapez un nom de site et entrez un nom pour le propriétaire du groupe (propriétaire du site).</span><span class="sxs-lookup"><span data-stu-id="a0456-152">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="a0456-153">Sous **Paramètres avancés**, choisissez si vous souhaitez qu’il s’agit d’un site public ou privé.</span><span class="sxs-lookup"><span data-stu-id="a0456-153">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="a0456-154">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="a0456-154">Click **Next**.</span></span>
7. <span data-ttu-id="a0456-155">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-155">Click **Finish**.</span></span>

<span data-ttu-id="a0456-156">Nous allons inviter les utilisateurs ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a0456-156">We'll invite users later.</span></span> <span data-ttu-id="a0456-157">Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour ce site.</span><span class="sxs-lookup"><span data-stu-id="a0456-157">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="a0456-158">Paramètres de partage au niveau du site SharePoint</span><span class="sxs-lookup"><span data-stu-id="a0456-158">SharePoint site level sharing settings</span></span>

<span data-ttu-id="a0456-159">Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès souhaité pour ce site.</span><span class="sxs-lookup"><span data-stu-id="a0456-159">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="a0456-160">Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs**, mais que vous souhaitez que tous les invités s’authentifient pour ce site, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="a0456-160">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="a0456-161">Notez que le site ne peut pas être partagé avec des personnes non authentifiées (paramètre**tout le monde** ), mais avec des fichiers et dossiers individuels.</span><span class="sxs-lookup"><span data-stu-id="a0456-161">Note that the site cannot be shared with unauthenticated people (**Anyone** setting), but individual files and folders can.</span></span>

![Capture d’écran des paramètres de partage externe de site SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="a0456-163">Pour définir les paramètres de partage au niveau du site</span><span class="sxs-lookup"><span data-stu-id="a0456-163">To set site-level sharing settings</span></span>
1. <span data-ttu-id="a0456-164">Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.</span><span class="sxs-lookup"><span data-stu-id="a0456-164">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="a0456-165">Sélectionnez le site que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="a0456-165">Select the site that you just created.</span></span>
3. <span data-ttu-id="a0456-166">Dans le ruban, cliquez sur **Partage**. </span><span class="sxs-lookup"><span data-stu-id="a0456-166">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="a0456-167">Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="a0456-167">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="a0456-168">Si vous avez effectué des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-168">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="a0456-169">Inviter des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a0456-169">Invite users</span></span>

<span data-ttu-id="a0456-170">Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre site.</span><span class="sxs-lookup"><span data-stu-id="a0456-170">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="a0456-171">L’accès au site est contrôlé par le biais du groupe Office 365 associé, c’est pourquoi nous allons y ajouter des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a0456-171">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="a0456-172">Pour inviter des utilisateurs internes à un groupe</span><span class="sxs-lookup"><span data-stu-id="a0456-172">To invite internal users to a group</span></span>
1. <span data-ttu-id="a0456-173">Accédez au site où vous souhaitez ajouter des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a0456-173">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="a0456-174">Cliquez sur **membres** dans le coin supérieur droit.</span><span class="sxs-lookup"><span data-stu-id="a0456-174">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="a0456-175">Cliquez sur **Ajouter des membres**.</span><span class="sxs-lookup"><span data-stu-id="a0456-175">Click **Add members**.</span></span>
4. <span data-ttu-id="a0456-176">Tapez les noms ou les adresses de messagerie des utilisateurs que vous souhaitez inviter sur le site, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-176">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="a0456-177">Les utilisateurs invités ne peuvent pas être ajoutés à partir du site.</span><span class="sxs-lookup"><span data-stu-id="a0456-177">Guest users can't be added from the site.</span></span> <span data-ttu-id="a0456-178">Vous devez les ajouter à l’aide d’Outlook sur le Web.</span><span class="sxs-lookup"><span data-stu-id="a0456-178">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="a0456-179">Pour inviter des invités à un groupe</span><span class="sxs-lookup"><span data-stu-id="a0456-179">To invite guests to a group</span></span>
1. <span data-ttu-id="a0456-180">Dans Outlook sur le Web, sous **groupes**, cliquez sur le groupe dans lequel vous souhaitez ajouter des membres.</span><span class="sxs-lookup"><span data-stu-id="a0456-180">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="a0456-181">Ouvrez la carte de visite de groupe, puis, sous **autres options** (...), cliquez sur **Ajouter des membres**.</span><span class="sxs-lookup"><span data-stu-id="a0456-181">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="a0456-182">Tapez les adresses de messagerie des invités que vous souhaitez inviter, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a0456-182">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="a0456-183">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="a0456-183">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0456-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0456-184">See Also</span></span>

[<span data-ttu-id="a0456-185">Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés</span><span class="sxs-lookup"><span data-stu-id="a0456-185">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="a0456-186">Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités</span><span class="sxs-lookup"><span data-stu-id="a0456-186">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="a0456-187">Créer un environnement de partage sécurisé avec des invités</span><span class="sxs-lookup"><span data-stu-id="a0456-187">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="a0456-188">Créer un extranet B2B avec des invités gérés</span><span class="sxs-lookup"><span data-stu-id="a0456-188">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)

