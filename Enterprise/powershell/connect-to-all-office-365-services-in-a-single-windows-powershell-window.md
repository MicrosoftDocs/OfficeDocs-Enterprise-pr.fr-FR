---
title: Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Résumé : Connectez Windows PowerShell à tous les services Office 365 dans une seule fenêtre Windows PowerShell.'
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547752"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="99d15-103">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d15-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="99d15-104">Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d’avoir jusqu’à cinq sessions Windows PowerShell différentes ouvertes en même temps correspondant au centre d’administration Microsoft 365, SharePoint Online, Exchange Online, Skype entreprise Online, Microsoft teams et le centre de &amp; sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="99d15-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="99d15-105">Avec cinq méthodes de connexion différentes dans des sessions Windows PowerShell distinctes, votre Bureau pourrait ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="99d15-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="99d15-107">Cette solution n’est pas optimale pour la gestion d’Office 365 car vous ne pouvez pas échanger des données entre ces cinq fenêtres pour la gestion interservice.</span><span class="sxs-lookup"><span data-stu-id="99d15-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="99d15-108">Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer Office 365, Skype entreprise Online, Exchange Online, SharePoint Online, Microsoft teams et le centre &amp; de sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="99d15-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="99d15-109">Cet article ne contient actuellement que les commandes permettant de se connecter au Cloud Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="99d15-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="99d15-110">Des notes supplémentaires fournissent des liens vers des articles contenant des informations sur la connexion aux autres nuages Office 365.</span><span class="sxs-lookup"><span data-stu-id="99d15-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="99d15-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="99d15-111">Before you begin</span></span>

