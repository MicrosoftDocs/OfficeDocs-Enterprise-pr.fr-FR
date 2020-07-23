---
title: Gestion de Skype entreprise Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour gérer des stratégies Skype entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230440"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Gestion de Skype entreprise Online avec PowerShell

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Une des tâches principales de tout administrateur de Skype Entreprise Online est la gestion des stratégies. Bien que vous puissiez effectuer certaines de ces tâches dans le centre d’administration 365 de Microsoft, les autres tâches sont beaucoup plus rapides et plus faciles dans PowerShell. 

## <a name="before-you-start"></a>Avant de commencer

Téléchargez et installez le [module du connecteur Skype entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366), puis redémarrez votre ordinateur.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Se connecter à l’aide du nom et du mot de passe d’un compte d’administrateur Skype entreprise Online

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Dans la boîte de dialogue **demande d’informations d’identification Windows PowerShell** , tapez le nom et le mot de passe de votre compte d’administrateur Skype entreprise Online, puis cliquez sur **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Se connecter à l’aide d’un compte d’administrateur Skype entreprise Online avec l’authentification multifacteur

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Lorsque vous y êtes invité par la commande **New-CsOnlineSession** , entrez le nom de votre compte d’administrateur Skype entreprise online.

3. Dans la boîte de dialogue **se connecter à votre compte** , saisissez votre mot de passe d’administrateur Skype entreprise Online, puis cliquez sur **se connecter**.

4. Suivez les instructions de la boîte de dialogue **se connecter à votre compte** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **vérifier**.

Pour plus d’informations, voir les rubriques suivantes :
  
- [Gestion des stratégies Skype entreprise Online avec PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Affecter des stratégies Skype entreprise Online par utilisateur avec PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Voir aussi

[Gérer Microsoft 365 avec PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

[Références de l’applet de commande PowerShell Skype entreprise](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

