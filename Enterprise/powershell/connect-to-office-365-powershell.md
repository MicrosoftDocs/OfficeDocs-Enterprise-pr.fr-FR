---
title: Se connecter à Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Résumé: Connectez-vous à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer des tâches du centre d’administration à partir de la ligne de commande.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639775"
---
# <a name="connect-to-office-365-powershell"></a>Se connecter à Office 365 PowerShell

 **Résumé:** Connectez-vous à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer des tâches d’administration à partir de la ligne de commande.
  
Office 365 PowerShell vous permet de gérer vos paramètres Office 365 à partir de la ligne de commande. La connexion à Office 365 PowerShell est un processus simple qui vous permet d’installer les logiciels requis, puis de vous connecter à votre organisation Office 365. 

Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Office 365 et administrer les comptes d’utilisateurs, les groupes et les licences:

- Azure Active Directory PowerShell pour Graph (les cmdlets incluent **AzureAD** dans leur nom) 
- Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSOL** dans leur nom) 

À la date de cet article, le module Azure Active Directory PowerShell for Graph ne remplace pas entièrement les fonctionnalités des applets de commande du module Microsoft Azure Active Directory pour le module Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences. . Dans de nombreux cas, vous devez utiliser les deux versions. Vous pouvez installer les deux versions en toute sécurité sur le même ordinateur.

> [!TIP]
> **Vous débutez avec PowerShell?** Consultez une [Présentation vidéo de PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), qui vous a été proposée par LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d’exécution estimée : 5 minutes
    
- Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10, Windows 8,1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Utilisez une version 64 bits de Windows. Prise en charge de la version 32 bits le module Microsoft Azure Active Directory pour Windows PowerShell a été abandonné en octobre 2014.
    
-  Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365. Pour obtenir plus d’informations, consultez l’article [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Se connecter avec le module Azure Active Directory PowerShell pour Graph

Les commandes dans le module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ont **AzureAD** dans leur nom de cmdlet.

Pour les procédures nécessitant les nouvelles applets de commande dans le module Azure Active Directory PowerShell pour Graph, procédez comme suit pour installer le module et vous connecter à votre abonnement Office 365.

>[!Note]
>Consultez la rubrique [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) pour obtenir des informations sur la prise en charge de différentes versions de Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1. Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).
    
2. Dans la fenêtre de commande **administrateur: Windows PowerShell** , exécutez la commande suivante:
    
  ```
  Install-Module -Name AzureAD
  ```

Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **Y** , puis appuyez sur entrée.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2: Connectez-vous à Azure AD pour votre abonnement Office 365

Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom de compte et un mot de passe ou avec *l’authentification multifacteur (MFA)*, exécutez l’une de ces commandes à partir d’une invite de commandes Windows PowerShell (elle n’a pas besoin d’être élevée).

|||
|:-------|:-----|
| **Cloud Office 365** | **Command** |
| Office 365 dans le monde entier (+ GCC) | `Connect-AzureAD` |
| Office 365 géré par 21 VIANET | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 gouvernement américain DoD and Office 365 gouvernement américain GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Dans la boîte de dialogue **se connecter à votre compte** , entrez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.

Si vous utilisez l’authentification multiFACTEUR, suivez les instructions des boîtes de dialogue supplémentaires pour fournir des informations d’authentification supplémentaires, telles qu’un code de vérification.


Une fois la connexion établie, vous pouvez utiliser les nouvelles applets de commande pour le [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Se connecter au module Microsoft Azure Active Directory pour Windows PowerShell

Les commandes du module Microsoft Azure Active Directory pour Windows PowerShell ont **MSOL** dans leur nom de cmdlet.
    
### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1.  Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services: Assistant de [connexion Microsoft Online Services pour les professionnels de l’informatique RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installez le module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit:
    
  - Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).
  - Exécutez la commande **install-module MSONLINE** .
  - Si vous êtes invité à installer le fournisseur NuGet, tapez **Y** , puis appuyez sur entrée.
  - Si vous êtes invité à installer le module à partir de PSGallery, tapez **Y** , puis appuyez sur entrée.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2: Connectez-vous à Azure AD pour votre abonnement Office 365

Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom de compte et un mot de passe ou avec *l’authentification multifacteur (MFA)*, exécutez l’une de ces commandes à partir d’une invite de commandes Windows PowerShell (elle n’a pas besoin d’être élevée).

|||
|:-------|:-----|
| **Cloud Office 365** | **Command** |
| Office 365 dans le monde entier (+ GCC) | `Connect-MsolService` |
| Office 365 géré par 21 VIANET | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 gouvernement américain DoD and Office 365 gouvernement américain GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Dans la boîte de dialogue **se connecter à votre compte** , entrez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.

Si vous utilisez l’authentification multiFACTEUR, suivez les instructions des boîtes de dialogue supplémentaires pour fournir des informations d’authentification supplémentaires, telles qu’un code de vérification.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter une cmdlet Office 365 (par exemple, **Get-MsolUser** ) et à afficher les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- **Un problème courant est un mot de passe incorrect**. Exécutez à nouveau l’étape 2. et faites attention au nom d’utilisateur et au mot de passe que vous entrez.
    
- * *Le module Microsoft Azure Active Directory pour Windows PowerShell requiert Microsoft .net Framework 3,5.* la fonctionnalité x * est activée sur votre ordinateur * *. Il est probable que votre ordinateur dispose d’une version plus récente (par exemple, 4 ou 4,5.* x *), mais la compatibilité descendante avec les versions antérieures de .NET Framework peut être activée ou désactivée. Pour plus d’informations, consultez les rubriques suivantes :
    
  - Pour Windows Server 2012 ou Windows Server 2012 R2, consultez [la rubrique activer .NET Framework 3,5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités](https://go.microsoft.com/fwlink/p/?LinkId=532368) .
    
  - Pour Windows 7 ou Windows Server 2008 R2, consultez [l’impossibilité d’ouvrir le module Azure Active Directory pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Pour Windows 10, Windows 8,1 et Windows 8, consultez [la rubrique installer .NET Framework 3,5 sur Windows 10, windows 8,1 et Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **Votre version du module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le module Microsoft Azure Active Directory pour Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le module Microsoft Azure Active Directory pour Windows PowerShell et installez la version la plus récente à partir du lien à l’étape 1.
    
- **Si vous recevez une erreur de connexion, reportez-vous à cette rubrique:** [Erreur «Connect-MsolService: exception de type a été levée»](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Voir aussi

- [Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Mise en route d’Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

