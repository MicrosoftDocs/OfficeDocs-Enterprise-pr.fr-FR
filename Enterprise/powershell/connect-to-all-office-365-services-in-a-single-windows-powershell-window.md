---
title: Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
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
description: 'Résumé: Connectez Windows PowerShell à tous les services Office 365 dans une seule fenêtre Windows PowerShell.'
ms.openlocfilehash: 38221a2c9b50aaeab217016336cf4d020abd706a
ms.sourcegitcommit: 2e5e2c65a1b785e229f1f7fd5b219f1b3de96f97
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "30339512"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="c4224-103">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4224-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="c4224-104">**Résumé:** Au lieu de gérer les différents services Office 365 dans des fenêtres de console PowerShell distinctes, vous pouvez vous connecter à tous les services Office 365 et les gérer à partir d'une seule fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="c4224-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="c4224-105">Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d'avoir jusqu'à cinq sessions Windows PowerShell différentes ouvertes en même temps correspondant au centre d'administration d'Office 365, à SharePoint Online, à Exchange Online, Skype entreprise Online et à la sécurité &amp;Centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="c4224-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="c4224-106">Avec cinq méthodes de connexion différentes dans des sessions Windows PowerShell distinctes, votre Bureau pourrait ressembler à ceci:</span><span class="sxs-lookup"><span data-stu-id="c4224-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="c4224-108">Cette solution n'est pas optimale pour la gestion d'Office 365 car vous ne pouvez pas échanger des données entre ces cinq fenêtres pour la gestion interservice.</span><span class="sxs-lookup"><span data-stu-id="c4224-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="c4224-109">Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer Office 365, Skype entreprise Online, Exchange Online, SharePoint Online et le centre de &amp; sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="c4224-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="c4224-110">Cet article ne contient actuellement que les commandes permettant de se connecter au Cloud Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="c4224-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="c4224-111">Des notes supplémentaires fournissent des liens vers des articles contenant des informations sur la connexion aux autres nuages Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4224-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="c4224-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="c4224-112">Before you begin</span></span>

<span data-ttu-id="c4224-113">Avant de pouvoir gérer l'ensemble des Office 365 à partir d'une seule instance de Windows PowerShell, tenez compte des conditions préalables suivantes:</span><span class="sxs-lookup"><span data-stu-id="c4224-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="c4224-114">Le compte professionnel ou scolaire Office 365 que vous utilisez pour ces procédures doit être membre d'un rôle d'administrateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4224-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="c4224-115">Pour obtenir plus d’informations, consultez l’article [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="c4224-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="c4224-116">Il s'agit d'une condition requise pour Office 365 PowerShell, pas nécessairement pour tous les autres services Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4224-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="c4224-117">Vous pouvez utiliser les versions 64 bits suivantes de Windows:</span><span class="sxs-lookup"><span data-stu-id="c4224-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="c4224-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c4224-118">Windows 10</span></span>
    
  - <span data-ttu-id="c4224-119">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="c4224-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="c4224-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="c4224-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="c4224-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c4224-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="c4224-122">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c4224-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="c4224-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="c4224-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="c4224-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="c4224-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="c4224-125">\*Vous devez installer Microsoft .NET Framework 4,5. *x* , puis sur Windows management Framework 3,0 ou Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="c4224-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="c4224-126">Pour plus d'informations, voir [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="c4224-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="c4224-127">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le module Skype entreprise Online et l'un des modules Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4224-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="c4224-128">Vous devez installer les modules requis pour Azure AD, SharePoint Online et Skype entreprise Online:</span><span class="sxs-lookup"><span data-stu-id="c4224-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="c4224-129">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="c4224-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="c4224-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="c4224-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="c4224-131">Skype entreprise Online, module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4224-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="c4224-132">Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype entreprise Online, Exchange Online et le centre de &amp; sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="c4224-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="c4224-133">Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **exécuter en tant qu'administrateur**).</span><span class="sxs-lookup"><span data-stu-id="c4224-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="c4224-134">Étapes de connexion lors de l'utilisation d'un mot de passe</span><span class="sxs-lookup"><span data-stu-id="c4224-134">Connection steps when using a password</span></span>

