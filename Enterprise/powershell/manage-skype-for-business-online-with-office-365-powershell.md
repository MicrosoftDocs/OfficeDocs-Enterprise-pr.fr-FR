---
title: Gestion de Skype Entreprise Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319235"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Gestion de Skype Entreprise Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.
  
Parmi les principales tâches de n’importe quel Skype pour l’administrateur d’entreprise en ligne est la gestion des stratégies. Bien que vous pouvez effectuer certaines de ces tâches dans le centre d’administration d’Office 365, les autres tâches sont beaucoup plus rapide et plus facile dans Office 365 PowerShell. 

## <a name="before-you-start"></a>Avant de commencer

Télécharger et installer le [Skype pour le module Business Connector en ligne](https://www.microsoft.com/en-us/download/details.aspx?id=39366), puis redémarrez votre ordinateur si vous y êtes invité.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Se connecter en utilisant un Skype pour le mot de passe et le nom du compte administrateur Business en ligne

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre Skype pour le nom du compte administrateur Business en ligne et le mot de passe, puis cliquez sur **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Se connecter en utilisant un Skype pour Business en ligne compte d’administrateur avec l’authentification multifacteur

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez votre Skype pour le nom du compte administrateur Business en ligne.

3. Dans la boîte de dialogue **se connecter à votre compte** , tapez votre Skype Business Online mot de passe administrateur, puis cliquez sur **se connecter**.

4. Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **Vérifier**.

Pour plus d'informations, consultez les rubriques suivantes :
  
- [Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>See also

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

