---
title: Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/27/2018
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
description: 'Résumé : Se connecter à Windows PowerShell à tous les services Office 365 dans une seule fenêtre Windows PowerShell.'
ms.openlocfilehash: 5635cf8b03490c2b2f811f22c231c271d5204552
ms.sourcegitcommit: 65de707bd1c389eea48767a68c31032dd5198359
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "26706688"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="c9573-103">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9573-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="c9573-104">**Résumé :** Au lieu de la gestion des différents services Office 365 dans les fenêtres de la console PowerShell distinctes, vous pouvez vous connecter à tous les services Office 365 et les gérer à partir de la même fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="c9573-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="c9573-p101">Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d’ouvrir en même temps correspondant au centre d’administration Office 365, SharePoint Online, Exchange Online, Skype pour Business Online et la sécurité &amp;Centre de conformité. Avec les méthodes de connexion différentes cinq sessions de Windows PowerShell distinct, votre bureau pourrait ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="c9573-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="c9573-p102">Cela n’est pas optimale pour la gestion d’Office 365, car vous ne pouvez pas échanger des données entre ces cinq windows pour la gestion de cross-service. Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer la sécurité, Skype pour Business Online, Exchange Online, SharePoint Online et Office 365 &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="c9573-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="c9573-p103">Actuellement, cet article contient uniquement les commandes pour se connecter à Office 365 dans le monde (+ GCC) nuage. Remarques supplémentaires fournissent des liens vers des articles, des informations sur la connexion à d’autres nuages Office 365.</span><span class="sxs-lookup"><span data-stu-id="c9573-p103">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud. Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="c9573-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="c9573-112">Before you begin</span></span>

