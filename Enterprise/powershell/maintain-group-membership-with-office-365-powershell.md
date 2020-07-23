---
title: Mettre à jour l’appartenance au groupe Microsoft 365 avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
description: Découvrez comment utiliser PowerShell pour gérer l’appartenance aux groupes Microsoft 365.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230650"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a>Mettre à jour l’appartenance au groupe Microsoft 365 avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 comme alternative au centre d’administration Microsoft 365 pour gérer l’appartenance au groupe dans Microsoft 365. 

> [!TIP]
> Pour générer des commandes PowerShell prêtes à l’emploi en spécifiant des noms de comptes et de groupes d’utilisateurs, utilisez ce [classeur Microsoft Excel de maintenance de groupe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx). 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph
Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

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

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Microsoft 365 ne le peuvent pas. Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


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

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Microsoft 365 ne le peuvent pas. Cette section contient les commandes PowerShell permettant d’ajouter ou de supprimer des groupes uniquement pour un groupe de sécurité.

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

[Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

