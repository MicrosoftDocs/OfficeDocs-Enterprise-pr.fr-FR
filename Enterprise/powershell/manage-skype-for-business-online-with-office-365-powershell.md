---
title: Gestion de Skype Entreprise Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: 80d8308a1c9b32fcafd47d1df2f699141e41accd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782134"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gestion de Skype Entreprise Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.
  
Une des tâches principales de tout administrateur de Skype Entreprise Online est la gestion des stratégies. Bien que vous puissiez effectuer certaines de ces tâches dans le Centre d’administration Microsoft 365, d’autres tâches sont beaucoup plus rapides et plus simples à exécuter dans Office 365 PowerShell. 

## <a name="before-you-start"></a>Avant de commencer

Téléchargez et installez le [module du connecteur Skype entreprise Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366), puis redémarrez votre ordinateur si vous y êtes invité.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Se connecter à l’aide du nom et du mot de passe d’un compte d’administrateur Skype entreprise Online

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Dans la boîte de dialogue **demande d’informations d’identification Windows PowerShell** , tapez le nom et le mot de passe de votre compte d’administrateur Skype entreprise Online, puis cliquez sur **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Se connecter à l’aide d’un compte d’administrateur Skype entreprise Online avec l’authentification multifacteur

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez le nom de votre compte d’administrateur Skype entreprise online.

3. Dans la boîte de dialogue **se connecter à votre compte** , saisissez votre mot de passe d’administrateur Skype entreprise Online, puis cliquez sur **se connecter**.

4. Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **vérifier**.

Pour plus d'informations, consultez les rubriques suivantes :
  
- [Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Voir aussi

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d’Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Références de l’applet de commande PowerShell Skype entreprise](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

