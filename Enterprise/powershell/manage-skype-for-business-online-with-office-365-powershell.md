---
title: Gestion de Skype Entreprise Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592208"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Gestion de Skype Entreprise Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’une des tâches principales de tout administrateur Skype Entreprise Online est de gérer les stratégies. Bien que vous puissiez effectuer certaines de ces tâches dans le Centre d’administration Microsoft 365, d’autres tâches sont beaucoup plus rapides et plus simples à exécuter dans PowerShell. 

## <a name="before-you-start"></a>Avant de commencer

Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366), puis redémarrez votre ordinateur.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Connectez-vous à l’aide du nom et du mot de passe du compte d'administrateur Skype Entreprise Online

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez le nom et le mot de passe de votre compte d'administrateur Skype Entreprise Online, puis cliquez sur **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Connectez-vous à l’aide du compte d'administrateur Skype Entreprise Online avec l’authentification multifacteur

1. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. Lorsque vous y êtes invité par la commande **New-CsOnlineSession**, entrez le nom de votre compte d'administrateur Skype Entreprise Online.

3. Dans la boîte de dialogue **Vous connecter à votre compte**, tapez votre mot de passe d’administrateur Skype Entreprise Online, puis cliquez sur **Connexion**.

4. Suivez les instructions de la boîte de dialogue **Vous connecter à votre compte** pour fournir des informations d’authentification supplémentaires, telles qu’un code de vérification, puis cliquez sur **Vérifier**.

Pour plus d’informations, voir les rubriques suivantes :
  
- [Gestion des stratégies Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

[Références sur l’applet de commande Skype Entreprise PowerShell](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

