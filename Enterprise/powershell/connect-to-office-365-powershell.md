---
title: Se connecter à PowerShell Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/31/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Connectez-vous à votre organisation Office 365 à l’aide de PowerShell Office 365 pour effectuer les tâches d’administration à partir de la ligne de commande.
ms.openlocfilehash: 642016f734a2a9d7e490d5905a3ed93d7f330ca9
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068756"
---
# <a name="connect-to-office-365-powershell"></a>Se connecter à PowerShell Office 365

PowerShell Office 365 vous permet de gérer vos paramètres Office 365 à partir de la ligne de commande. La connexion à PowerShell Office 365 est un processus simple dans le cadre duquel vous installez les logiciels requis, puis vous connectez à votre organisation Office 365. 

Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Office 365 et administrer les comptes d’utilisateurs, les groupes et les licences :

- Azure Active Directory PowerShell pour Graph (les cmdlets **incluent** AzureAD dans leur nom) ;
- Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSol** dans leur nom). 

Au moment de rédiger cet article, le module Azure Active Directory PowerShell pour Graph ne remplace pas complètement la fonctionnalité des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences. Dans de nombreux cas, vous devez utiliser les deux versions. Vous pouvez installer en toute sécurité les deux versions sur le même ordinateur.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1

    > [!NOTE]
    > Pour le module Graph d'Azure Active Directory PowerShell, vous devez utiliser PowerShell version 5.1 ou ultérieure. Vous devez utiliser PowerShell version 5.1 ou ultérieure jusqu’à PowerShell version 6 pour le Module Microsoft Azure Active Directory pour Windows PowerShell. Vous ne pouvez pas utiliser la version 7 de PowerShell. Pour Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 et Windows Server 2008 R2 SP1, téléchargez et installez [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616). 
    
    > [!NOTE]
    > Utilisez une version 64 bits de Windows. Le support de la version 32 bits du Module Microsoft Azure Active Directory pour Windows PowerShell a cessé en octobre 2014.
    
Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365. Pour plus d’informations, voir [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Se connecter avec le module PowerShell Azure Active Directory pour Graph

Le nom des cmdlets du module Azure Active Directory PowerShell pour Graph contient la chaîne de caractères **AzureAD**. Vous pouvez installer le module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ou [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).

Dans le cadre des procédures qui requièrent les nouvelles cmdlets dans le module Microsoft Azure Active Directory PowerShell pour Graph, pour installer le module et vous connecter à votre abonnement Office 365, procédez comme suit.

>[!Note]
>Pour plus d’informations sur le support de différentes versions de Microsoft Windows, voir [Module Microsoft Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
>

### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1. Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).
    
2. Dans la fenêtre de commande **Administrateur : Windows PowerShell**, exécutez la commande suivante :
    
  ```powershell
  Install-Module -Name AzureAD
  ```

Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **O**, puis appuyez sur Entrée.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2 : se connecter à Azure AD pour votre abonnement Office 365

Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une authentification multifacteur (MFA), exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).

|||
|:-------|:-----|
| **Cloud Office 365** | **Commande** |
| Office 365 dans le monde (+GCC) | `Connect-AzureAD` |
| Office 365 géré par 21 ViaNet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Allemagne | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.

Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.

Une fois connecté, vous pouvez utiliser les cmdlets du [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Se connecter au Module Microsoft Azure Active Directory pour Windows PowerShell

Le nom des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell contient la chaîne de caractères **MSol**.

PowerShell version 7 ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets incluant **Msol** dans leur nom. Pour PowerShell version 7 ou ultérieure, vous devez utiliser le module Azure Active Directory PowerShell pour Graph ou Azure PowerShell.

PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell. 
    
### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1.  Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant de connexion Microsoft Online Services pour les professionnels des technologies de l’information RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :
    
  - Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).
  - Exécutez la commande **Install-Module MSOnline**.
  - Si vous êtes invité à installer le fournisseur NuGet, tapez **O**, puis appuyez sur Entrée.
  - Si vous êtes invité à installer le module à partir de PSGallery, tapez **O**, puis appuyez sur Entrée.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2 : se connecter à Azure AD pour votre abonnement Office 365

Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une authentification multifacteur (MFA), exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).

|||
|:-------|:-----|
| **Cloud Office 365** | **Commande** |
| Office 365 dans le monde (+GCC) | `Connect-MsolService` |
| Office 365 géré par 21 ViaNet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Allemagne | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.

Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Si aucun message d’erreur ne s’affiche, cela signifie que la connexion a été correctement établie. Pour effectuer un test rapide, vous pouvez exécuter une cmdlet Office 365 (par exemple, **Get-MsolUser**) et en examiner les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- **L’inexactitude du mot de passe est un problème courant**. Exécutez à nouveau l’étape 2 en étant attentif aux nom d’utilisateur et mot de passe que vous entrez.
    
- **Le Module Microsoft Azure Active Directory pour Windows PowerShell requiert que la fonctionnalité Microsoft .NET Framework 3.5.* x* soit activée sur votre ordinateur**. Il est probable qu’une version plus récente soit installée sur votre ordinateur (par exemple, 4 ou 4.5.* x*), mais la compatibilité descendante avec des versions antérieures du .NET Framework peut être activée ou désactivée. Pour plus d’informations, voir les rubriques suivantes :
    
  - Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Activer .NET Framework 3.5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités).
    
  - For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Pour Windows 10, Windows 8.1 et Windows 8, voir [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10).

  
- **Votre version du Module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.** Pour vérifier cela, exécutez la commande suivante dans PowerShell Office 365 ou le Module Microsoft Azure Active Directory pour Windows PowerShell :
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Module Microsoft Azure Active Directory pour Windows PowerShell, puis installez la dernière version à partir du lien fourni à l’étape 1.

- **Si un message d’erreur de connexion s’affiche, voir ** [Erreur « Connect-MsolService: Une exception de type a été levée »](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
- **Si vous recevez un message d’erreur « Get-Item : Chemin introuvable », utilisez la commande suivante :** 

  ```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
 
```

## <a name="see-also"></a>Voir également

- [Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Mise en route d’Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
