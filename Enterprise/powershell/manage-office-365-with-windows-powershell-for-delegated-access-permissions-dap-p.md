---
title: Gestion d’Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Résumé :Partenaires de syndication et fournisseur de solutions cloud peut utiliser Windows PowerShell pour gérer les locataires de clients Office 365.
ms.openlocfilehash: 93b323d8de7016008ba7e4f75ff4b1c011adb9f2
ms.sourcegitcommit: 509bcf92580d7a0bcebbf6f1d10311d6b0014984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "31992814"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="b62d3-103">Gestion d’Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="b62d3-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="b62d3-104">**Résumé :** Partenaires de syndication et fournisseur de solutions cloud peut utiliser Windows PowerShell pour gérer les locataires de clients Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62d3-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="b62d3-105">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="b62d3-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="b62d3-106">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="b62d3-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="b62d3-107">Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients.</span><span class="sxs-lookup"><span data-stu-id="b62d3-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="b62d3-108">Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations AOBO (Administrer au nom de) sur les locations clientes et peuvent donc gérer les locations du client et créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="b62d3-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="b62d3-109">Ainsi, ils peuvent administrer les locations clientes et créer des rapports les concernant.</span><span class="sxs-lookup"><span data-stu-id="b62d3-109">At best, this is difficult and time consuming to do in the Office 365 admin center.</span></span> <span data-ttu-id="b62d3-110">Cette opération est difficile et chronophage dans le Centre d'administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62d3-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b62d3-111">Il est beaucoup plus facile d'effectuer des tâches d'administration comme répertorier les codes TenantIds de tous les clients et leurs domaines ou identifier tous les utilisateurs d'une location d'un client et les licences qui leur sont affectées à l'aide de Windows PowerShell pour Office 365 Dans certains cas, il est possible d'effectuer ces tâches d'administration uniquement dans Windows PowerShell pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62d3-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b62d3-112">Voici quelques exemples de scénarios que les partenaires fournisseurs de solutions cloud et de syndication utilisent le plus souvent pour administrer les locations de leurs clients :</span><span class="sxs-lookup"><span data-stu-id="b62d3-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="b62d3-113">Gestion de clients Office 365 avec Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b62d3-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="b62d3-114">Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b62d3-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="b62d3-115">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b62d3-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="b62d3-116">Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b62d3-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

