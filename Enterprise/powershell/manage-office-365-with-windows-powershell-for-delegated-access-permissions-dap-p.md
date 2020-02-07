---
title: Gestion d’Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Résumé :Partenaires de syndication et fournisseur de solutions cloud peut utiliser Windows PowerShell pour gérer les locataires de clients Office 365.
ms.openlocfilehash: 5e3fb67cad453593119347e2de07222f35d03f56
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844205"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="b6227-103">Gestion d’Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="b6227-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="b6227-104">**Résumé :** Partenaires de syndication et fournisseur de solutions cloud peut utiliser Windows PowerShell pour gérer les locataires de clients Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6227-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="b6227-105">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="b6227-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="b6227-106">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="b6227-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="b6227-107">Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients.</span><span class="sxs-lookup"><span data-stu-id="b6227-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="b6227-108">Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations AOBO (Administrer au nom de) sur les locations clientes et peuvent donc gérer les locations du client et créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="b6227-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="b6227-109">Au mieux, cette opération est difficile et fastidieuse dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b6227-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b6227-110">Cette opération est difficile et chronophage dans le Centre d'administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6227-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b6227-111">Il est beaucoup plus facile d'effectuer des tâches d'administration comme répertorier les codes TenantIds de tous les clients et leurs domaines ou identifier tous les utilisateurs d'une location d'un client et les licences qui leur sont affectées à l'aide de Windows PowerShell pour Office 365 Dans certains cas, il est possible d'effectuer ces tâches d'administration uniquement dans Windows PowerShell pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="b6227-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b6227-112">Voici quelques exemples de scénarios que les partenaires fournisseurs de solutions cloud et de syndication utilisent le plus souvent pour administrer les locations de leurs clients :</span><span class="sxs-lookup"><span data-stu-id="b6227-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="b6227-113">Gestion de clients Office 365 avec Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b6227-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="b6227-114">Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b6227-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="b6227-115">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b6227-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="b6227-116">Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b6227-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

