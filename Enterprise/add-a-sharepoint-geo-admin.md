---
title: Ajouter ou supprimer un administrateur géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Priority
f1.keywords:
- NOCSH
description: Découvrez comment ajouter ou supprimer un administrateur géographique dans Office 365 multigéographique.
ms.openlocfilehash: 0e0ce9166d7e290ea0f038bf8d4f20c132be2bc4
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840791"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="5d9be-103">Ajouter ou supprimer un administrateur géographique dans Office 365 multigéographique</span><span class="sxs-lookup"><span data-stu-id="5d9be-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="5d9be-104">Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique disponible dans votre client.</span><span class="sxs-lookup"><span data-stu-id="5d9be-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="5d9be-105">Ces administrateurs ont accès aux paramètres SharePoint Online et OneDrive spécifiques de leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="5d9be-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="5d9be-106">Certains services (par exemple, le magasin de termes) sont administrés à partir de l’emplacement central et répliqués vers des emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="5d9be-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="5d9be-107">L’administrateur géographique de l’emplacement central a accès à ces fonctionnalités, au contraire des administrateurs géographiques des emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="5d9be-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="5d9be-108">Les administrateurs généraux et les administrateurs SharePoint Online ont toujours accès aux paramètres dans l’emplacement central et dans tous les emplacements satellites.</span><span class="sxs-lookup"><span data-stu-id="5d9be-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="5d9be-109">Configuration des administrateurs géographiques</span><span class="sxs-lookup"><span data-stu-id="5d9be-109">Configuring geo administrators</span></span>

<span data-ttu-id="5d9be-110">La configuration des administrateurs géographiques nécessite un module SharePoint Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d9be-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="5d9be-111">Pour vous connecter au centre d’administration de l’emplacement géographique auquel vous voulez ajouter l’administrateur géo, utilisez la cmdlet [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) (par exemple, Connect-SPOService https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="5d9be-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="5d9be-112">Pour afficher les administrateurs géographiques existants d’un emplacement, exécutez la cmdlet `Get-SPOGeoAdministrator`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="5d9be-113">Ajout d’un utilisateur en tant qu’administrateur géographique</span><span class="sxs-lookup"><span data-stu-id="5d9be-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="5d9be-114">Pour ajouter un utilisateur en tant qu’administrateur géographique, exécutez la cmdlet `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="5d9be-115">Pour supprimer un utilisateur administrateur géographique d’un emplacement, exécutez la cmdlet `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="5d9be-116">Ajout d’un groupe en tant qu’administrateur géographique</span><span class="sxs-lookup"><span data-stu-id="5d9be-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="5d9be-117">Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension courrier en tant qu’administrateur géographique (les groupes de distribution et les groupes Office 365 ne sont pas pris en charge).</span><span class="sxs-lookup"><span data-stu-id="5d9be-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="5d9be-118">Pour ajouter un groupe en tant qu’administrateur géographique, exécutez la cmdlet `Add-SPOGeoAdministrator -GroupAlias <alias>`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="5d9be-119">Pour supprimer un groupe administrateur géographique, exécutez la cmdlet `Remove-SPOGeoAdministrator -GroupAlias <alias>`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="5d9be-120">Notez que certains groupes de sécurité n’ont pas d’alias de groupe.</span><span class="sxs-lookup"><span data-stu-id="5d9be-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="5d9be-121">Si vous voulez ajouter un groupe de sécurité dépourvu d’alias, exécutez la cmdlet [MsolGroup Get](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) pour récupérer une liste de groupes, recherchez l’ObjectID de votre groupe de sécurité, puis exécutez la cmdlet suivante :</span><span class="sxs-lookup"><span data-stu-id="5d9be-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="5d9be-122">Pour supprimer un groupe à l’aide de l’ObjectID, exécutez la cmdlet `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="5d9be-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d9be-123">See Also</span></span>

[<span data-ttu-id="5d9be-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5d9be-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="5d9be-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5d9be-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="5d9be-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5d9be-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="5d9be-127">Définir un alias (MailNickName) pour un groupe de sécurité</span><span class="sxs-lookup"><span data-stu-id="5d9be-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)