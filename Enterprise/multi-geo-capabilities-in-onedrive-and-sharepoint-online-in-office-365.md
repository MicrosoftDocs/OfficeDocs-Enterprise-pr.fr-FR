---
title: Fonctionnalités multi-géographiques OneDrive et SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Étendez votre présence Office 365 à plusieurs régions géographiques grâce aux fonctionnalités multi-géographiques dans OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948585"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="8121f-103">Fonctionnalités multi-géographiques OneDrive et SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8121f-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="8121f-104">Les fonctionnalités multi-géographiques dans OneDrive et SharePoint Online permettent de contrôler le pays ou la région où des ressources partagées tels que les sites d’équipe SharePoint et les boîtes aux lettres de groupe Office 365 qui sont stockés au repos. </span><span class="sxs-lookup"><span data-stu-id="8121f-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="8121f-105">Chaque utilisateur, une boîte aux lettres de groupe et un site SharePoint ont un emplacement recommandé de données (PDL) qui indique l’emplacement géographique où les données connexes sont stockées.</span><span class="sxs-lookup"><span data-stu-id="8121f-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="8121f-106">Les donnée personnelle des utilisateurs (boîte aux lettres Exchange et OneDrive), ainsi que les sites de Groupes Office 365 ou SharePoint qu’ils créent peuvent être stockées dans l’emplacement spécifié géographique pour répondre aux exigences de résidence de données.</span><span class="sxs-lookup"><span data-stu-id="8121f-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="8121f-107">Vous pouvez[spécifier des différents administrateurs pour chaque emplacement géo](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="8121f-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="8121f-108">Les utilisateurs profitent d’une expérience transparente lors de l’utilisation des services Office 365, y compris les applications Office, OneDrive et Recherche.</span><span class="sxs-lookup"><span data-stu-id="8121f-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="8121f-109">Voir [Expérience utilisateur dans un environnement multi-géographique](multi-geo-user-experience.md) pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="8121f-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="8121f-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="8121f-110">OneDrive</span></span>

<span data-ttu-id="8121f-111">Le OneDrive de chaque utilisateur peut être configuré dans ou [déplacé par un administrateur](move-onedrive-between-geo-locations.md) vers un emplacement satellite conformément aux PDL de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8121f-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="8121f-112">Les fichiers personnels sont alors conservés dans cet emplacement géo, même s’ils peuvent être partagés avec des utilisateurs dans d’autres emplacements géo.</span><span class="sxs-lookup"><span data-stu-id="8121f-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="8121f-113">Utilisateurs et groupes</span><span class="sxs-lookup"><span data-stu-id="8121f-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="8121f-114">Lorsqu’un utilisateur crée un site connecté à un groupe SharePoint, leur PDL permet de déterminer l’emplacement géo où le site et sa boîte aux lettres de groupe associés sont créés.</span><span class="sxs-lookup"><span data-stu-id="8121f-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="8121f-115">(Si une valeur PDL de l’utilisateur n’a pas été définie ou a été définie sur l’emplacement géo qui n’a pas été configuré comme un emplacement satellite, puis le site et la boîte aux lettres sont créés dans l’emplacement central.)</span><span class="sxs-lookup"><span data-stu-id="8121f-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="8121f-116">Les services Office 365 autre qu’ Exchange, OneDrive et SharePoint ne sont pas multi-géographiques.</span><span class="sxs-lookup"><span data-stu-id="8121f-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="8121f-117">Toutefois, les Groupes Office 365 créés par ces services sont marqués avec PDL de l’application de création et leur boîte aux lettres de groupe Exchange et le Site de groupe Office 365 SharePoint fournis dans le géo correspondant.</span><span class="sxs-lookup"><span data-stu-id="8121f-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="8121f-118">Gestion de l’environnement multi-Géo</span><span class="sxs-lookup"><span data-stu-id="8121f-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="8121f-119">Configurer et gérer votre environnement multi-géographique sont effectués via le Centre d’Administration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8121f-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Capture d’écran de la page emplacements géo dans le Centre d’Administration SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="8121f-121">(Certaines actions, telles que le déplacement d’un site SharePoint ou un site OneDrive nécessitent Microsoft PowerShell).</span><span class="sxs-lookup"><span data-stu-id="8121f-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="8121f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8121f-122">See also</span></span>

[<span data-ttu-id="8121f-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="8121f-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="8121f-124">Administration d’un environnement multi-géographique</span><span class="sxs-lookup"><span data-stu-id="8121f-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="8121f-125">Quotas de stockage SharePoint dans des environnements multi-géographiques</span><span class="sxs-lookup"><span data-stu-id="8121f-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="8121f-126">Administration des boîtes aux lettres Exchange Online dans un environnement multi-géographique</span><span class="sxs-lookup"><span data-stu-id="8121f-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
