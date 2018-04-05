---
title: Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="a6109-103">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6109-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="a6109-104">**Résumé :** Au lieu de gérer différents services Office 365 dans des fenêtres de console PowerShell distinctes, vous pouvez vous connecter à tous les services Office 365 et les gérer à partir de la fenêtre de la console seule.</span><span class="sxs-lookup"><span data-stu-id="a6109-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="a6109-p101">Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d’avoir jusqu'à cinq sessions Windows PowerShell différentes en même temps correspondant au centre d’administration Office 365, SharePoint Online, Exchange Online, Skype pour professionnels en ligne et la sécurité &amp;Centre de conformité. Avec cinq méthodes de connexion différentes dans les sessions Windows PowerShell séparées, votre bureau se présenterait comme suit :</span><span class="sxs-lookup"><span data-stu-id="a6109-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="a6109-p102">Ce n’est pas optimal pour la gestion d’Office 365, car vous ne pouvez pas échanger des données entre ces cinq fenêtres Gestion des services-entre. Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer la sécurité, Skype pour Business Online, Exchange Online, SharePoint Online et Office 365 &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="a6109-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="a6109-110">Cet article est en cours de mise à jour pour utiliser le module PowerShell de Azure Active Directory V2 et pour l’authentification multifactorielle (AMF).</span><span class="sxs-lookup"><span data-stu-id="a6109-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="a6109-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="a6109-111">Before you begin</span></span>
<span data-ttu-id="a6109-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="a6109-112"></span></span>

<span data-ttu-id="a6109-113">Avant de pouvoir gérer tous d’Office 365 à partir d’une seule instance de Windows PowerShell, prenez en compte les conditions préalables suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6109-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="a6109-p103">L’Office 365 fonctionne ou l’école de compte que vous l’utilisation de ces procédures doit pour être membre d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Présente une condition requise pour Office 365 PowerShell, et pas nécessairement pour tous les autres services Office 365.</span><span class="sxs-lookup"><span data-stu-id="a6109-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="a6109-117">Vous pouvez utiliser les versions 64 bits de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6109-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="a6109-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a6109-118">Windows 10</span></span>
    
  - <span data-ttu-id="a6109-119">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="a6109-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="a6109-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a6109-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="a6109-121">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a6109-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="a6109-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="a6109-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="a6109-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="a6109-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="a6109-p104">Vous devez installer le Microsoft.NET Framework 4.5. *x* et ensuite soit le Windows Management Framework 3.0 ou le de Windows Management Framework 4.0. Pour plus d’informations, consultez [installation du.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) et de [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="a6109-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="a6109-126">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le Skype pour module Business Online et d’un des modules Office 365.</span><span class="sxs-lookup"><span data-stu-id="a6109-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="a6109-127">Vous devez installer les modules requis pour Office 365, SharePoint Online et Skype pour entreprise en ligne :</span><span class="sxs-lookup"><span data-stu-id="a6109-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="a6109-128">Microsoft Online Service Assistant de connexion pour les professionnels de l’informatique RTW</span><span class="sxs-lookup"><span data-stu-id="a6109-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="a6109-129">Windows Azure Active Directory Module pour Windows PowerShell (version 64 bits) avec la commande **MSOnline du Module d’installation** à une invite de commandes avec élévation de privilèges PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6109-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="a6109-130">Shell de gestion en ligne de SharePoint</span><span class="sxs-lookup"><span data-stu-id="a6109-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="a6109-131">Skype pour les entreprises en ligne, Module de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6109-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="a6109-p105">Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype pour Business Online, Exchange Online et de la sécurité &amp; centre de conformité. Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="a6109-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="a6109-134">Étapes de connexion</span><span class="sxs-lookup"><span data-stu-id="a6109-134">Connection steps</span></span>
<span data-ttu-id="a6109-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="a6109-135"></span></span>

<span data-ttu-id="a6109-136">Voici la procédure pour se connecter à tous les services dans une seule fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6109-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="a6109-137">Ouvrez Windows PowerShell en tant qu’administrateur (utilisez **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="a6109-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="a6109-138">Exécutez cette commande et entrez votre travail d’Office 365 ou école d’informations d’identification du compte.</span><span class="sxs-lookup"><span data-stu-id="a6109-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="a6109-139">Exécutez ces commandes pour vous connecter à Office 365.</span><span class="sxs-lookup"><span data-stu-id="a6109-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="a6109-p106">Exécutez ces commandes pour se connecter à SharePoint Online. Remplacer _ \<domainhost >_ avec la valeur réelle de votre domaine. Par exemple, pour `litwareinc.onmicrosoft.com`, la _ \<domainhost >_ valeur est `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="a6109-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="a6109-p107">Exécutez ces commandes pour se connecter sur Skype pour Business Online. Un avertissement sur l’augmentation de la `WSMan NetworkDelayms` valeur est attendue de la première fois que vous vous connectez et qui doit être ignoré.</span><span class="sxs-lookup"><span data-stu-id="a6109-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="a6109-145">Exécutez ces commandes pour se connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="a6109-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="a6109-146">Exécutez ces commandes pour vous connecter à la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="a6109-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="a6109-p108">Le préfixe de texte « cc » est ajouté à *tous les* sécurité &amp; noms d’applet de commande de centre de conformité afin de pouvoir exécuter applets de commande qui existent dans Exchange Online et de la sécurité &amp; centre de conformité dans la même session Windows PowerShell. Par exemple, **Get-RoleGroup** devient **Get-ccRoleGroup** dans la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="a6109-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="a6109-p109">Voici toutes les commandes dans un seul bloc. Spécifiez le nom de votre hôte de domaine et tous les exécuter à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="a6109-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```
<span data-ttu-id="a6109-151">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez cette commande pour supprimer les sessions actives à Skype pour Business Online, Exchange Online, SharePoint Online et la sécurité &amp; centre de conformité :</span><span class="sxs-lookup"><span data-stu-id="a6109-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="a6109-152">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="a6109-152">New to Office 365?</span></span>
<span data-ttu-id="a6109-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a6109-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="a6109-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6109-154">See also</span></span>

- [<span data-ttu-id="a6109-155">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6109-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="a6109-156">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="a6109-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="a6109-157">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6109-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="a6109-158">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6109-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a6109-159">Utilisez Windows PowerShell pour créer des rapports dans Office 365</span><span class="sxs-lookup"><span data-stu-id="a6109-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
