---
title: "Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, PowerShell, Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "Résumé : Utilisez Office 365 PowerShell et la cmdlet Add-MsolRoleMember pour attribuer des rôles aux comptes d'utilisateur."
ms.openlocfilehash: 68e8be24f1581aa3430bca95206ecc1b2512f09a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Attribuer des rôles à des comptes d’utilisateur avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell et la cmdlet **Add-MsolRoleMember** pour attribuer des rôles aux comptes d'utilisateur.
  
Vous pouvez rapidement et facilement attribuer des rôles aux comptes d'utilisateur à l'aide de Office 365 PowerShell en identifiant le nom d'affichage du compte d'utilisateur et le nom du rôle.
  
## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell à l'aide d'un compte d'administrateur global. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Pour une seule modification de rôle

Déterminez les éléments suivants :
  
- Le compte d’utilisateur que vous souhaitez configurer.
    
    Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Le rôle que vous souhaitez attribuer.
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous avez déterminé le nom d’affichage du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$dispName** et **$roleName**, remplacez le texte de description par leurs valeurs, supprimez les caractères \< et > et laissez les guillemets. Copiez les lignes modifiées et collez-les dans la fenêtre du Module Windows Azure Active Directory pour Windows PowerShell pour les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.
  
Voici un exemple d’un jeu de commandes terminées :
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Pour plusieurs modifications de rôle

Déterminez les éléments suivants :
  
- Les comptes d’utilisateur que vous souhaitez configurer.
    
    Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir une liste de comptes, utilisez cette commande :
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie le nom d'affichage de tous vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voici un exemple :
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur.
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ensuite, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs DisplayName et rôle Name. Voici un exemple :
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Voir aussi

#### 

[Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
#### 

[Add-MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

