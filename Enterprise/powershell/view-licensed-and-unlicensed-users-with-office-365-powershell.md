---
title: Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.
ms.openlocfilehash: 79f7bf1966d515634c5fc038db650c19547259aa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730339"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="ef89a-103">Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef89a-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="ef89a-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.</span><span class="sxs-lookup"><span data-stu-id="ef89a-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="ef89a-p101">Il se peut que l'intégralité, une partie ou aucune des licences disponibles soit attribuée aux comptes d'utilisateurs de votre organisation Office 365 à partir des plans de gestion des licences disponibles dans votre organisation. Vous pouvez utiliser Office 365 PowerShell pour rechercher rapidement les utilisateurs avec ou sans licence dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="ef89a-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ef89a-107">Utilisez Azure Active Directory PowerShell pour le module de graphique</span><span class="sxs-lookup"><span data-stu-id="ef89a-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ef89a-108">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ef89a-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="ef89a-109">Pour afficher la liste de tous les comptes d’utilisateurs dans votre organisation qui n’a pas attribué un de vos plans de gestion des licences (les utilisateurs sans licence), exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ef89a-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="ef89a-110">Pour afficher la liste de tous les comptes d’utilisateurs dans votre organisation qui ont été affectés à un de vos plans de gestion des licences (utilisateurs sous licence), exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ef89a-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ef89a-111">Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef89a-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ef89a-112">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ef89a-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ef89a-113">Pour afficher la liste de tous les comptes d'utilisateurs et leur statut de licence dans votre organisation, exécutez la commande suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="ef89a-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="ef89a-114">Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ef89a-114">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ef89a-115">Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ef89a-115">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="ef89a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef89a-116">See also</span></span>

[<span data-ttu-id="ef89a-117">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef89a-117">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ef89a-118">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef89a-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ef89a-119">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="ef89a-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