<span data-ttu-id="c9573-113">Avant de pouvoir gérer ensemble d’Office 365 à partir d’une seule instance de Windows PowerShell, prenez en compte les conditions préalables suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9573-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="c9573-p104">Office 365 fonctionne ou école compte que vous utilisez pour ces procédures besoins pour être un membre d’un rôle d’administration d’Office 365. Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Présente une condition requise pour Office 365 PowerShell, et pas nécessairement pour tous les autres services Office 365.</span><span class="sxs-lookup"><span data-stu-id="c9573-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="c9573-117">Vous pouvez utiliser les versions 64 bits de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9573-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="c9573-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c9573-118">Windows 10</span></span>
    
  - <span data-ttu-id="c9573-119">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="c9573-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="c9573-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="c9573-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="c9573-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c9573-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="c9573-122">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c9573-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="c9573-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="c9573-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="c9573-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="c9573-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="c9573-p105">\*Vous devez installer Microsoft .NET Framework 4.5. *x* et puis soit Windows Management Framework 3.0 ou Windows Management Framework 4.0. Pour plus d’informations, consultez [installation du .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) et [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="c9573-p105">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="c9573-127">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le Skype pour le module Business Online et l’un des modules d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="c9573-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="c9573-128">Vous devez installer les modules qui sont requis pour Azure AD, SharePoint Online et Skype pour Business Online :</span><span class="sxs-lookup"><span data-stu-id="c9573-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="c9573-129">V2 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c9573-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="c9573-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="c9573-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="c9573-131">Skype pour les entreprises en ligne, le Module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9573-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="c9573-p106">Windows PowerShell doit être configuré afin d’exécuter des scripts signés pour Skype pour Business Online, Exchange Online et la sécurité &amp; centre de conformité. Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="c9573-p106">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="c9573-134">Étapes de connexion lors de l’utilisation d’un mot de passe</span><span class="sxs-lookup"><span data-stu-id="c9573-134">Connection steps when using a password</span></span>

<span data-ttu-id="c9573-135">Voici les étapes à suivre pour se connecter à tous les services dans une seule fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9573-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="c9573-136">Ouvrez Windows PowerShell en tant qu’administrateur (utilisez **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="c9573-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="c9573-137">Exécutez cette commande et entrez votre bureau Office 365 ou établissement des informations d’identification du compte.</span><span class="sxs-lookup"><span data-stu-id="c9573-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="c9573-138">Exécutez cette commande pour se connecter à Azure Active Directory (AD) à l’aide d’Azure Active Directory PowerShell pour le module de graphique.</span><span class="sxs-lookup"><span data-stu-id="c9573-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="c9573-139">Sinon, si vous utilisez le module Microsoft Azure Active Directory Module pour Windows PowerShell, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="c9573-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="c9573-p107">Exécutez ces commandes pour se connecter à SharePoint Online. Remplacez _ \<domainhost >_ avec la valeur réelle pour votre domaine. Par exemple, pour « litwareinc.onmicrosoft.com », la _ \<domainhost >_ valeur est « litwareinc ».</span><span class="sxs-lookup"><span data-stu-id="c9573-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="c9573-p108">Exécutez ces commandes pour se connecter à Skype pour Business Online. Un avertissement sur l’augmentation de la `WSMan NetworkDelayms` valeur est attendue de la première fois que vous vous connectez et doit être ignorée.</span><span class="sxs-lookup"><span data-stu-id="c9573-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="c9573-145">Exécutez ces commandes pour se connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c9573-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

>[!Note]
><span data-ttu-id="c9573-146">Pour vous connecter à Exchange Online pour Office 365 nuages autre que dans le monde entier, voir [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9573-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="c9573-147">Exécutez ces commandes pour se connecter à la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="c9573-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="c9573-148">Pour se connecter à la sécurité &amp; centre de conformité pour Office 365 nuages autre que dans le monde entier, voir [se connecter à Office 365 sécurité & PowerShell du centre de conformité](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9573-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="c9573-p109">Voici toutes les commandes dans un bloc unique lors de l’utilisation d’Azure Active Directory PowerShell pour le module de graphique. Spécifier le nom d’hôte de votre domaine, puis les exécuter tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="c9573-p109">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
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

<span data-ttu-id="c9573-p110">Alternativement, voici toutes les commandes dans un bloc unique lors de l’utilisation du module Microsoft Azure Active Directory Module pour Windows PowerShell. Spécifier le nom d’hôte de votre domaine, puis les exécuter tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="c9573-p110">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
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

<span data-ttu-id="c9573-153">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez cette commande pour supprimer les sessions actives Skype pour Business Online, Exchange Online, SharePoint Online et la sécurité &amp; centre de conformité :</span><span class="sxs-lookup"><span data-stu-id="c9573-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="c9573-154">Étapes de connexion lors de l’utilisation de l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c9573-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="c9573-p111">Voici toutes les commandes dans un bloc unique pour se connecter à AD Azure, SharePoint Online et Skype pour professionnelle à l’aide de l’authentification multifacteur dans une fenêtre unique. Spécifiez le nom d’utilisateur principal (UPN) de nom d’un compte d’administrateur global et votre nom d’hôte de domaine, puis les exécuter tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="c9573-p111">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="c9573-157">Alternativement, voici toutes les commandes lors de l’utilisation du module Microsoft Azure Active Directory Module pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9573-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="c9573-158">Pour Exchange Online et de la sécurité &amp; centre de conformité, consultez les rubriques suivantes pour vous connecter à l’aide de l’authentification multifacteur :</span><span class="sxs-lookup"><span data-stu-id="c9573-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="c9573-159">Connexion à Exchange Online PowerShell avec l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c9573-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="c9573-160">Se connecter à Office 365 sécurité & PowerShell de centre de conformité à l’aide de l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c9573-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="c9573-161">Notez que dans les deux cas, vous devez vous connecter à l’aide de sessions distinctes du PowerShell Module Exchange Online à distance.</span><span class="sxs-lookup"><span data-stu-id="c9573-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="c9573-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9573-162">See also</span></span>

- [<span data-ttu-id="c9573-163">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9573-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="c9573-164">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9573-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="c9573-165">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9573-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="c9573-166">Utilisez Windows PowerShell pour créer des rapports dans Office 365</span><span class="sxs-lookup"><span data-stu-id="c9573-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