<span data-ttu-id="c4224-135">Voici les étapes à suivre pour vous connecter à tous les services dans une seule fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4224-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="c4224-136">Ouvrez Windows PowerShell en tant qu'administrateur (utilisez **exécuter en tant qu'administrateur**).</span><span class="sxs-lookup"><span data-stu-id="c4224-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="c4224-137">Exécutez cette commande et entrez les informations d'identification de votre compte professionnel ou scolaire Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4224-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="c4224-138">Exécutez cette commande pour vous connecter à Azure Active Directory (AD) à l'aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="c4224-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="c4224-139">Si vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell, vous pouvez également exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="c4224-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="c4224-140">Exécutez les commandes suivantes pour vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c4224-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="c4224-141">Remplacez _ \<domainhost>_ par la valeur réelle de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="c4224-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="c4224-142">par exemple, pour «litwareinc.onmicrosoft.com», la _ \<valeur domainhost>_ est «litwareinc».</span><span class="sxs-lookup"><span data-stu-id="c4224-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="c4224-143">Exécutez les commandes suivantes pour vous connecter à Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="c4224-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="c4224-144">Un avertissement indiquant que l' `WSMan NetworkDelayms` augmentation de la valeur est attendu lors de la première connexion et doit être ignoré.</span><span class="sxs-lookup"><span data-stu-id="c4224-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="c4224-145">Exécutez les commandes suivantes pour vous connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c4224-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="c4224-146">Pour vous connecter à Exchange Online pour Office 365 nuages autres que dans le monde entier, consultez la rubrique [connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="c4224-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="c4224-147">Exécutez ces commandes pour vous connecter au centre &amp; de sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="c4224-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="c4224-148">Pour vous connecter au centre &amp; de sécurité conformité pour Office 365 nuages autres que dans le monde entier, consultez la rubrique [connect to Office 365 Security _AMP_ Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="c4224-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="c4224-149">Voici toutes les commandes dans un seul bloc lors de l'utilisation du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="c4224-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="c4224-150">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="c4224-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="c4224-151">Par ailleurs, Voici toutes les commandes dans un seul bloc lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4224-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="c4224-152">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="c4224-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="c4224-153">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez la commande suivante pour supprimer les sessions actives vers Skype entreprise Online, Exchange Online, SharePoint Online et le centre de sécurité &amp; conformité:</span><span class="sxs-lookup"><span data-stu-id="c4224-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="c4224-154">Étapes de connexion lors de l'utilisation de l'authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c4224-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="c4224-155">Voici toutes les commandes dans un seul bloc pour se connecter à Azure AD, SharePoint Online et Skype pour buiness à l'aide de l'authentification multifacteur dans une seule fenêtre à l'aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="c4224-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="c4224-156">Spécifiez le nom d'utilisateur principal (UPN) d'un compte d'utilisateur et votre nom d'hôte de domaine, puis exécutez-les tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="c4224-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="c4224-157">Vous pouvez également utiliser toutes les commandes lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4224-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="c4224-158">Pour Exchange Online et le centre &amp; de sécurité conformité, consultez les rubriques suivantes pour vous connecter à l'aide de l'authentification multifacteur:</span><span class="sxs-lookup"><span data-stu-id="c4224-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="c4224-159">Connexion à Exchange Online PowerShell avec l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c4224-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="c4224-160">Se connecter au centre de sécurité & de la sécurité d'Office 365 PowerShell à l'aide de l'authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="c4224-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="c4224-161">Notez que dans les deux cas, vous devez vous connecter à l'aide de sessions distinctes du module Exchange Online Remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4224-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="c4224-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4224-162">See also</span></span>

- [<span data-ttu-id="c4224-163">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4224-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="c4224-164">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4224-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="c4224-165">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4224-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="c4224-166">Utilisez Windows PowerShell pour créer des rapports dans Office 365</span><span class="sxs-lookup"><span data-stu-id="c4224-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
