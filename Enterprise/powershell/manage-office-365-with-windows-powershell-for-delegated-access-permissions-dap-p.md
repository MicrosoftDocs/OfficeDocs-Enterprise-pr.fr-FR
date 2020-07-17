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
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998220"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="b7771-103">Gérer Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="b7771-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="b7771-104">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="b7771-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="b7771-105">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="b7771-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="b7771-106">Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients.</span><span class="sxs-lookup"><span data-stu-id="b7771-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="b7771-107">Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.</span><span class="sxs-lookup"><span data-stu-id="b7771-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="b7771-108">Au mieux, cette opération est difficile et fastidieuse dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b7771-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b7771-109">Cette opération est difficile et chronophage dans le Centre d'administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="b7771-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b7771-110">Il est beaucoup plus facile d'effectuer des tâches d'administration comme répertorier les codes TenantIds de tous les clients et leurs domaines ou identifier tous les utilisateurs d'une location d'un client et les licences qui leur sont affectées à l'aide de Windows PowerShell pour Office 365 Dans certains cas, il est possible d'effectuer ces tâches d'administration uniquement dans Windows PowerShell pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="b7771-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="b7771-111">Voici quelques exemples de scénarios que les partenaires fournisseurs de solutions cloud et de syndication utilisent le plus souvent pour administrer les locations de leurs clients :</span><span class="sxs-lookup"><span data-stu-id="b7771-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="b7771-112">Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="b7771-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="b7771-113">Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b7771-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="b7771-114">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b7771-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="b7771-115">Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué</span><span class="sxs-lookup"><span data-stu-id="b7771-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

