---
title: "Se connecter à Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "Résumé : Connexion à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches de centre d’administration Office 365 à partir de la ligne de commande."
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a>Se connecter à Office 365 PowerShell

 **Résumé :** Se connecter à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches d’administration Office 365 à partir de la ligne de commande.
  
Office 365 PowerShell vous permet pour gérer vos paramètres Office 365 à partir de la ligne de commande. Se connecter à Office 365 PowerShell est un processus en trois étapes simple où vous installez les logiciels requis, exécuter les logiciels requis et puis connectez à votre organisation d’Office 365. 

Notez que ces instructions de connexion sont les mêmes que ceux de la rubrique [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Nouveau PowerShell ?** Voir une [Présentation vidéo de PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), proposée par formation de LinkedIn. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer ?

- Durée d’exécution estimée : 5 minutes
    
- Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Utilisez une version 64 bits de Windows. Prise en charge de la version 32 bits du Microsoft Azure Active Directory Module pour Windows PowerShell a été interrompu en octobre de 2014.
    
-  L’Office 365 fonctionne ou l’école de compte que vous l’utilisation de ces procédures doit pour être membre d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).
    
## <a name="step-1-install-required-software"></a>Étape 1 : Installer les logiciels requis

Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.
  
1.  Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Microsoft Online Services - Assistant de connexion pour la version RTW de professionnels de l’informatique](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installez la version 64 bits de la Microsoft Azure Active Directory Module pour Windows PowerShell avec ces étapes :
    
  - Ouvrez la page web de [Connexion à Active Directory Azure](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) .
    
  - Dans **les fichiers de téléchargement** en bas de la page, cliquez sur **Télécharger** le fichier **AdministrationConfig-V1.1.166.0-GA.msi** et installez-le.
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>Étape 2 : Ouvrir le module Windows Azure Active Directory

1. Recherchez et ouvrez le Microsoft Azure Active Directory Module pour Windows PowerShell en utilisant l’une des méthodes suivantes selon votre version de Windows :
    
  - **Menu Démarrer** À partir du bureau, cliquez sur **Démarrer**et tapez Azure.
    
  - **Menu Démarrer de N°** ForAzure de recherche à l’aide d’une des méthodes suivantes :
    
  - Sur l’écran de démarrage, cliquez sur une zone vide et tapez Azure.
    
  - Sur le bureau ou l’écran de démarrage, appuyez sur la touche Windows + touche Q. Dans l’icône de recherche, tapez Azure.
    
  - Sur le bureau ou l’écran de démarrage, déplacez votre curseur dans le coin supérieur droit, ou faites défiler le bord droit de l’écran pour afficher les icônes de gauche. Cliquez sur l’icône de recherche et tapez **Azure**.
    
2. Dans les résultats, cliquez sur **Microsoft Azure Active Directory Module pour Windows PowerShell**.
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>Étape 3 : Se connecter à votre abonnement à Office 365
<a name="step3"> </a>

Se connecter avec seulement un *nom de compte et de mot de passe* :
  
1. Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez les commandes suivantes.
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.
    
Se connecter avec *l’authentification par plusieurs facteur (AMF)* :
  
1. Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez la commande suivante.
    
  ```
  Connect-MsolService
  ```

2. Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.
    
3. Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.
    
## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?
<a name="step3"> </a>

Si vous ne recevez pas d’erreurs, vous est connecté correctement. Un test rapide est d’exécuter une applet de commande d’Office 365, par exemple, **Get-MsolUser** et afficher les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- **Un problème courant est un mot de passe incorrect**. Réexécutez l’étape 3. et faites attention pour le nom d’utilisateur et le mot de passe que vous entrez.
    
- **Le Microsoft Azure Active Directory Module pour Windows PowerShell requiert que le Microsoft.NET Framework 3.5. fonctionnalité de _x_ est activée sur votre ordinateur**. Il est probable que votre ordinateur dispose d’une version plus récente est installée (par exemple, 4 ou 4.5. _x_), mais en arrière la compatibilité avec les versions antérieures du.NET Framework peut être activée ou désactivée. Pour plus d’informations, consultez les rubriques suivantes :
    
  - Pour Windows Server 2012 ou de Windows Server 2012 R2, voir [Activer le.NET Framework 3.5 à l’aide de l’ajout de rôles et fonctionnalités Assistant](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Pour Windows 8 ou Windows 8.1, consultez [installer le 3.5 de.NET Framework sur Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Pour Windows 7 ou Windows Server 2008 R2, consultez [Impossible d’ouvrir le Module Azure pour annuaire Active pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Votre version de la Microsoft Azure Active Directory Module pour Windows PowerShell est peut-être périmée.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le Microsoft Azure Active Directory Module pour Windows PowerShell :
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si le numéro de version retourné est inférieur à la valeur 1.0.8070.2, désinstallez le Microsoft Azure Active Directory Module pour Windows PowerShell et installer la dernière version à partir du lien à l’étape 1.
    
- **Si vous recevez une erreur de connexion, consultez la rubrique suivante :** [« Connect-MsolService : la levée de l’Exception de type » erreur](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Se connecter au module Azure Active Directory V2 PowerShell
<a name="ConnectV2"> </a>

Pour les procédures nécessitant les nouvelles applets de commande du [module PowerShell de Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), suivez cette procédure pour installer le module et le connecter à votre abonnement à Office 365 :
  
1. Ouvrez une invite de commande Windows PowerShell avec élévation de privilèges (d’exécution Windows PowerShell en tant qu’administrateur).
    
2. Dans la **administrateur : Windows PowerShell** fenêtre de commande, exécutez la commande suivante :
    
  ```
  Install-Module -Name AzureAD 
  ```

Si vous êtes invité à propos de l’installation d’un module à partir d’un référentiel non approuvé, tapez **o** et appuyez sur ENTRÉE.
    
3. Une fois l’installation du nouveau module terminée, utilisez ces commandes pour vous connecter à votre abonnement Office 365 :
    
  -  Avec un *nom de compte et de mot de passe* :
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.
    
  - Avec une *authentification à facteurs multiples (AMF)* :
    
  ```
  Connect-AzureAD
  ```

Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.
    
Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.
    
Une fois connecté, vous pouvez utiliser les nouvelles applets de commande du [module PowerShell de Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>Voir aussi

#### 

[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)
  
[Connexion à tous les services Office 365 à l'aide d'une seule fenêtre Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[MsolService de connexion](https://go.microsoft.com/fwlink/p/?LinkId=532375)

