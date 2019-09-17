---
title: Collaborer avec des invités dans une équipe
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Découvrez comment collaborer avec des invités dans Teams.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992413"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="a7a5a-103">Collaborer avec des invités dans une équipe</span><span class="sxs-lookup"><span data-stu-id="a7a5a-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="a7a5a-104">Si vous avez besoin de collaborer avec des invités dans des documents, des tâches et des conversations, nous vous recommandons d’utiliser Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="a7a5a-105">Teams fournit toutes les fonctionnalités de collaboration disponibles dans Office et SharePoint avec conversation permanente et un ensemble d’outils de collaboration personnalisable et extensible dans une expérience utilisateur unifiée.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="a7a5a-106">Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe de collaboration avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="a7a5a-107">Paramètres Azure de relations organisationnelles</span><span class="sxs-lookup"><span data-stu-id="a7a5a-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="a7a5a-108">Le partage dans Microsoft 365 est régi par les paramètres de relations organisationnelles dans Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="a7a5a-109">Si le partage d’invités est désactivé ou restreint dans Azure AD, cela remplace tous les paramètres de partage que vous configurez dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="a7a5a-110">Vérifiez les paramètres de relations organisationnelles pour vous assurer que le partage avec des invités n’est pas bloqué.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Capture d’écran de la page des paramètres des relations organisationnelles Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="a7a5a-112">Pour définir les paramètres de relation organisationnelle</span><span class="sxs-lookup"><span data-stu-id="a7a5a-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="a7a5a-113">Connectez-vous à Microsoft Azure [https://portal.azure.com](https://portal.azure.com)à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="a7a5a-114">Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="a7a5a-115">Dans le volet de **vue d’ensemble** , cliquez sur **relations organisationnelles**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="a7a5a-116">Dans le volet **relations organisationnelles** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="a7a5a-117">Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="a7a5a-118">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="a7a5a-119">Notez les paramètres dans la section **restrictions de collaboration** .</span><span class="sxs-lookup"><span data-stu-id="a7a5a-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="a7a5a-120">Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="a7a5a-121">Paramètres d’accès invité de teams</span><span class="sxs-lookup"><span data-stu-id="a7a5a-121">Teams guest access settings</span></span>

<span data-ttu-id="a7a5a-122">Teams dispose d’un commutateur maître/inactif pour l’accès invité et de divers paramètres permettant de contrôler ce que les invités peuvent faire dans une équipe.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="a7a5a-123">Le commutateur maître, **autoriser l’accès invité dans teams** doit être **activé** pour que l’accès invité fonctionne dans Teams.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="a7a5a-124">Vérifiez que l’accès invité est activé dans teams et effectuez les ajustements nécessaires aux paramètres invités en fonction des besoins de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="a7a5a-125">N’oubliez pas que ces paramètres affectent toutes les équipes.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-125">Keep in mind that these settings affect all teams.</span></span>

![Capture d’écran du basculement d’accès invité de teams](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="a7a5a-127">Pour définir les paramètres d’accès invité aux équipes</span><span class="sxs-lookup"><span data-stu-id="a7a5a-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="a7a5a-128">Connectez-vous au centre d’administration Microsoft 365 [https://admin.microsoft.com](https://admin.microsoft.com)à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="a7a5a-129">Dans le volet de navigation de gauche, cliquez sur **Afficher tout**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="a7a5a-130">Sous **centres d’administration**, cliquez sur **équipes**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="a7a5a-131">Dans le centre d’administration Teams, dans le volet de navigation de gauche, développez Paramètres à l’échelle de l' **organisation** , puis cliquez sur **accès invité**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="a7a5a-132">Assurez-vous que **l’autorisation autoriser l’accès invité dans teams** est **activée.**</span><span class="sxs-lookup"><span data-stu-id="a7a5a-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="a7a5a-133">Effectuez toutes les modifications souhaitées dans les paramètres d’invité supplémentaires, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="a7a5a-134">Le paramètre invité de teams peut prendre jusqu’à vingt-quatre heures après son activation.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="a7a5a-135">Les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="a7a5a-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="a7a5a-136">Teams utilise les groupes Office 365 pour les membres de l’équipe.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="a7a5a-137">Les paramètres invités des groupes Office 365 doivent être activés pour que l’accès invité dans teams puisse fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Capture d’écran des paramètres invités des groupes Office 365 dans le centre d’administration Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="a7a5a-139">Pour définir les paramètres invités des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="a7a5a-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="a7a5a-140">Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="a7a5a-141">Cliquez sur **Services & compléments**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="a7a5a-142">Dans la liste, cliquez sur **groupes Office 365**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="a7a5a-143">Assurez-vous que les **membres de groupe Let en dehors de votre organisation accèdent au contenu de groupe** et que les **propriétaires de groupes ajoutent des personnes en dehors de votre organisation aux** cases à cocher sont activées.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="a7a5a-144">Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="a7a5a-145">Paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a7a5a-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="a7a5a-146">Pour que les invités aient accès aux fichiers dans Teams, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="a7a5a-147">Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour des sites individuels, y compris les sites associés à Teams.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="a7a5a-148">Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="a7a5a-149">Si vous souhaitez autoriser le partage de fichiers et de dossiers avec des utilisateurs anonymes, sélectionnez **tout le monde**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="a7a5a-150">Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **nouveau et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="a7a5a-151">Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Capture d’écran des paramètres de partage au niveau de l’organisation SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="a7a5a-153">Pour définir les paramètres de partage au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a7a5a-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="a7a5a-154">Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="a7a5a-155">Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="a7a5a-156">Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="a7a5a-157">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="a7a5a-158">Paramètres de lien par défaut au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a7a5a-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="a7a5a-159">Les paramètres de lien de fichier et de dossier par défaut déterminent l’option de lien qui est présentée par défaut à l’utilisateur lorsqu’il partage un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="a7a5a-160">Les utilisateurs peuvent remplacer le type de lien par l’une des autres options avant de procéder au partage si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="a7a5a-161">N’oubliez pas que ce paramètre affecte toutes les équipes et tous les sites SharePoint de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="a7a5a-162">Choisissez le type de lien sélectionné par défaut lorsque les utilisateurs partagent des fichiers et des dossiers :</span><span class="sxs-lookup"><span data-stu-id="a7a5a-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="a7a5a-163">**Toute personne disposant du lien** : choisissez cette option si vous envisagez de partager un grand nombre de fichiers et de dossiers avec des utilisateurs anonymes.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="a7a5a-164">Si vous souhaitez autoriser les liens de *tous les utilisateurs* mais s’inquiète du partage anonyme accidentel, envisagez l’une des autres options par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="a7a5a-165">Ce type de lien n’est disponible que si vous avez activé le partage d’un **utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="a7a5a-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="a7a5a-166">**Uniquement les personnes de votre organisation** : choisissez cette option si vous pensez que le partage de fichiers et de dossiers doit être associé à des personnes au sein de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="a7a5a-167">**Personnes spécifiques** : envisagez cette option si vous envisagez de faire beaucoup de partage de fichiers et de dossiers avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="a7a5a-168">Ce type de lien fonctionne avec les invités et les requiert pour s’authentifier.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![Capture d’écran des paramètres de partage de fichiers et de dossiers au niveau de l’organisation SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="a7a5a-170">Pour définir les paramètres de liaison par défaut au niveau de l’organisation SharePoint</span><span class="sxs-lookup"><span data-stu-id="a7a5a-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="a7a5a-171">Accédez à la page de partage dans le centre d’administration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="a7a5a-172">Sous **liens de fichiers et de dossiers**, sélectionnez le lien de partage par défaut à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="a7a5a-173">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="a7a5a-174">Créer une équipe</span><span class="sxs-lookup"><span data-stu-id="a7a5a-174">Create a team</span></span>

<span data-ttu-id="a7a5a-175">L’étape suivante consiste à créer l’équipe que vous envisagez d’utiliser pour collaborer avec des invités.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="a7a5a-176">Pour créer une équipe</span><span class="sxs-lookup"><span data-stu-id="a7a5a-176">To create a team</span></span>
1. <span data-ttu-id="a7a5a-177">Dans Teams, sous l’onglet **teams** , cliquez sur **rejoindre ou créer une équipe** en bas du volet de gauche.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="a7a5a-178">Cliquez sur **créer une équipe**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="a7a5a-179">Cliquez sur **créer une équipe de toutes pièces**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="a7a5a-180">Choisissez **privé** ou **public**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="a7a5a-181">Tapez un nom et une description pour l’équipe, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="a7a5a-182">Cliquez sur **Ignorer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-182">Click **Skip**.</span></span>

<span data-ttu-id="a7a5a-183">Nous allons inviter les utilisateurs ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-183">We'll invite users later.</span></span> <span data-ttu-id="a7a5a-184">Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour le site SharePoint qui est associé à l’équipe.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="a7a5a-185">Paramètres de partage au niveau du site SharePoint</span><span class="sxs-lookup"><span data-stu-id="a7a5a-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="a7a5a-186">Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès que vous souhaitez pour cette équipe.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="a7a5a-187">Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs**, mais que vous souhaitez que tous les invités s’authentifient pour cette équipe, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Capture d’écran des paramètres de partage externe du site SharePoint](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="a7a5a-189">Pour définir les paramètres de partage au niveau du site</span><span class="sxs-lookup"><span data-stu-id="a7a5a-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="a7a5a-190">Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **sites** , puis cliquez sur **sites actifs**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="a7a5a-191">Sélectionnez le site de l’équipe que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="a7a5a-192">Dans le ruban, cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="a7a5a-193">Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="a7a5a-194">Si vous avez apporté des modifications, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="a7a5a-195">Inviter des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a7a5a-195">Invite users</span></span>

<span data-ttu-id="a7a5a-196">Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre équipe.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="a7a5a-197">Pour inviter des utilisateurs internes à une équipe</span><span class="sxs-lookup"><span data-stu-id="a7a5a-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="a7a5a-198">Dans l’équipe, cliquez sur plus d'**\*\*** **options** (), puis sur **Ajouter un membre**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="a7a5a-199">Tapez le nom de la personne que vous souhaitez inviter.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="a7a5a-200">Cliquez sur **Ajouter**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="a7a5a-201">Pour inviter des invités à une équipe</span><span class="sxs-lookup"><span data-stu-id="a7a5a-201">To invite guests to a team</span></span>
1. <span data-ttu-id="a7a5a-202">Dans l’équipe, cliquez sur plus d'**\*\*** **options** (), puis sur **Ajouter un membre**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="a7a5a-203">Tapez l’adresse de messagerie de l’invité que vous souhaitez inviter.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="a7a5a-204">Cliquez sur **modifier les informations invité**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="a7a5a-205">Tapez le nom complet de l’invité et cliquez sur la coche.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="a7a5a-206">Cliquez sur **Ajouter**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="a7a5a-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7a5a-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7a5a-207">See Also</span></span>

