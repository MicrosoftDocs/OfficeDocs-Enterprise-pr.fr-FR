---
title: Récupérer des données de création de rapports de client avec Windows PowerShell pour les partenaires DAP
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
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Résumé : Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.'
ms.openlocfilehash: 69c441f1e241f964ec3ef24a915331a8980a4794
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606240"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="82522-103">Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="82522-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="82522-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="82522-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="82522-105">Utilisez Windows PowerShell à distance pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.</span><span class="sxs-lookup"><span data-stu-id="82522-105">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="82522-106">Les partenaires de syndication et fournisseur de solutions Cloud peuvent accéder aux données qui composent les rapports client directement via Windows PowerShell à distance pour Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82522-106">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remote Windows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="82522-107">Cela permet aux partenaires de recueillir et d'enregistrer les données des rapports et de s'en servir pour effectuer d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="82522-107">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="82522-108">Après avoir ouvert une connexion à distance, la récupération des données de création de rapports sur une location client est identique à l'exécution de n'importe quelle cmdlet sur la location d'un client.</span><span class="sxs-lookup"><span data-stu-id="82522-108">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="82522-109">Dans cet article, vous utilisez Windows PowerShell à distance pour Exchange Online pour vous connecter à un client unique et récupérer un rapport.</span><span class="sxs-lookup"><span data-stu-id="82522-109">In this article, you use remote Windows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="82522-110">Par défaut, Windows PowerShell ne prend pas en charge le regroupement des données des rapports à partir de plusieurs locations de clients.</span><span class="sxs-lookup"><span data-stu-id="82522-110">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="82522-111">Les rapports que vous récupérez avec cette procédure ne sont destinés qu'aux organisations déléguées ( _DelegatedOrg_) auxquelles vous vous connectez.</span><span class="sxs-lookup"><span data-stu-id="82522-111">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="82522-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="82522-112">Before you begin</span></span>

- <span data-ttu-id="82522-p103">Vous devez vous connecter à votre locataire Exchange Online à l'aide de Remote Windows PowerShell Pour plus d'informations, voir [Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="82522-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="82522-115">Exécution de l’exemple Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="82522-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="82522-116">Une fois que vous avez ouvert une session Exchange Online à distance, exécutez la commande **Get-StaleMailboxReport** pour récupérer le rapport pour la plage de dates du 25/03/2015 au 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="82522-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="82522-p104">Il existe plusieurs autres cmdlets que vous pouvez utiliser pour la création de rapports pour Exchange Online, Lync Online et SharePoint Online, ainsi que d'autres cmdlets pour le suivi des messages. Pour en savoir plus sur les cmdlets de création de rapports disponibles et le service web de création de rapports Office 365, voir les rubriques dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="82522-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="82522-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82522-119">See also</span></span>

#### 

[<span data-ttu-id="82522-120">Service web de création de rapports Office 365</span><span class="sxs-lookup"><span data-stu-id="82522-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="82522-121">Cmdlets de création de rapports dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="82522-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="82522-122">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="82522-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

