---
title: Utilisation de PowerShell pour créer des rapports pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour créer des rapports que vous ne pouvez pas produire dans le centre d’administration Microsoft 365.'
ms.openlocfilehash: d2d03d6ac170fef95352a2aabf6cd27176202a1e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605316"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="49c08-103">Utilisation de PowerShell pour créer des rapports pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="49c08-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="49c08-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="49c08-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="49c08-105">De nombreux rapports sont disponibles dans le centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="49c08-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="49c08-106">Toutefois, ces rapports fournissent uniquement une certaine quantité d'informations et vous avez parfois besoin de plus.</span><span class="sxs-lookup"><span data-stu-id="49c08-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="49c08-107">C’est lorsque vous avez besoin de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="49c08-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="49c08-108">Ces articles décrivent comment utiliser PowerShell pour Microsoft 365 pour obtenir des informations à partir de votre client Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="49c08-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="49c08-109">Prise en main de la création de rapports à l’aide de PowerShell pour Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="49c08-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="49c08-110">PowerShell pour Microsoft 365 peut révéler des informations supplémentaires qui ne sont pas visibles avec le centre d’administration</span><span class="sxs-lookup"><span data-stu-id="49c08-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="49c08-111">PowerShell pour Microsoft 365 est idéal pour le filtrage des données</span><span class="sxs-lookup"><span data-stu-id="49c08-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="49c08-112">PowerShell pour Microsoft 365 facilite l’impression ou l’enregistrement des données</span><span class="sxs-lookup"><span data-stu-id="49c08-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="49c08-113">Rapports pour les comptes d’utilisateurs et les licences :</span><span class="sxs-lookup"><span data-stu-id="49c08-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="49c08-114">Afficher les licences et les services Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="49c08-115">Afficher les utilisateurs titulaires d’une licence et d’utilisateurs sans licence Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="49c08-116">Afficher les détails de service et de licence de compte Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="49c08-117">Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="49c08-118">Rapports pour SharePoint Online :</span><span class="sxs-lookup"><span data-stu-id="49c08-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="49c08-119">Prise en main de SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="49c08-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="49c08-120">Gestion des groupes de sites SharePoint Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="49c08-121">Rapports pour Exchange Online :</span><span class="sxs-lookup"><span data-stu-id="49c08-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="49c08-122">Afficher les informations de boîte aux lettres Exchange Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="49c08-123">Affichage des rapports Exchange Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="related-topics"></a><span data-ttu-id="49c08-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49c08-124">Related topics</span></span>

[<span data-ttu-id="49c08-125">Gestion de Microsoft 365 à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="49c08-126">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="49c08-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="49c08-127">Gérer SharePoint Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="49c08-128">Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c08-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