<span data-ttu-id="99d15-112">Avant de pouvoir gérer l’ensemble des Office 365 à partir d’une seule instance de Windows PowerShell, tenez compte des conditions préalables suivantes :</span><span class="sxs-lookup"><span data-stu-id="99d15-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="99d15-113">Le compte professionnel ou scolaire Office 365 que vous utilisez pour ces procédures doit être membre d’un rôle d’administrateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="99d15-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="99d15-114">Pour plus d’informations, voir [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="99d15-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="99d15-115">Il s’agit d’une condition requise pour Office 365 PowerShell, pas nécessairement pour tous les autres services Office 365.</span><span class="sxs-lookup"><span data-stu-id="99d15-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="99d15-116">Vous pouvez utiliser les versions 64 bits suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="99d15-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="99d15-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="99d15-117">Windows 10</span></span>
    
  - <span data-ttu-id="99d15-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="99d15-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="99d15-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="99d15-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="99d15-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="99d15-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="99d15-121">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="99d15-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="99d15-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="99d15-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="99d15-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="99d15-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="99d15-124">\*Vous devez installer Microsoft .NET Framework 4,5. *x* , puis sur Windows management Framework 3,0 ou Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="99d15-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="99d15-125">Pour plus d’informations, voir [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="99d15-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="99d15-126">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le module Skype entreprise Online et l’un des modules Office 365.</span><span class="sxs-lookup"><span data-stu-id="99d15-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="99d15-127">Vous devez installer les modules requis pour Azure AD, Exchange Online, SharePoint Online, Skype entreprise Online et teams :</span><span class="sxs-lookup"><span data-stu-id="99d15-127">You need to install the modules that are required for Azure AD, Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="99d15-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="99d15-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="99d15-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="99d15-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="99d15-130">Skype entreprise Online, module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d15-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="99d15-131">Exchange Online PowerShell v2</span><span class="sxs-lookup"><span data-stu-id="99d15-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="99d15-132">Vue d’ensemble de PowerShell teams</span><span class="sxs-lookup"><span data-stu-id="99d15-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="99d15-133">Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype entreprise Online et le centre &amp; de sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="99d15-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="99d15-134">Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="99d15-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="99d15-135">Étapes de connexion lors de l’utilisation d’un mot de passe</span><span class="sxs-lookup"><span data-stu-id="99d15-135">Connection steps when using a password</span></span>

<span data-ttu-id="99d15-136">Voici les étapes à suivre pour vous connecter à tous les services dans une seule fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="99d15-137">Ouvrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="99d15-138">Exécutez cette commande et entrez les informations d’identification de votre compte professionnel ou scolaire Office 365.</span><span class="sxs-lookup"><span data-stu-id="99d15-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="99d15-139">Exécutez cette commande pour vous connecter à Azure Active Directory (AD) à l’aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="99d15-139">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="99d15-140">Si vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell, vous pouvez également exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="99d15-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="99d15-141">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="99d15-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="99d15-142">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="99d15-143">Exécutez les commandes suivantes pour vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="99d15-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="99d15-144">Remplacez _ \<domainhost>_ par la valeur réelle de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="99d15-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="99d15-145">Par exemple, pour « litwareinc.onmicrosoft.com », la _ \<valeur domainhost>_ est « litwareinc ».</span><span class="sxs-lookup"><span data-stu-id="99d15-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="99d15-146">Exécutez les commandes suivantes pour vous connecter à Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="99d15-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="99d15-147">Un avertissement indiquant que l' `WSMan NetworkDelayms` augmentation de la valeur est attendu lors de la première connexion et doit être ignoré.</span><span class="sxs-lookup"><span data-stu-id="99d15-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="99d15-148">Exécutez cette commande pour vous connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="99d15-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="99d15-149">Pour vous connecter à Exchange Online pour Office 365 nuages autres que dans le monde entier, utilisez le paramètre **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="99d15-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="99d15-150">Pour plus d’informations, consultez la rubrique [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="99d15-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="99d15-151">Exécutez ces commandes pour vous connecter à teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="99d15-152">Pour vous connecter à des nuages Microsoft teams autres que le monde entier, consultez la rubrique [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="99d15-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="99d15-153">Exécutez ces commandes pour vous connecter au centre &amp; de sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="99d15-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="99d15-154">Pour vous connecter au centre &amp; de sécurité conformité pour Office 365 nuages autres que dans le monde entier, consultez la rubrique [connect to office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="99d15-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="99d15-155">Voici toutes les commandes dans un seul bloc lors de l’utilisation du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="99d15-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="99d15-156">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="99d15-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="99d15-157">Par ailleurs, Voici toutes les commandes dans un seul bloc lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="99d15-158">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="99d15-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="99d15-159">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez la commande suivante pour supprimer les sessions actives vers Skype entreprise Online, SharePoint Online, le centre de &amp; sécurité conformité et teams :</span><span class="sxs-lookup"><span data-stu-id="99d15-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="99d15-160">Étapes de connexion lors de l’utilisation de l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="99d15-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="99d15-161">Voici toutes les commandes dans un seul bloc pour vous connecter à Azure AD, SharePoint Online, Skype entreprise, Exchange Online et teams à l’aide de l’authentification multifacteur dans une fenêtre unique à l’aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="99d15-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="99d15-162">Spécifiez le nom d’utilisateur principal (UPN) d’un compte d’utilisateur et votre nom d’hôte de domaine, puis exécutez-les tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="99d15-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="99d15-163">Vous pouvez également utiliser toutes les commandes lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99d15-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="99d15-164">Pour le centre &amp; de sécurité conformité, consultez la rubrique [connect to Office 365 Security & Compliance Center PowerShell using Multi-Factor Authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to Connect using Multi-Factor Authentication :</span><span class="sxs-lookup"><span data-stu-id="99d15-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="99d15-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99d15-165">See also</span></span>

- [<span data-ttu-id="99d15-166">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d15-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="99d15-167">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d15-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="99d15-168">Gérer les comptes d’utilisateur, les licences et les groupes avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d15-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="99d15-169">Utilisez Windows PowerShell pour créer des rapports dans Office 365</span><span class="sxs-lookup"><span data-stu-id="99d15-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
