---
title: Connexion à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Résumé : Connectez Windows PowerShell à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell.'
ms.openlocfilehash: 222355bb3c8c9d8123fd2738c80a7225da15ca46
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502679"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>Connexion à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell

Lorsque vous utilisez PowerShell pour gérer Microsoft 365, vous pouvez avoir jusqu’à cinq sessions Windows PowerShell différentes ouvertes en même temps correspondant au centre d’administration Microsoft 365, SharePoint Online, Exchange Online, Skype Entreprise Online, Microsoft teams et le centre de sécurité &amp; conformité. Avec cinq méthodes de connexion différentes dans les sessions Windows PowerShell distinctes, votre ordinateur de bureau pourrait ressembler à ceci :
  
![Cinq consoles Windows PowerShell exécutées simultanément](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Cet affichage n’est pas optimal pour gérer Microsoft 365, car vous ne pouvez pas échanger de données entre ces cinq fenêtres pour effectuer une gestion croisée des services. Cette rubrique explique comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer les comptes Microsoft 365, Skype Entreprise Online, Exchange Online, SharePoint Online, Microsoft teams et le centre de sécurité &amp; conformité.

>[!Note]
>Cet article contient actuellement uniquement les commandes permettant de se connecter au Cloud (+ GCC) dans le monde entier. Des notes supplémentaires fournissent des liens vers des articles contenant des informations sur la connexion aux autres nuages Microsoft 365.
>

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir gérer l’ensemble de Microsoft 365 à partir d’une seule instance de Windows PowerShell, tenez compte des conditions préalables suivantes :
  
- Le compte professionnel ou scolaire Microsoft 365 que vous utilisez pour ces procédures doit être membre du rôle d’administrateur Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide). Il s’agit d’une condition requise pour PowerShell pour Microsoft 365, pas nécessairement pour tous les autres services Microsoft 365.
    
- Vous pouvez utiliser les versions 64 bits de Windows suivantes :
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \* Vous devez installer Microsoft .NET Framework 4.5.*x* puis Windows Management Framework 3.0 ou Windows Management Framework 4.0. Pour plus d’informations, voir [l’installation du .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) et [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le module Skype Entreprise Online et un des modules Microsoft 365.
    
- Vous devez installer les modules requis pour Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype Entreprise Online et les équipes :
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype Entreprise Online, module Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Echange en ligne PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Aperçu de Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype Entreprise Online et le centre de sécurité &amp; conformité. Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (fenêtre Windows PowerShell que vous ouvrez en sélectionnant **Exécuter en tant qu’administrateur**).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Étapes de connexion lors de l’utilisation d’un mot de passe

Voici les étapes à suivre pour vous connecter à tous les services dans une seule fenêtre PowerShell lorsque vous utilisez uniquement un mot de passe pour la connexion.
  
1. Ouvrez Windows PowerShell.
    
2. Exécutez la commande suivante et entrez les informations d’identification de votre compte professionnel ou scolaire Microsoft 365.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Exécutez cette commande pour vous connecter à Azure AD à l’aide du module PowerShell Azure Active Directory pour Graph.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Si vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell, vous pouvez également exécuter la commande suivante.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.

4. Exécutez ces commandes pour vous connecter à SharePoint Online. Spécifiez le nom de l’organisation de votre domaine. Par exemple, pour « litwareinc.onmicrosoft.com », la valeur nom de l’organisation est « litwareinc ».
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
   ```

5. Exécutez ces commandes pour vous connecter à Skype Entreprise online. Vous devez normalement voir apparaître un avertissement sur l’augmentation de la valeur `WSMan NetworkDelayms` la première fois que vous connectez. Ignorez-le.
     
   ```powershell
   Import-Module SkypeOnlineConnector
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. Exécutez cette commande pour vous connecter à Exchange Online.
    
   ```powershell
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > Pour vous connecter à Exchange Online pour les nuages Microsoft 365 autres que le monde, utilisez le paramètre de **-ExchangeEnvironmentName**. Pour plus d’informations, voir [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps).

7. Exécutez ces commandes pour vous connecter au PowerShell Teams.
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Pour vous connecter aux clouds Microsoft teams autres que le monde, voir [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).

8. Exécutez ces commandes pour vous connecter au centre de conformité &amp; sécurité.
    
   ```powershell
   $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $SccSession -Prefix cc
   ```

   > [!Note]
   > Pour vous connecter au centre de conformité &amp; de sécurité pour les nuages Microsoft 365 autres que le monde, voir [Se connecter à la sécurité &](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)PowerShell du centre de conformité.

Voici toutes les commandes d’un seul bloc lors de l’utilisation d’Azure Active Directory PowerShell for Graph module. Spécifiez le nom de votre hôte de domaine, puis exécutez-les tous en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Vous pouvez également utiliser les commandes suivantes dans un seul bloc lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell. Spécifiez le nom de votre hôte de domaine, puis exécutez-les tous en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez cette commande pour supprimer les sessions actives pour Skype Entreprise Online, SharePoint Online, le centre de sécurité &amp; conformité et les équipes :
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Étapes de connexion lors de l’utilisation de l’authentification multifacteur

Voici toutes les commandes d’un seul bloc pour vous connecter à Azure AD, SharePoint Online, Skype Entreprise, Exchange Online et teams à l’aide de l’authentification multifacteur dans une seule fenêtre à l’aide d’Azure Active Directory PowerShell for Graph module. Spécifiez le nom d’utilisateur principal (UPN) d’un compte d’utilisateur et le nom d’hôte de votre domaine, puis exécutez-les tous en même temps.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Vous pouvez également utiliser les commandes suivantes lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Pour le centre de sécurité &amp; conformité, voir [se connecter à la sécurité & centre de conformité PowerShell à l’aide de l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) pour vous connecter à l’aide de l’authentification multifacteur :

## <a name="see-also"></a>Voir aussi

- [Connexion à Microsoft 365 à l’aide de PowerShell](connect-to-office-365-powershell.md)
- [Gérer SharePoint Online avec PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Utilisez Windows PowerShell pour créer des rapports dans Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)
