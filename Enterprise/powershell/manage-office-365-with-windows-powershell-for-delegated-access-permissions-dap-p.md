---
title: Gérer Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 'Résumé : les partenaires de syndication et fournisseur de solutions Cloud peuvent utiliser Windows PowerShell pour gérer les locataires de clients Microsoft 365.'
ms.openlocfilehash: 22fd26fb89d15cc036d52ed49ec61319c7e13a52
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230480"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ed429-103">Gérer Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="ed429-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="ed429-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="ed429-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ed429-105">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="ed429-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="ed429-106">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="ed429-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="ed429-107">Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients.</span><span class="sxs-lookup"><span data-stu-id="ed429-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="ed429-108">Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.</span><span class="sxs-lookup"><span data-stu-id="ed429-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="ed429-109">Au mieux, cette opération est difficile et fastidieuse dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ed429-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="ed429-110">Il est beaucoup plus facile d’effectuer des tâches d’administration, comme la mise en vente de tous les clients **TenantIds** et leurs domaines ou l’identification de tous les utilisateurs d’un client, ainsi que les licences affectées à l’aide de PowerShell pour Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ed429-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="ed429-111">Dans certains cas, il est possible d’effectuer ces tâches d’administration uniquement dans PowerShell pour Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ed429-111">In some cases, it is possible to do these administrative tasks only in PowerShell for Microsoft 365.</span></span> <span data-ttu-id="ed429-112">Voici quelques exemples de scénarios que les partenaires fournisseurs de solutions cloud et de syndication utilisent le plus souvent pour administrer les locations de leurs clients :</span><span class="sxs-lookup"><span data-stu-id="ed429-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="ed429-113">Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="ed429-113">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="ed429-114">Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="ed429-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="ed429-115">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="ed429-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="ed429-116">Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="ed429-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

