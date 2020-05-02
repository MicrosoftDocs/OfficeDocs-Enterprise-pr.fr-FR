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
# <a name="maintain-group-membership-with-office-365-powershell"></a>Mettre à jour l’appartenance au groupe avec Office 365 PowerShell

Vous pouvez utiliser Office 365 PowerShell comme alternative au centre d’administration de Microsoft 365 pour gérer l’appartenance au groupe dans Office 365. 

> [!TIP]
> Pour générer des commandes PowerShell prêtes à l’emploi en spécifiant des noms de comptes et de groupes d’utilisateurs, utilisez ce [classeur Microsoft Excel de maintenance de groupe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx). 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisez le module Azure Active Directory PowerShell pour Graph
Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Ajouter ou supprimer des comptes d’utilisateurs en tant que membres d’un groupe

**Pour ajouter un compte d’utilisateur par son UPN**, renseignez le nom d’utilisateur du compte d’utilisateur (UPN) (exemple : belindan@contoso.com) et le nom d’affichage du groupe, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou dans l’environnement de script intégré PowerShell (ISE).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour ajouter un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour supprimer un compte d’utilisateur par son UPN**, renseignez l’UPN du compte d’utilisateur (par exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour supprimer un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Ajouter ou supprimer des groupes en tant que membres d’un groupe

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Office 365 ne le peuvent pas. Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.

**Pour ajouter un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez ajouter et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour supprimer un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez supprimer et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Ajouter ou supprimer des comptes d’utilisateurs en tant que membres d’un groupe

**Pour ajouter un compte d’utilisateur par son UPN**, renseignez le nom d’utilisateur du compte d’utilisateur (UPN) (exemple : belindan@contoso.com) et le nom d’affichage du groupe, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour ajouter un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour supprimer un compte d’utilisateur par son UPN**, renseignez l’UPN du compte d’utilisateur (par exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Pour supprimer un compte d’utilisateur par son nom d’affichage**, renseignez le nom d’affichage du compte d’utilisateur (par exemple : Belinda Newman) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Ajouter ou supprimer des groupes en tant que membres d’un groupe

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Office 365 ne le peuvent pas. Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.

**Pour ajouter un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez ajouter et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Pour supprimer un groupe par son nom d’affichage**, renseignez le nom d’affichage du groupe que vous allez supprimer et le nom d’affichage du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

