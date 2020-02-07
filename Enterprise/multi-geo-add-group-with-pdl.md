---
title: Créer un groupe Office 365 avec un emplacement par défaut des données spécifique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment créer un groupe Office 365 avec un emplacement par défaut des données spécifique dans un environnement multigéographique.
ms.openlocfilehash: 5a6417f1758cd6c5e4eb9d4df9e7796d4309e62c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843735"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="824da-103">Créer un groupe Office 365 avec un emplacement par défaut des données spécifique</span><span class="sxs-lookup"><span data-stu-id="824da-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="824da-104">Quand un utilisateur dans un environnement multigéographique crée un groupe Office 365, l’emplacement par défaut des données du groupe est automatiquement défini sur celui de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="824da-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="824da-105">Les administrateurs Exchange, SharePoint et généraux peuvent créer des groupes dans n’importe quelle région sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="824da-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="824da-106">Si vous devez créer un groupe avec un emplacement par défaut des données spécifique, vous le faire à l’aide de l’applet de commande Microsoft PowerShell New-UnifiedGroup d’Exchange Online ou à partir du Centre d’administration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="824da-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="824da-107">Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont configurés dans l’emplacement par défaut des données spécifié.</span><span class="sxs-lookup"><span data-stu-id="824da-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="824da-108">Pour créer un groupe Office 365 incluant un emplacement par défaut des données à spécifier, accédez au Centre d’administration SharePoint de l’emplacement géographique dans lequel vous souhaitez créer le site de groupe.</span><span class="sxs-lookup"><span data-stu-id="824da-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="824da-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="824da-109">For example:</span></span>

<span data-ttu-id="824da-110">Si vous souhaitez créer un site de groupe à partir de votre emplacement en Australie, vous pouvez aller à https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="824da-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="824da-111">Sélectionnez **+ Créer**.</span><span class="sxs-lookup"><span data-stu-id="824da-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="824da-112">Suivez le processus pour créer un site de groupe.</span><span class="sxs-lookup"><span data-stu-id="824da-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="824da-113">Votre site de groupe est configuré dans l’emplacement géographique correspondant au Centre d’administration SharePoint à partir duquel vous avez initié la demande de création de site.</span><span class="sxs-lookup"><span data-stu-id="824da-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="824da-114">Utilisation d’Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="824da-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="824da-115">Connectez-vous à Exchange Online PowerShell en transmettant le paramètre *-MailBoxRegion* avec le code d’emplacement géographique.</span><span class="sxs-lookup"><span data-stu-id="824da-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="824da-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="824da-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran de la cmdlet PowerShell New-UnifiedGroup avec la syntaxe](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="824da-118">Notez que l’approvisionnement du site du groupe SharePoint est à la demande.</span><span class="sxs-lookup"><span data-stu-id="824da-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="824da-119">Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="824da-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="824da-120">Codes d’emplacement géographique</span><span class="sxs-lookup"><span data-stu-id="824da-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="824da-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="824da-121">See also</span></span>

[<span data-ttu-id="824da-122">Connexion à Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="824da-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
