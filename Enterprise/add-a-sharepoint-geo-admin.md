---
title: Ajouter ou supprimer un administrateur géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Découvrez comment ajouter ou supprimer un administrateur localisés dans OneDrive pour Business Multi-localisés.
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849810"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="4a9ad-103">Ajouter ou supprimer un administrateur localisés dans OneDrive pour Busniess Multi-localisés</span><span class="sxs-lookup"><span data-stu-id="4a9ad-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="4a9ad-p101">Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique que vous avez dans votre client. Ces administrateurs auront accès aux paramètres de SharePoint Online et OneDrive qui sont spécifiques à leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="4a9ad-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="4a9ad-p102">Certains services - telles que le magasin de termes - sont administrés à partir de l’emplacement central et répliquées aux emplacements satellites. L’administrateur localisés pour l’emplacement central a accès à ces derniers, tandis que les administrateurs localisés pour les emplacements satellites ne.</span><span class="sxs-lookup"><span data-stu-id="4a9ad-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="4a9ad-108">Les administrateurs globaux et les administrateurs SharePoint Online continuent à accéder aux paramètres de l’emplacement central et tous les emplacements de satellites.</span><span class="sxs-lookup"><span data-stu-id="4a9ad-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="4a9ad-109">Configuration des administrateurs localisés</span><span class="sxs-lookup"><span data-stu-id="4a9ad-109">Configuring geo administrators</span></span>

<span data-ttu-id="4a9ad-110">Configuration des administrateurs localisés nécessite module SharePoint Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a9ad-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="4a9ad-111">[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) permet de se connecter au centre d’administration de l’emplacement géographique où vous souhaitez ajouter l’administrateur de géolocalisation. (Par exemple, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="4a9ad-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="4a9ad-112">Pour afficher les administrateurs geo existant d’un emplacement, exécutez`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="4a9ad-113">Ajout d’un utilisateur en tant qu’un administrateur localisés</span><span class="sxs-lookup"><span data-stu-id="4a9ad-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="4a9ad-114">Pour ajouter un utilisateur en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="4a9ad-115">Pour supprimer un utilisateur en tant qu’un administrateur géographique d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="4a9ad-116">Ajout d’un groupe en tant qu’un administrateur localisés</span><span class="sxs-lookup"><span data-stu-id="4a9ad-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="4a9ad-117">Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension messagerie en tant qu’un administrateur de géolocalisation. (Groupes de distribution et les groupes d’Office 365 ne sont pas pris en charge.)</span><span class="sxs-lookup"><span data-stu-id="4a9ad-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="4a9ad-118">Pour ajouter un groupe en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="4a9ad-119">Pour supprimer un groupe en tant qu’un administrateur localisés, exécutez`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="4a9ad-p103">Notez que pas tous les groupes de sécurité ont un alias de groupe. Si vous souhaitez ajouter un groupe de sécurité qui ne dispose pas d’un alias, exécutez [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) pour récupérer la liste des groupes, trouver ObjectID de votre groupe de sécurité, puis exécutez :</span><span class="sxs-lookup"><span data-stu-id="4a9ad-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="4a9ad-122">Pour supprimer un groupe à l’aide de ObjectID, exécutez`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="4a9ad-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="4a9ad-123">Accès au centre d’administration pour un géolocalisation spécifique</span><span class="sxs-lookup"><span data-stu-id="4a9ad-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="4a9ad-124">Pour administrer les paramètres de OneDrive pour leur emplacement géographique, administrateurs doivent accéder au centre d’administration OneDrive directement à l’aide du format d’URL suivant :</span><span class="sxs-lookup"><span data-stu-id="4a9ad-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="4a9ad-125">https://admin.onedrive.com/?geo=<*localisés*></span><span class="sxs-lookup"><span data-stu-id="4a9ad-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="4a9ad-126">Par exemple, le centre d’administration de OneDrive pour le Canada trouve à l’adresse : https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="4a9ad-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a9ad-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a9ad-127">See Also</span></span>

[<span data-ttu-id="4a9ad-128">SPOGeoAdministrator ajouter</span><span class="sxs-lookup"><span data-stu-id="4a9ad-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="4a9ad-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="4a9ad-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="4a9ad-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="4a9ad-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="4a9ad-131">Définir un alias (MailNickName) pour un groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="4a9ad-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)