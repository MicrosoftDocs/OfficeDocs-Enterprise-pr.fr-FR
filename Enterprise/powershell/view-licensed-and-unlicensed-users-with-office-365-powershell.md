---
title: Afficher les utilisateurs titulaires d’une licence et de Microsoft 365 sans licence avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explique comment utiliser PowerShell pour afficher des comptes d’utilisateurs Microsoft 365 sans licence ou sous licence.
ms.openlocfilehash: 02b1f76bab0e64e4e7e72f5e5556f5047d956d11
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230250"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a><span data-ttu-id="da833-103">Afficher les utilisateurs titulaires d’une licence et de Microsoft 365 sans licence avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="da833-103">View licensed and unlicensed Microsoft 365 users with PowerShell</span></span>

<span data-ttu-id="da833-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="da833-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="da833-105">Les comptes d’utilisateur de votre organisation Microsoft 365 peuvent avoir certaines, toutes ou aucune des licences disponibles qui leur sont attribuées à partir des plans de gestion des licences disponibles dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="da833-105">User accounts in your Microsoft 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization.</span></span> <span data-ttu-id="da833-106">Vous pouvez utiliser PowerShell pour Microsoft 365 pour trouver rapidement les utilisateurs sous licence et sans licence de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="da833-106">You can use PowerShell for Microsoft 365 to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="da833-107">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="da833-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="da833-108">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="da833-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="da833-109">Pour afficher la liste de tous les comptes d’utilisateur de votre organisation auxquels aucun de vos plans de licence n’a été attribué (utilisateurs sans licence), exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="da833-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="da833-110">Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation auxquels ont été affectés des plans de gestion des licences (utilisateurs sous licence), exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="da833-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="da833-111">Pour répertorier tous les utilisateurs de votre abonnement, utilisez la `Get-AzureAdUser -All $true` commande.</span><span class="sxs-lookup"><span data-stu-id="da833-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="da833-112">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da833-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="da833-113">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="da833-113">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="da833-114">Pour afficher la liste de tous les comptes d’utilisateurs et leur statut de licence dans votre organisation, exécutez la commande suivante dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="da833-114">To view the list of all user accounts and their licensing status in your organization, run the following command in PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="da833-115">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="da833-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="da833-116">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da833-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="da833-117">Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="da833-117">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="da833-118">Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="da833-118">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="da833-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da833-119">See also</span></span>

[<span data-ttu-id="da833-120">Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="da833-120">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="da833-121">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="da833-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="da833-122">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="da833-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
