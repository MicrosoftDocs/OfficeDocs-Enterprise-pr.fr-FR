---
title: Ajouter ou supprimer un administrateur localisés
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Découvrez comment ajouter ou supprimer un administrateur localisés dans OneDrive pour Business Multi-localisés.
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="e53eb-103">Ajouter ou supprimer un administrateur localisés dans OneDrive pour Busniess Multi-localisés</span><span class="sxs-lookup"><span data-stu-id="e53eb-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="e53eb-p101">Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique que vous avez dans votre client. Ces administrateurs auront accès aux paramètres de SharePoint Online et OneDrive qui sont spécifiques à leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="e53eb-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="e53eb-p102">Certains services - telles que le magasin de termes - sont administrés à partir de l’emplacement central et répliquées aux emplacements satellites. L’administrateur localisés pour l’emplacement central a accès à ces derniers, tandis que les administrateurs localisés pour les emplacements satellites ne.</span><span class="sxs-lookup"><span data-stu-id="e53eb-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="e53eb-108">Les administrateurs globaux et les administrateurs SharePoint Online continuent à accéder aux paramètres dans tous les emplacements de géolocalisation.</span><span class="sxs-lookup"><span data-stu-id="e53eb-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="e53eb-109">Configuration des administrateurs localisés</span><span class="sxs-lookup"><span data-stu-id="e53eb-109">Configuring geo administrators</span></span>

<span data-ttu-id="e53eb-110">Configuration des administrateurs localisés nécessite module SharePoint Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e53eb-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="e53eb-111">[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) permet de se connecter au centre d’administration de l’emplacement géographique où vous souhaitez ajouter l’administrateur de géolocalisation. (Par exemple, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="e53eb-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="e53eb-112">Pour afficher les administrateurs geo existant d’un emplacement, exécutez`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="e53eb-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="e53eb-113">Ajout d’un utilisateur en tant qu’un administrateur localisés</span><span class="sxs-lookup"><span data-stu-id="e53eb-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="e53eb-114">Pour ajouter un utilisateur en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="e53eb-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="e53eb-115">Pour supprimer un utilisateur en tant qu’un administrateur géographique d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="e53eb-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="e53eb-116">Ajout d’un groupe en tant qu’un administrateur localisés</span><span class="sxs-lookup"><span data-stu-id="e53eb-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="e53eb-117">Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension messagerie en tant qu’un administrateur de géolocalisation. (Groupes de distribution et les groupes d’Office 365 ne sont pas pris en charge.)</span><span class="sxs-lookup"><span data-stu-id="e53eb-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="e53eb-118">Pour ajouter un groupe en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="e53eb-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="e53eb-119">Pour supprimer un groupe en tant qu’un administrateur localisés, exécutez`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="e53eb-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="e53eb-p103">Notez que pas tous les groupes de sécurité ont un alias de groupe. Si vous souhaitez ajouter un groupe de sécurité qui ne dispose pas d’un alias, exécutez [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) pour récupérer la liste des groupes, trouver ObjectID de votre groupe de sécurité, puis exécutez :</span><span class="sxs-lookup"><span data-stu-id="e53eb-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="e53eb-122">Pour supprimer un groupe à l’aide de ObjectID, exécutez`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="e53eb-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="e53eb-123">Accès au centre d’administration pour un géolocalisation spécifique</span><span class="sxs-lookup"><span data-stu-id="e53eb-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="e53eb-124">Pour administrer les paramètres de OneDrive pour leur emplacement géographique, administrateurs doivent accéder au centre d’administration OneDrive directement à l’aide du format d’URL suivant :</span><span class="sxs-lookup"><span data-stu-id="e53eb-124">To administer OneDrive settings for their geo-location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="e53eb-125">https://admin.onedrive.com/?geo=<*localisés*></span><span class="sxs-lookup"><span data-stu-id="e53eb-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="e53eb-126">Par exemple, le centre d’administration de OneDrive pour le Canada trouve à l’adresse : https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="e53eb-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="e53eb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e53eb-127">See Also</span></span>

[<span data-ttu-id="e53eb-128">SPOGeoAdministrator ajouter</span><span class="sxs-lookup"><span data-stu-id="e53eb-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="e53eb-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="e53eb-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="e53eb-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="e53eb-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="e53eb-131">Définir un alias (MailNickName) pour un groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="e53eb-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)