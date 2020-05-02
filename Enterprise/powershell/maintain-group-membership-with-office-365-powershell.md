---
title: Mettre à jour l’appartenance au groupe avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Découvrez comment utiliser Office 365 PowerShell pour gérer l’appartenance à des groupes pour Office 365.
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004627"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="ccaa0-103">Mettre à jour l’appartenance au groupe avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccaa0-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="ccaa0-104">Vous pouvez utiliser Office 365 PowerShell comme alternative au centre d’administration de Microsoft 365 pour gérer l’appartenance au groupe dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="ccaa0-105">Pour générer des commandes PowerShell prêtes à l’emploi en spécifiant des noms de comptes et de groupes d’utilisateurs, utilisez ce [classeur Microsoft Excel de maintenance de groupe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="ccaa0-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ccaa0-106">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="ccaa0-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="ccaa0-107">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ccaa0-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="ccaa0-108">Ajouter ou supprimer des comptes d’utilisateurs en tant que membres d’un groupe</span><span class="sxs-lookup"><span data-stu-id="ccaa0-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="ccaa0-109">**Pour ajouter un compte d’utilisateur par son UPN**, renseignez le nom d’utilisateur du compte d’utilisateur (UPN) (exemple : belindan@contoso.com) et le nom d’affichage du groupe, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou dans l’environnement de script intégré PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="ccaa0-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-110">**Pour ajouter un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-111">**Pour supprimer un compte d’utilisateur par son UPN**, renseignez l’UPN du compte d’utilisateur (par exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-112">**Pour supprimer un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="ccaa0-113">Ajouter ou supprimer des groupes en tant que membres d’un groupe</span><span class="sxs-lookup"><span data-stu-id="ccaa0-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="ccaa0-114">Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="ccaa0-115">Toutefois, les groupes Office 365 ne le peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="ccaa0-116">Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="ccaa0-117">**Pour ajouter un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez ajouter et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-118">**Pour supprimer un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez supprimer et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ccaa0-119">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ccaa0-120">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ccaa0-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="ccaa0-121">Ajouter ou supprimer des comptes d’utilisateurs en tant que membres d’un groupe</span><span class="sxs-lookup"><span data-stu-id="ccaa0-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="ccaa0-122">**Pour ajouter un compte d’utilisateur par son UPN**, renseignez le nom d’utilisateur du compte d’utilisateur (UPN) (exemple : belindan@contoso.com) et le nom d’affichage du groupe, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-123">**Pour ajouter un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-124">**Pour supprimer un compte d’utilisateur par son UPN**, renseignez l’UPN du compte d’utilisateur (par exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="ccaa0-125">**Pour supprimer un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="ccaa0-126">Ajouter ou supprimer des groupes en tant que membres d’un groupe</span><span class="sxs-lookup"><span data-stu-id="ccaa0-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="ccaa0-127">Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="ccaa0-128">Toutefois, les groupes Office 365 ne le peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="ccaa0-129">Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="ccaa0-130">**Pour ajouter un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez ajouter et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="ccaa0-131">**Pour supprimer un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez supprimer et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccaa0-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="ccaa0-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccaa0-132">See also</span></span>

[<span data-ttu-id="ccaa0-133">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccaa0-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ccaa0-134">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccaa0-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ccaa0-135">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="ccaa0-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

