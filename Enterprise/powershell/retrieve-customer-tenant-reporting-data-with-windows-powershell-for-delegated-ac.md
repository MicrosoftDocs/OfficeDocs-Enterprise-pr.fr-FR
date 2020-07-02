---
title: Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Résumé : Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.'
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998623"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="50aec-103">Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="50aec-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="50aec-104">Utilisez Windows PowerShell à distance pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.</span><span class="sxs-lookup"><span data-stu-id="50aec-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="50aec-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50aec-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="50aec-106">This lets partners collect and save the reporting data and then perform other operations on it.</span><span class="sxs-lookup"><span data-stu-id="50aec-106">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="50aec-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span><span class="sxs-lookup"><span data-stu-id="50aec-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="50aec-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span><span class="sxs-lookup"><span data-stu-id="50aec-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="50aec-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span><span class="sxs-lookup"><span data-stu-id="50aec-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="50aec-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span><span class="sxs-lookup"><span data-stu-id="50aec-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="50aec-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="50aec-111">Before you begin</span></span>

- <span data-ttu-id="50aec-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50aec-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span></span> <span data-ttu-id="50aec-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="50aec-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="50aec-114">Exécution de l’exemple Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="50aec-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="50aec-115">Une fois que vous avez ouvert une session Exchange Online à distance, exécutez la commande **Get-StaleMailboxReport** pour récupérer le rapport pour la plage de dates du 25/03/2015 au 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="50aec-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="50aec-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span><span class="sxs-lookup"><span data-stu-id="50aec-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span></span> <span data-ttu-id="50aec-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span><span class="sxs-lookup"><span data-stu-id="50aec-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="50aec-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50aec-118">See also</span></span>

#### 

[<span data-ttu-id="50aec-119">Service web de création de rapports Office 365</span><span class="sxs-lookup"><span data-stu-id="50aec-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="50aec-120">Cmdlets de création de rapports dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="50aec-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="50aec-121">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="50aec-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

