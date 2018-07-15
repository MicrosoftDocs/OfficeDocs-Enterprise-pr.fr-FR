---
title: Se connecter à Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Résumé : Se connecter à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches du centre d’administration à partir de la ligne de commande.'
ms.openlocfilehash: b603e019564f85d490dd560bda9967c9bb164d4b
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319245"
---
# <a name="connect-to-office-365-powershell"></a>Se connecter à Office 365 PowerShell

 **Résumé :** Se connecter à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches d’administration à partir de la ligne de commande.
  
Office 365 PowerShell vous permet pour gérer vos paramètres de Office 365 à partir de la ligne de commande. Connexion à Office 365 PowerShell est un processus en trois étapes simple où vous installez les logiciels requis, exécuter des logiciels requis et puis connectez à votre organisation Office 365. 

  
> [!TIP]
> **Nouveau PowerShell ?** Consultez une [Présentation vidéo de PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), proposée par apprentissage LinkedIn. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d'exécution estimée : 5 minutes
    
- Vous pouvez utiliser les versions de Windows suivantes :
    
  - 10 Windows, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Utilisez une version 64 bits de Windows. Prise en charge pour la version 32 bits du Microsoft Azure Active Directory Module pour Windows PowerShell a été abandonné en octobre de 2014.
    
-  Ces procédures sont destinés aux utilisateurs qui sont membres d’un rôle d’administration d’Office 365. Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Se connecter avec le Module d’Active Directory de Microsoft Azure pour Windows PowerShell

Commandes dans le Microsoft Azure Active Directory Module pour Windows PowerShell ont **Msol** dans leur nom de l’applet de commande.
    
### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1.  Installer la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant connexion de Microsoft Online Services pour les professionnels de l’informatique RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installer le Microsoft Azure Active Directory Module pour Windows PowerShell en suivant ces étapes :
    
  - Ouvrez une invite de commandes PowerShell au niveau administrateur.
  - Exécutez la commande **Install-Module MSOnline** .
  - Si vous êtes invité à installer le fournisseur NuGet, tapez **o** et appuyez sur ENTRÉE.
  - Si vous êtes invité à installer le module de PSGallery, tapez **o** et appuyez sur ENTRÉE.
  - Après l’installation, fermez la fenêtre de commande PowerShell.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2 : Se connecter à Azure AD pour votre abonnement à Office 365

Pour vous connecter uniquement avec un *nom de compte et un mot de passe* :
  
1. Exécutez une invite de commandes Windows PowerShell.
2. Dans la fenêtre de commande **Windows PowerShell** , exécutez les commandes suivantes :
    
  ```
  $UserCredential = Get-Credential
  Connect-MsolService -Credential $UserCredential

  ```

3. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.
    
Pour se connecter avec *l’authentification multifacteur (MFA)*:
  
1. Exécutez une invite de commandes Windows PowerShell.
2. Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez la commande suivante.
    
  ```
  Connect-MsolService
  ```

3. Dans la boîte de dialogue **Windows Azure Active Directory PowerShell** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.
    
4. Suivez les instructions de la boîte de dialogue **Azure Active Directory PowerShell** pour fournir les informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **Se connecter**.
    
### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Si vous ne recevez des erreurs, vous connecté avec succès. Un test rapide consiste à exécuter une applet de commande Office 365 — par exemple, **Get-MsolUser** — et afficher les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- **Un mot de passe incorrect est un problème courant**. Exécutez à nouveau l’étape 3 et portez une attention particulière au nom d’utilisateur et au mot de passe que vous saisissez.
    
- * *Le Microsoft Azure Active Directory Module pour Windows PowerShell requiert que Microsoft .NET Framework 3.5.* fonctionnalité de x est activée sur votre ordinateur **. Il est probable qu’une version plus récente est installée sur votre ordinateur (par exemple, 4 ou 4.5.* x *), mais à compatibilité descendante compatibilité avec les versions antérieures du .NET Framework peut être activée ou désactivée. Pour plus d’informations, voir les rubriques suivantes :
    
  - Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Activer .NET Framework 3.5 à l’aide de l’ajout de rôles et fonctionnalités Assistant](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Pour Windows 8 ou Windows 8.1, voir [installation de .NET Framework 3.5 sur Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Pour Windows 7 ou Windows Server 2008 R2, voir [vous ne peuvent pas ouvrir les Azure Active Directory Module pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Votre version de la Microsoft Azure Active Directory Module pour Windows PowerShell est peut-être obsolète.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le Microsoft Azure Active Directory Module pour Windows PowerShell :
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Microsoft Azure Active Directory Module pour Windows PowerShell et installez la dernière version à partir du lien à l’étape 1.
    
- **Si vous recevez une erreur de connexion, consultez la rubrique suivante :** [« Connect-MsolService : a levé une Exception de type « erreur](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
<a name="ConnectV2"> </a>
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Se connecter avec Azure Active Directory PowerShell pour le module de graphique

Commandes dans le module [Azure Active Directory PowerShell pour le module graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ont **AzureAD** dans leur nom de l’applet de commande.

Pour les procédures qui nécessitent les nouvelles applets de commande dans Azure Active Directory PowerShell pour module graphique, suivez ces étapes pour installer le module et se connecter à votre abonnement Office 365.

>[!Note]
>Pour plus d’informations sur la prise en charge pour les différentes versions de Microsoft Windows, voir [Windows Azure Active Directory PowerShell pour le module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.

  
1. Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutée Windows PowerShell en tant qu’administrateur).
    
2. Dans la **administrateur : Windows PowerShell** fenêtre de commande, exécutez la commande suivante :
    
  ```
  Install-Module -Name AzureAD 
  ```

Si vous y êtes invité sur l’installation d’un module à partir d’un référentiel non approuvé, tapez **o** et appuyez sur ENTRÉE.


### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Étape 2 : Se connecter à Azure AD pour votre abonnement à Office 365

Pour se connecter à votre abonnement à Office 365 avec un *nom de compte et mot de passe*:
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential

```

Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.
    
Pour se connecter à votre abonnement à Office 365 avec *l’authentification multifacteur (MFA)*:

```
Connect-AzureAD
```

Dans la boîte de dialogue **Windows Azure Active Directory PowerShell** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.
    
Suivez les instructions de la boîte de dialogue **Azure Active Directory PowerShell** pour fournir les informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **Se connecter**.
    
Une fois connecté, vous pouvez utiliser les nouvelles applets de commande pour [Azure Active Directory PowerShell pour le module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>See also

- [Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
- [Connexion à tous les services Office 365 à l'aide d'une seule fenêtre Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connecter-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

