---
title: Ajouter ou supprimer un administrateur de zone géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Apprenez à ajouter ou supprimer un administrateur de la zone géographique dans OneDrive pour entreprise Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="74238-103">Ajouter ou supprimer un administrateur de la zone géographique dans OneDrive pour Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="74238-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="74238-p101">Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique que vous avez dans votre client. Ces administrateurs auront accès aux paramètres de SharePoint Online et OneDrive qui sont spécifiques à leur emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="74238-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="74238-p102">Certains services - tels que la banque de termes - sont administrés depuis un emplacement central et répliqués dans des endroits de satellite. L’administrateur geo pour l’emplacement central a accès à ceux-ci, alors que les administrateurs geo pour les emplacements de satellites ne.</span><span class="sxs-lookup"><span data-stu-id="74238-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="74238-108">Les administrateurs globaux et les administrateurs SharePoint Online continuent à accéder aux paramètres dans tous les emplacements de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="74238-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="74238-109">Configuration des administrateurs de geo</span><span class="sxs-lookup"><span data-stu-id="74238-109">Configuring geo administrators</span></span>

<span data-ttu-id="74238-110">Configuration des administrateurs de geo requiert SharePoint Online PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="74238-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="74238-111">Utilisez [SPOService à la connexion](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) pour vous connecter au centre d’administration de l’emplacement géographique où vous souhaitez ajouter l’administrateur de zone géographique. (Par exemple, se connecter à SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="74238-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="74238-112">Pour ajouter un utilisateur comme un administrateur de zone géographique, exécuter`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="74238-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="74238-113">Pour afficher les administrateurs geo existant d’un emplacement, exécutez`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="74238-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="74238-114">Pour supprimer un utilisateur en tant qu’un administrateur géographique d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="74238-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="74238-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74238-115">See Also</span></span>

[<span data-ttu-id="74238-116">Ajouter-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="74238-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="74238-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="74238-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="74238-118">Supprimer-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="74238-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)