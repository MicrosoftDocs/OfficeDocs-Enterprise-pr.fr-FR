---
title: Se connecter à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
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
description: 'Résumé : Connectez Windows PowerShell à tous les services Microsoft 365 dans une fenêtre Windows PowerShell unique.'
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230840"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="3f0cd-103">Se connecter à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-103">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="3f0cd-104">Lorsque vous utilisez PowerShell pour gérer Microsoft 365, il est possible d’avoir jusqu’à cinq sessions Windows PowerShell différentes ouvertes en même temps correspondant au centre d’administration Microsoft 365, SharePoint Online, Exchange Online, Skype entreprise Online, Microsoft teams et le centre de sécurité &amp; conformité.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-104">When you use PowerShell to manage Microsoft 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="3f0cd-105">Avec cinq méthodes de connexion différentes dans des sessions Windows PowerShell distinctes, votre Bureau pourrait ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="3f0cd-107">Cette solution n’est pas optimale pour la gestion de Microsoft 365 car vous ne pouvez pas échanger des données entre ces cinq fenêtres pour la gestion interservice.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-107">This is not optimal for managing Microsoft 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="3f0cd-108">Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer les comptes Microsoft 365, Skype entreprise Online, Exchange Online, SharePoint Online, Microsoft teams et le &amp; Centre de sécurité conformité.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Microsoft 365 accounts, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="3f0cd-109">Cet article ne contient actuellement que les commandes permettant de se connecter au Cloud mondial (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-109">This article currently only contains the commands to connect to the Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="3f0cd-110">Des notes supplémentaires fournissent des liens vers des articles contenant des informations sur la connexion aux autres nuages Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-110">Additional notes provide links to articles with information about connecting to the other Microsoft 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="3f0cd-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3f0cd-111">Before you begin</span></span>

<span data-ttu-id="3f0cd-112">Avant de pouvoir gérer l’ensemble de Microsoft 365 à partir d’une seule instance de Windows PowerShell, tenez compte des conditions préalables suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-112">Before you can manage all of Microsoft 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="3f0cd-113">Le compte professionnel ou scolaire Microsoft 365 que vous utilisez pour ces procédures doit être membre d’un rôle d’administrateur Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-113">The Microsoft 365 work or school account that you use for these procedures needs to be a member of a Microsoft 365 admin role.</span></span> <span data-ttu-id="3f0cd-114">Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-114">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span></span> <span data-ttu-id="3f0cd-115">Ceci est une condition requise pour PowerShell pour Microsoft 365, pas nécessairement pour tous les autres services Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-115">This a requirement for PowerShell for Microsoft 365, not necessarily for all other Microsoft 365 services.</span></span>
    
- <span data-ttu-id="3f0cd-116">Vous pouvez utiliser les versions 64 bits suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="3f0cd-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3f0cd-117">Windows 10</span></span>
    
  - <span data-ttu-id="3f0cd-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="3f0cd-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="3f0cd-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="3f0cd-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="3f0cd-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3f0cd-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="3f0cd-121">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3f0cd-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="3f0cd-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="3f0cd-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="3f0cd-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="3f0cd-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="3f0cd-124">\*Vous devez installer Microsoft .NET Framework 4,5. *x* , puis sur Windows management Framework 3,0 ou Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="3f0cd-125">Pour plus d’informations, voir [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="3f0cd-126">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le module Skype entreprise Online et l’un des modules Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Microsoft 365 modules.</span></span>
    
- <span data-ttu-id="3f0cd-127">Vous devez installer les modules requis pour Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype entreprise Online et teams :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="3f0cd-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="3f0cd-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="3f0cd-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="3f0cd-130">Skype Entreprise Online, module Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="3f0cd-131">Echange en ligne PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="3f0cd-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="3f0cd-132">Vue d’ensemble de PowerShell teams</span><span class="sxs-lookup"><span data-stu-id="3f0cd-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="3f0cd-133">Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype entreprise Online et le centre de sécurité &amp; conformité.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="3f0cd-134">Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a><span data-ttu-id="3f0cd-135">Étapes de connexion lors de l’utilisation d’un mot de passe uniquement</span><span class="sxs-lookup"><span data-stu-id="3f0cd-135">Connection steps when using just a password</span></span>

<span data-ttu-id="3f0cd-136">Voici les étapes à suivre pour vous connecter à tous les services dans une seule fenêtre PowerShell lorsque vous utilisez uniquement un mot de passe pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-136">Here are the steps to connect to all the services in a single PowerShell window when you are using just a password for sign-in.</span></span>
  
1. <span data-ttu-id="3f0cd-137">Ouvrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="3f0cd-138">Exécutez cette commande et entrez vos informations d’identification de compte professionnel ou scolaire Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-138">Run this command and enter your Microsoft 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="3f0cd-139">Exécutez cette commande pour vous connecter à Azure AD à l’aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="3f0cd-140">Si vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell, vous pouvez également exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="3f0cd-141">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="3f0cd-142">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="3f0cd-143">Exécutez les commandes suivantes pour vous connecter à SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="3f0cd-144">Spécifiez le nom de l’Organisation pour votre domaine.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-144">Specify the organization name for your domain.</span></span> <span data-ttu-id="3f0cd-145">Par exemple, pour « litwareinc.onmicrosoft.com », la valeur du nom de l’organisation est « litwareinc ».</span><span class="sxs-lookup"><span data-stu-id="3f0cd-145">For example, for "litwareinc.onmicrosoft.com", the  organization name value is "litwareinc".</span></span>
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. <span data-ttu-id="3f0cd-146">Exécutez les commandes suivantes pour vous connecter à Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="3f0cd-147">Un avertissement indiquant que l’augmentation de la `WSMan NetworkDelayms` valeur est attendu lors de la première connexion et doit être ignoré.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="3f0cd-148">Exécutez cette commande pour vous connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="3f0cd-149">Pour vous connecter à Exchange Online pour les nuages Microsoft 365 autres que dans le monde entier, utilisez le paramètre **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="3f0cd-149">To connect to Exchange Online for Microsoft 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="3f0cd-150">Pour plus d’informations, consultez la rubrique [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="3f0cd-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="3f0cd-151">Exécutez ces commandes pour vous connecter à teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="3f0cd-152">Pour vous connecter à des nuages Microsoft teams autres que le monde entier, consultez la rubrique [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="3f0cd-153">Exécutez ces commandes pour vous connecter au centre de sécurité &amp; conformité.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="3f0cd-154">Pour vous connecter au centre de sécurité &amp; conformité pour les nuages Microsoft 365 autres que dans le monde entier, consultez la rubrique [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="3f0cd-154">To connect to the Security &amp; Compliance Center for Microsoft 365 clouds other than Worldwide, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="3f0cd-155">Voici toutes les commandes dans un seul bloc lors de l’utilisation du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="3f0cd-156">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="3f0cd-157">Par ailleurs, Voici toutes les commandes dans un seul bloc lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="3f0cd-158">Spécifiez le nom de votre hôte de domaine, puis exécutez-le en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="3f0cd-159">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez la commande suivante pour supprimer les sessions actives vers Skype entreprise Online, SharePoint Online, le centre de sécurité &amp; conformité et teams :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="3f0cd-160">Étapes de connexion lors de l’utilisation de l’authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="3f0cd-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="3f0cd-161">Voici toutes les commandes dans un seul bloc pour vous connecter à Azure AD, SharePoint Online, Skype entreprise, Exchange Online et teams à l’aide de l’authentification multifacteur dans une fenêtre unique à l’aide du module Azure Active Directory PowerShell pour Graph.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="3f0cd-162">Spécifiez le nom d’utilisateur principal (UPN) d’un compte d’utilisateur et votre nom d’hôte de domaine, puis exécutez-les tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="3f0cd-163">Vous pouvez également utiliser toutes les commandes lorsque vous utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0cd-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="3f0cd-164">Pour le centre de sécurité &amp; conformité, consultez la rubrique [connexion au centre de sécurité & conformité PowerShell à l’aide de Multi-Factor Authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) pour se connecter à l’aide de l’authentification multifacteur :</span><span class="sxs-lookup"><span data-stu-id="3f0cd-164">For the Security &amp; Compliance Center, see [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="3f0cd-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f0cd-165">See also</span></span>

- [<span data-ttu-id="3f0cd-166">Se connecter à Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-166">Connect to Microsoft 365 with PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="3f0cd-167">Gérer SharePoint Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-167">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="3f0cd-168">Gérer les comptes d’utilisateur, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0cd-168">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="3f0cd-169">Utiliser Windows PowerShell pour créer des rapports dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="3f0cd-169">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
