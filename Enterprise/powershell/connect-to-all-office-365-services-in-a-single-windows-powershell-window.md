---
title: Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Résumé : Connexion de Windows PowerShell à tous les services Office 365 dans une seule fenêtre de Windows PowerShell.'
ms.openlocfilehash: 7e3a3ecbb0526c88392848cf39b59b40f1f4c80c
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell

 **Résumé :** Au lieu de gérer différents services Office 365 dans des fenêtres de console PowerShell distinctes, vous pouvez vous connecter à tous les services Office 365 et les gérer à partir de la fenêtre de la console seule.
  
Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d’avoir jusqu'à cinq sessions Windows PowerShell différentes en même temps correspondant au centre d’administration Office 365, SharePoint Online, Exchange Online, Skype pour professionnels en ligne et la sécurité &amp;Centre de conformité. Avec cinq méthodes de connexion différentes dans les sessions Windows PowerShell séparées, votre bureau se présenterait comme suit :
  
![Cinq consoles Windows PowerShell exécutées simultanément](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Ce n’est pas optimal pour la gestion d’Office 365, car vous ne pouvez pas échanger des données entre ces cinq fenêtres Gestion des services-entre. Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer la sécurité, Skype pour Business Online, Exchange Online, SharePoint Online et Office 365 &amp; centre de conformité.

## <a name="before-you-begin"></a>Avant de commencer
<a name="BeforeYouBegin"> </a>

Avant de pouvoir gérer tous d’Office 365 à partir d’une seule instance de Windows PowerShell, prenez en compte les conditions préalables suivantes :
  
- L’Office 365 fonctionne ou l’école de compte que vous l’utilisation de ces procédures doit pour être membre d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Présente une condition requise pour Office 365 PowerShell, et pas nécessairement pour tous les autres services Office 365.
    
- Vous pouvez utiliser les versions 64 bits de Windows suivantes :
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Vous devez installer le Microsoft.NET Framework 4.5. *x* et ensuite soit le Windows Management Framework 3.0 ou le de Windows Management Framework 4.0. Pour plus d’informations, consultez [installation du.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) et de [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le Skype pour module Business Online et d’un des modules Office 365.
    
- Vous devez installer les modules qui sont nécessaires pour qu’une annonce Azure, SharePoint Online et Skype pour entreprise en ligne :
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md#ConnectV2)
   - [Shell de gestion en ligne de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype pour les entreprises en ligne, Module de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype pour Business Online, Exchange Online et de la sécurité &amp; centre de conformité. Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **Exécuter en tant qu’administrateur**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Étapes de connexion lors de l’utilisation d’un mot de passe
<a name="ConnStepsPassword"> </a>

Voici la procédure pour se connecter à tous les services dans une seule fenêtre PowerShell.
  
1. Ouvrez Windows PowerShell en tant qu’administrateur (utilisez **Exécuter en tant qu’administrateur**).
    
2. Exécutez cette commande et entrez votre travail d’Office 365 ou école d’informations d’identification du compte.
    
  ```
  $credential = Get-Credential
  ```

3. Exécutez cette commande pour vous connecter à Azure Active Directory (AD).
    
  ```
   Connect-AzureAD -Credential $credential
  ```

4. Exécutez ces commandes pour se connecter à SharePoint Online. Remplacer _ \<domainhost >_ avec la valeur réelle de votre domaine. Par exemple, pour `litwareinc.onmicrosoft.com`, la _ \<domainhost >_ valeur est `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Exécutez ces commandes pour se connecter sur Skype pour Business Online. Un avertissement sur l’augmentation de la `WSMan NetworkDelayms` valeur est attendue de la première fois que vous vous connectez et qui doit être ignoré.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Exécutez ces commandes pour se connecter à Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. Exécutez ces commandes pour vous connecter à la sécurité &amp; centre de conformité.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

Voici toutes les commandes dans un seul bloc. Spécifiez le nom de votre hôte de domaine et tous les exécuter à un moment donné.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```
Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez cette commande pour supprimer les sessions actives à Skype pour Business Online, Exchange Online, SharePoint Online et la sécurité &amp; centre de conformité :
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Étapes de connexion lorsque vous utilisez une authentification multifactorielle
<a name="ConnStepsMFA"> </a>

Voici toutes les commandes dans un seul bloc pour se connecter à AD Azure, SharePoint Online et Skype pour la gestion à l’aide de l’authentification à facteurs multiples dans une seule fenêtre. Spécifiez le nom d’utilisateur principaux (UPN) d’un compte d’administrateur global et de votre nom d’hôte de domaine et tous les exécuter à un moment donné.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Pour Exchange Online et de la sécurité &amp; centre de conformité, consultez les rubriques suivantes pour vous connecter à l’aide de l’authentification selon plusieurs facteur :

- [Se connecter à Exchange Online PowerShell à l’aide de l’authentification multicritères](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Se connecter à Office 365 sécurité & PowerShell de centre de conformité à l’aide de l’authentification multicritères](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Notez que, dans les deux cas, vous devez vous connecter à l’aide de sessions séparées du PowerShell de Module Exchange en ligne distant.


## <a name="new-to-office-365"></a>Vous débutez avec Office 365 ?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Voir aussi

- [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md)
- [Gestion de SharePoint Online avec Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Utilisez Windows PowerShell pour créer des rapports dans Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
