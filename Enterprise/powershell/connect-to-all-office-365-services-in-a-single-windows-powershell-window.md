---
title: "Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell"
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
- Ent_Office_Other
- O365ITProTrain
- DecEntMigration
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Résumé : Connexion de Windows PowerShell à tous les services Office 365 dans une seule fenêtre de Windows PowerShell."
ms.openlocfilehash: 28016342fff77e33bd18369ae08b773ecea32644
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="aad23-103">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad23-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="aad23-104">**Résumé :** Au lieu de gérer différents services Office 365 dans des fenêtres de console PowerShell distinctes, vous pouvez vous connecter à tous les services Office 365 et les gérer à partir de la fenêtre de la console seule.</span><span class="sxs-lookup"><span data-stu-id="aad23-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="aad23-p101">Lorsque vous utilisez PowerShell pour gérer Office 365, il est possible d’avoir jusqu'à cinq sessions Windows PowerShell différentes en même temps correspondant au centre d’administration Office 365, SharePoint Online, Exchange Online, Skype pour professionnels en ligne et la sécurité &amp;Centre de conformité. Avec cinq méthodes de connexion différentes dans les sessions Windows PowerShell séparées, votre bureau se présenterait comme suit :</span><span class="sxs-lookup"><span data-stu-id="aad23-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinq consoles Windows PowerShell exécutées simultanément](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="aad23-p102">Ce n’est pas optimal pour la gestion d’Office 365, car vous ne pouvez pas échanger des données entre ces cinq fenêtres Gestion des services-entre. Cette rubrique décrit comment utiliser une seule instance de Windows PowerShell à partir de laquelle vous pouvez gérer la sécurité, Skype pour Business Online, Exchange Online, SharePoint Online et Office 365 &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="aad23-110">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="aad23-110">Before you begin</span></span>
<span data-ttu-id="aad23-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-111"></span></span>

<span data-ttu-id="aad23-112">Avant de pouvoir gérer tous d’Office 365 à partir d’une seule instance de Windows PowerShell, prenez en compte les conditions préalables suivantes :</span><span class="sxs-lookup"><span data-stu-id="aad23-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="aad23-p103">L’Office 365 fonctionne ou l’école de compte que vous l’utilisation de ces procédures doit pour être membre d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Présente une condition requise pour Office 365 PowerShell, et pas nécessairement pour tous les autres services Office 365.</span><span class="sxs-lookup"><span data-stu-id="aad23-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="aad23-116">Vous pouvez utiliser les versions 64 bits de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="aad23-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="aad23-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="aad23-117">Windows 10</span></span>
    
  - <span data-ttu-id="aad23-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="aad23-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="aad23-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="aad23-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="aad23-120">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="aad23-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="aad23-121">Windows 7 Service Pack 1 (SP1)*</span><span class="sxs-lookup"><span data-stu-id="aad23-121">Windows 7 Service Pack 1 (SP1)*</span></span>
    
  - <span data-ttu-id="aad23-122">Windows Server 2008 R2 SP1*</span><span class="sxs-lookup"><span data-stu-id="aad23-122">Windows Server 2008 R2 SP1*</span></span>
    
    * <span data-ttu-id="aad23-p104">Vous devez installer le Microsoft.NET Framework 4.5. _x_ et ensuite soit le Windows Management Framework 3.0 ou le de Windows Management Framework 4.0. Pour plus d’informations, consultez [installation du.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) et de [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="aad23-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="aad23-126">Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le Skype pour module Business Online et d’un des modules Office 365.</span><span class="sxs-lookup"><span data-stu-id="aad23-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="aad23-127">Vous devez installer les modules requis pour Office 365, SharePoint Online et Skype pour entreprise en ligne :</span><span class="sxs-lookup"><span data-stu-id="aad23-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="aad23-128">Microsoft Online Service Assistant de connexion pour les professionnels de l’informatique RTW</span><span class="sxs-lookup"><span data-stu-id="aad23-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="aad23-129">Windows Azure Active Directory Module pour Windows PowerShell (version 64 bits)</span><span class="sxs-lookup"><span data-stu-id="aad23-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="aad23-130">Shell de gestion en ligne de SharePoint</span><span class="sxs-lookup"><span data-stu-id="aad23-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="aad23-131">Skype pour les entreprises en ligne, Module de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad23-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="aad23-p105">Windows PowerShell doit être configuré pour exécuter des scripts signés pour Skype pour Business Online, Exchange Online et de la sécurité &amp; centre de conformité. Pour ce faire, exécutez la commande suivante dans une session Windows PowerShell avec élévation de privilèges (une fenêtre Windows PowerShell que vous ouvrez en sélectionnant **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="aad23-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="aad23-134">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="aad23-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="aad23-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-135"></span></span>

<span data-ttu-id="aad23-p106">Cette section présente les étapes de connexion sans explications détaillées. Si vous avez des questions ou que vous souhaitez plus d’informations, vous pouvez lire le reste de la rubrique. Les numéros d’étape utilisés ici sont les mêmes que ceux des sections consacrées à chaque étape dans le reste de la rubrique :</span><span class="sxs-lookup"><span data-stu-id="aad23-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="aad23-139">Ouvrez Windows PowerShell en tant qu’administrateur (utilisez **Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="aad23-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="aad23-140">Exécutez cette commande et entrez votre travail d’Office 365 ou école d’informations d’identification du compte.</span><span class="sxs-lookup"><span data-stu-id="aad23-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="aad23-141">Exécutez ces commandes pour vous connecter à Office 365.</span><span class="sxs-lookup"><span data-stu-id="aad23-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="aad23-p107">Exécutez ces commandes pour se connecter à SharePoint Online. Remplacer _ \<domainhost >_ avec la valeur réelle de votre domaine. Par exemple, pour `litwareinc.onmicrosoft.com`, la _ \<domainhost >_ valeur est `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="aad23-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="aad23-p108">Exécutez ces commandes pour se connecter sur Skype pour Business Online. Un avertissement sur l’augmentation de la `WSMan NetworkDelayms` valeur est attendue de la première fois que vous vous connectez et qui doit être ignoré.</span><span class="sxs-lookup"><span data-stu-id="aad23-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="aad23-147">Exécutez ces commandes pour se connecter à Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="aad23-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="aad23-148">Exécutez ces commandes pour vous connecter à la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="aad23-p109">Le préfixe de texte « cc » est ajouté à *tous les* sécurité &amp; noms d’applet de commande de centre de conformité afin de pouvoir exécuter applets de commande qui existent dans Exchange Online et de la sécurité &amp; centre de conformité dans la même session Windows PowerShell. Par exemple, **Get-RoleGroup** devient **Get-ccRoleGroup** dans la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="aad23-p110">Voici toutes les commandes dans un seul bloc. Spécifiez le nom de votre hôte de domaine et tous les exécuter à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="aad23-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="aad23-153">Lorsque vous êtes prêt à fermer la fenêtre Windows PowerShell, exécutez cette commande pour supprimer les sessions actives à Skype pour Business Online, Exchange Online, SharePoint Online et la sécurité &amp; centre de conformité :</span><span class="sxs-lookup"><span data-stu-id="aad23-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="aad23-154">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="aad23-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="aad23-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="aad23-156">Étapes 1 : ouvrez Windows PowerShell en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="aad23-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="aad23-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-157"></span></span>

<span data-ttu-id="aad23-158">Si vous exécutez Windows 10, Windows 8, Windows 8.1, 2016 de serveur Windows, Windows Server 2012 R2 ou Windows Server 2012 R2, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aad23-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="aad23-159">Pour trouver le raccourci de **Windows PowerShell**, utilisez une de ces méthodes :</span><span class="sxs-lookup"><span data-stu-id="aad23-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="aad23-160">Sur l’écran de démarrage, cliquez sur une zone vide et tapez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="aad23-p111">Sur le bureau ou l’écran de démarrage, appuyez sur la touche Windows + touche Q. Dans l’icône de recherche, tapez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="aad23-p112">Sur le bureau ou l’écran de démarrage, déplacez votre curseur dans le coin supérieur droit, ou faites défiler le bord droit de l’écran pour afficher les icônes de gauche. Cliquez sur l’icône de recherche et entrez de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="aad23-165">Dans les résultats, cliquez sur **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="aad23-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="aad23-166">Si la boîte de dialogue **Contrôle de compte d’utilisateur** s’affiche, sélectionnez **Oui** pour vérifier que vous souhaitez exécuter Windows PowerShell sous les informations d’identification de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="aad23-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="aad23-167">Si vous exécutez Windows 7 SP1 (ou Windows Server 2008 R2 SP1), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aad23-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="aad23-p113">Dans le menu **Démarrer** , sélectionnez **Tous les programmes** > **Accessoires** > **De Windows PowerShell**. Avec le bouton droit de **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="aad23-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="aad23-170">Si la boîte de dialogue **Contrôle de compte d’utilisateur** s’affiche, sélectionnez **Oui** pour vérifier que vous souhaitez exécuter Windows PowerShell sous les informations d’identification de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="aad23-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="aad23-p114">Vous devez exécuter Windows PowerShell en tant qu’administrateur. Si vous ne le faites pas, vous allez obtenir un message d’erreur similaire à celui-ci lorsque vous essayez d’importer un des modules requis.</span><span class="sxs-lookup"><span data-stu-id="aad23-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="aad23-p115">Pour remédier à la situation, la seule consiste à fermer Windows PowerShell et redémarrez-le en tant qu’administrateur. Voici un moyen rapide et simple pour savoir si vous exécutez Windows PowerShell en tant qu’administrateur : l’invite est `PS C:\Windows\System32>`, et non pas `PS C:\Users\YourUserName>`.</span><span class="sxs-lookup"><span data-stu-id="aad23-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="aad23-175">Étape 2 : créez un objet d’informations d’identification Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="aad23-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-176"></span></span>

<span data-ttu-id="aad23-p116">L’objet d’informations d’identification offre un moyen crypté pour transmettre votre nom d’utilisateur et le mot de passe pour Windows PowerShell. Pour créer un objet d’informations d’identification, exécutez la commande suivante dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="aad23-p117">`$credential`est une variable qui stocke l’objet d’informations d’identification. Vous n’êtes pas obligé de le nom de la variable `$credential`, mais cela facilite les plus faciles à mémoriser quelle variable contient l’objet d’informations d’identification. (Et c’est important, car nous allons réutiliser cette variable plusieurs fois). Qui rend plus facile de suivre nos exemples, car cet article utilisent toujours `$credential` pour représenter l’objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="aad23-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="aad23-182">Windows PowerShell affiche ensuite une boîte de dialogue qui ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="aad23-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![Boîte de dialogue de demande d’informations d’identifications vides.](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="aad23-184">Tapez votre travail ou à l’école de nom d’utilisateur de compte dans la zone **nom d’utilisateur** , en utilisant format _username@domainname_ (par exemple, kenmyer@litwareinc.onmicrosoft.com) ; Tapez votre mot de passe dans la zone **mot de passe** ; puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="aad23-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![Boîte de dialogue de demande d’informations d’identifications complètes.](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="aad23-p118">Notez que, comme c’est souvent le cas, vous ne verrez aucune sorte de confirmation que l’objet d’informations d’identification a été créé. (Windows PowerShell en général vous indique quand les choses problème mais n’indique toujours pas lorsque les choses tournent droite.) Si vous voulez vérifier que l’objet d’informations d’identification a été créée, dans Windows PowerShell, tapez et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="aad23-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="aad23-188">Quelque chose de ce type doit ensuite apparaître à l’écran.</span><span class="sxs-lookup"><span data-stu-id="aad23-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="aad23-p119">Une chose à retenir ici est que l’applet de commande [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) crée uniquement l’objet d’informations d’identification ; Il ne pas vous authentifier, ou sinon, vérifiez que le nom d’utilisateur et le mot de passe fourni sont corrects. Par exemple, supposons que vous mal tapé le nom d’utilisateur en tant que kenmyer@litwareinc.onmicrosoft.com. Si vous ne le faites que **Get-Credential** crée un objet d’informations d’identification à l’aide de ce nom d’utilisateur et sans vérifier si c’est en fait un nom d’utilisateur valide. Vous ne saurez pas si vous avez créé un objet d’informations d’identification valides réellement jusqu'à ce que vous en fait Utilisez cet objet pour essayer de se connecter aux services Office 365.</span><span class="sxs-lookup"><span data-stu-id="aad23-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="aad23-192">Étape 3 : connectez-vous à Office 365</span><span class="sxs-lookup"><span data-stu-id="aad23-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="aad23-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-193"></span></span>

<span data-ttu-id="aad23-194">Nous allons commencer en vous connectant à Office 365 lui-même.</span><span class="sxs-lookup"><span data-stu-id="aad23-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="aad23-p120">La première chose à faire est d’importer le module Office 365 (le Microsoft Azure Active Directory Module pour Windows PowerShell). Pour ce faire, exécutez cette commande dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="aad23-197">Si vous souhaitez vérifier que le module a été importé, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aad23-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="aad23-198">Dans la liste des modules qui sont retournées par cette commande vous devez voir quelque chose qui ressemble à ceci : `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span><span class="sxs-lookup"><span data-stu-id="aad23-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="aad23-199">Si vous voyez `MSOnline` dans la liste, cela signifie que tout se déroule conformément au plan.</span><span class="sxs-lookup"><span data-stu-id="aad23-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="aad23-200">Avec l’objet d’informations d’identification créée (reportez-vous à la section [étape 2 : créer un objet d’informations d’identification Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) et avec le `MsOnline` module chargé, nous pouvons maintenant se connecter à Office 365 à l’aide de l’applet de commande [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) et de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aad23-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="aad23-p121">Notez que vous devez fournir est l’objet d’informations d’identification ( `$credential`). En fonction de ces informations d’identification, Office 365 se connectera automatiquement vous le domaine approprié. Il est inutile de spécifier votre nom de domaine lors de l’exécution de **MsolService de la connexion**.</span><span class="sxs-lookup"><span data-stu-id="aad23-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="aad23-204">Pour vérifier que vous avez réellement *sont* connecté à Office 365, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="aad23-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="aad23-205">Vous devriez obtenir en retour un élément semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="aad23-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="aad23-206">Étape 4 : connectez-vous à SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="aad23-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="aad23-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-207"></span></span>

<span data-ttu-id="aad23-208">Importer le module SharePoint Online avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="aad23-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="aad23-209">Le commutateur _DisableNameChecking_ supprime cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="aad23-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="aad23-p122">Pour vous connecter à SharePoint Online, vous devez fournir deux éléments d’information : vos informations d’identification et de l’URL de votre site d’administration SharePoint Online. La partie des informations d’identification est simple : nous avons déjà qui stockée dans la variable `$credential` (voir [étape 2 : créer un objet d’informations d’identification Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). En ce qui concerne l’URL de votre site admin, ce qui est assez facile de déterminer également. Supposons que votre nom de domaine d’Office 365 est `litwareinc.onmicrosoft.com`.</span><span class="sxs-lookup"><span data-stu-id="aad23-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="aad23-214">Pour déterminer l’URL du site d’administration, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aad23-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="aad23-215">Démarrer en utilisant le préfixe `https://`.</span><span class="sxs-lookup"><span data-stu-id="aad23-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="aad23-p123">Ajoutez la partie hôte de domaine de votre nom de domaine. Par exemple, pour `litwareinc.onmicrosoft.com`, le nom d’hôte de domaine est `litwareinc`. Pour `contoso.onmicrosoft.com`, le nom d’hôte de domaine est `contoso`.</span><span class="sxs-lookup"><span data-stu-id="aad23-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="aad23-219">Ajouter un trait d’union (-) suivi par `admin.sharepoint.com`.</span><span class="sxs-lookup"><span data-stu-id="aad23-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="aad23-220">En d’autres termes :</span><span class="sxs-lookup"><span data-stu-id="aad23-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="aad23-p124">Une fois que vous avez construit l’URL, vous pouvez ensuite utiliser cette URL et votre objet d’informations d’identification pour se connecter à SharePoint Online. Appeler l’applet de commande [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) , en utilisant une commande semblable à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="aad23-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="aad23-223">Pour vérifier que la connexion a été établie, exécutez la commande suivante dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="aad23-p125">Vous devez obtenir une liste de tous vos sites SharePoint Online. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="aad23-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="aad23-p126">Vos commandes d’Office 365 (ceux qui sont décrits dans [étape 3 : se connecter à Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) fonctionnera toujours. (Essayez d’exécuter **Get-MsolUser**et voyez par vous-même). Cela signifie que vous pouvez désormais gérer Office 365 et SharePoint Online à partir de la même instance de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="aad23-228">Étape 5 : connectez-vous à Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="aad23-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="aad23-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-229"></span></span>

<span data-ttu-id="aad23-p127">Connexion à Skype pour Business Online (et à Exchange en ligne ou à la sécurité &amp; centre de conformité) est différent de celui de la connexion à Office 365 ou à SharePoint Online. C’est parce que le Skype pour les applets de commande Business Online et Exchange Online n’installé sur votre ordinateur comme l’Office 365 et les applets de commande SharePoint Online. Au lieu de cela, chaque fois que vous vous connectez, les applets de commande appropriés sont copiés temporairement sur votre ordinateur. Lorsque vous vous connectez hors tension, ces applets de commande sont ensuite supprimés à partir de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aad23-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="aad23-p128">Pour vous connecter sur Skype pour professionnels en ligne, vous devez importer le Skype pour module Business Online. Pour ce faire, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aad23-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="aad23-236">La première fois que vous le faites, il se peut que le message d’avertissement suivant apparaisse. Vous pouvez l’ignorer sans risque.</span><span class="sxs-lookup"><span data-stu-id="aad23-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="aad23-237">Une fois le module importé, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="aad23-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="aad23-p129">Nous avons créé une session PowerShell distante. Dans ce cas, cela signifie que nous avons connecté à une instance de Windows PowerShell s’exécutant sur un des serveurs Office 365.</span><span class="sxs-lookup"><span data-stu-id="aad23-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="aad23-p130">Bien que nous avons établi une connexion à Office 365, nous n’avons pas téléchargé les scripts, les applets de commande et les autres éléments nécessaires à la gestion de Skype pour l’activité en ligne. Pour ce faire, nous devons exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="aad23-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="aad23-242">Lorsque vous importez la session Windows PowerShell, vous devriez voir une barre de progression semblable à la suivante, une barre de progression qui génère des rapports sur tous le Skype pour les applets de commande entreprise en ligne en cours d’importation sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aad23-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Barre de progression de Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="aad23-244">Lorsque la barre de progression disparaît, un résultat semblable à celui ci-dessous apparaît :</span><span class="sxs-lookup"><span data-stu-id="aad23-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="aad23-245">Étape 6 : connectez-vous à Exchange Online</span><span class="sxs-lookup"><span data-stu-id="aad23-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="aad23-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-246"></span></span>

<span data-ttu-id="aad23-247">Exécutez cette commande, qui crée une session à distance de Windows PowerShell avec Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="aad23-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="aad23-p131">Pourquoi est-la commande pour se connecter à Exchange Online plus complexe que la commande se connecter sur Skype pour Business en ligne ? Techniquement, il ne l’est pas : les deux commandes font exactement la même chose. Toutefois, le Skype pour une équipe commerciale en ligne créé sa propre cmdlet : **New-CsOnlineSession** , qui masque certains paramètres (tels que _l’authentification_ et _AllowRedirection_) qui sont utilisés lors de la connexion à Exchange Online. Au lieu de vous obliger à taper vous-même les informations, les paramètres _d’authentification_ et de _AllowRedirection_ sont effectivement intégrées dans l’applet de commande **New-CsOnlineSession** . Vous devez taper ces paramètres lors de la connexion à Exchange Online, dans la mesure où Exchange Online utilise l’applet de commande [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) standard pour se connecter à Office 365. L’inconvénient est que vous devez taper un peu plus pour faire. L’avantage est que vous n’êtes pas obligé de télécharger et d’installer un module Exchange en ligne.</span><span class="sxs-lookup"><span data-stu-id="aad23-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="aad23-255">Il vous est maintenant importer cette session à distance, comme nous l’avons fait avec Skype pour entreprise en ligne.</span><span class="sxs-lookup"><span data-stu-id="aad23-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="aad23-256">Quelque chose de ce type doit apparaître à l’écran.</span><span class="sxs-lookup"><span data-stu-id="aad23-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="aad23-257">Maintenant, essayez d’exécuter la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aad23-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="aad23-258">En retour, vous devez voir des informations concernant vos domaines Office 365 qui sont configurés pour des adresses de messagerie dans Exchange en ligne.</span><span class="sxs-lookup"><span data-stu-id="aad23-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="aad23-259">Étape 7 : Se connecter à la sécurité &amp; centre de conformité</span><span class="sxs-lookup"><span data-stu-id="aad23-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="aad23-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-260"></span></span>

<span data-ttu-id="aad23-p132">La sécurité &amp; centre de conformité est un service de Office 365 vous permettant de gérer les fonctions de conformité à partir d’un seul emplacement. Pour plus d’informations, consultez le [Centre de conformité d’Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span><span class="sxs-lookup"><span data-stu-id="aad23-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="aad23-263">Les instructions de connexion pour la sécurité &amp; centre de conformité sont très similaires à celles d’Exchange Online, mais avec une torsion ajoutée, que vous verrez dans un moment.</span><span class="sxs-lookup"><span data-stu-id="aad23-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="aad23-264">Exécutez cette commande, ce qui crée une session PowerShell à distance avec la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="aad23-265">À présent, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="aad23-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="aad23-p133">À nouveau, cette commande est très similaire à la commande pour Exchange Online. Le commutateur _DisableNameChecking_ n’est pas nécessaire, car il n’y aucun verbe non approuvé dans la sécurité &amp; centre de conformité. Mais qu’en est-il des `-Prefix cc` paramètre et valeur ? C’est la torsion ajoutée que nous vous informé.</span><span class="sxs-lookup"><span data-stu-id="aad23-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="aad23-p134">Exchange Online et la sécurité &amp; centre de conformité partager des applets de commande qui ont exactement le même nom et offrent les mêmes fonctionnalités. **Get-RoleGroup** est un exemple.</span><span class="sxs-lookup"><span data-stu-id="aad23-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="aad23-p135">Que se passe-t-il si vous essayez d’importer les deux sessions contenant des applets de commande avec le même nom ? Ils entrent en collision. Vous obtiendrez un message d’avertissement jaune big indiquant, `WARNING: Proxy creation has been skipped for the following command:` suivie de la liste des applets de commande en conflit qui n’a pas pu être importés. Le résultat final ? Vous pouvez exécuter **Get-RoleGroup** dans Exchange Online car vous connecté il tout d’abord, mais vous ne pouvez pas exécuter **Get-RoleGroup** dans la sécurité &amp; car vous il le dernier connecté et les applets de commande en conflit a refusé d’importer du centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="aad23-p136">Pour résoudre ce problème le plus simple est d’ajouter un préfixe de texte arbitraire à la sécurité importé &amp; applets de commande de centre de conformité. Nous avons fait que l’utilisation du _préfixe de_ paramètre avec la valeur « cc » sur la cmdlet **Import-PSSession** . Que qui nous aider ? Il d’éliminer les conflits par la modification de la sécurité (légèrement) &amp; noms d’applet de commande de centre de conformité pour cette session. Ensemble de la sécurité importée &amp; applets de commande de centre de conformité maintenant commencent avec « cc » dans la partie substantif du nom de l’applet de commande (à droite de la «- »). Par exemple, l’applet de commande **Get-RoleGroup** contentieuse devienne **Get-ccRoleGroup** pour la sécurité &amp; centre de conformité afin qu’il n’entre en conflit avec **Get-RoleGroup** pour Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="aad23-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="aad23-p137">L’inconvénient ?  *Tous les*  Sécurité &amp; noms d’applet de commande de centre de conformité recevoir le préfixe « cc » — même les applets de commande unique qui n’est pas nécessaire. Par exemple, **Get-ComplianceSearch** devient **Get-ccComplianceSearch** , même s’il n’existe pas cette applet de commande dans Exchange en ligne. Il est un peu une douleur, mais pas trop mal lorsque vous considérez les avantages de la gestion de tous les services Office 365 dans une même session Windows PowerShell. N’oubliez pas d’ajouter « cc » pour les noms d’applet de commande pour toutes les procédures de sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="aad23-288">Si tout se passe bien, vous obtenez un résultat de ce type :</span><span class="sxs-lookup"><span data-stu-id="aad23-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="aad23-289">Maintenant, vous êtes libre de gérer tous les services Office 365 dans une même session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aad23-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="aad23-290">Étape 8 : arrêtez votre session PowerShell convenablement</span><span class="sxs-lookup"><span data-stu-id="aad23-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="aad23-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-291"></span></span>

<span data-ttu-id="aad23-p138">Si vous fermez la fenêtre Windows PowerShell, votre Skype pour entreprise en ligne connexion à distance reste active pour la prochaine environ 15 minutes. Étant donné que Skype pour Business Online limite le nombre de connexions simultanées qu’une personne ou à tout un domaine peut ouvrir, qui pourrait être un problème. Avec Skype pour professionnels en ligne, un administrateur peut avoir, au plus, trois connexions ouvertes en même temps, et un domaine peut posséder un maximum de neuf des connexions ouvertes. Si vous vous connecter sur Skype pour Business Online avant de quittez sans fermer correctement la session, la session reste ouverte pour la prochaine environ 15 minutes. Par conséquent, qui est une connexion moins disponible à vous ou à d’autres administrateurs de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="aad23-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="aad23-p139">Au lieu de cela, fermons les sessions à distance pour Skype pour Business Online, Exchange Online et de la sécurité &amp; normalement du centre de conformité. Avant cela, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aad23-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="aad23-p140">L’applet de commande [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) doit vous indiquer que vous avez ouvert d’au moins trois sessions à distance, un pour Skype pour professionnels en ligne, un pour Exchange Online et un pour la sécurité &amp; centre de conformité (il est possible, vous pourriez avoir plus de trois distants sessions en cours d’exécution, en fonction de si vous avez utilisé cette instance de Windows PowerShell pour se connecter à quelque chose d’autre, outre les services Office 365). Vous devriez voir quelque chose de similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="aad23-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="aad23-p141">Pour fermer ces trois sessions, exécuter ces commandes à la fois. La première commande ferme le Skype pour session Business Online, la deuxième ferme la session Exchange en ligne, et la troisième ferme la sécurité &amp; session de centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="aad23-303">Si vous exécutez maintenant l’applet de commande **Get-PSSession** , vous devez voir rien (à moins d’avoir d’autres sessions à distance en hausse et en cours d’exécution).</span><span class="sxs-lookup"><span data-stu-id="aad23-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![Console Windows PowerShell sans session distante](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="aad23-305">Si vous préférez fermer tous vos sessions à distance en même temps, vous pouvez utiliser cette commande : >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="aad23-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="aad23-306">Si vous essayez maintenant d’exécuter une applet de commande à partir d’un de ces fermé les sessions (par exemple, **Get-CsMeetingConfiguration** dans Skype pour Business Online), vous obtiendrez un message d’erreur semblable à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="aad23-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="aad23-307">Nous obtenons ce message d’erreur parce que les applets de commande pour Skype pour Business Online, Exchange Online et de la sécurité &amp; centre de conformité ont été supprimés lorsque nous avons fermé les sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="aad23-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="aad23-308">Pour fermer la session SharePoint Online, tapez cette commande.</span><span class="sxs-lookup"><span data-stu-id="aad23-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="aad23-309">Si vous tentez d’exécuter l’applet de commande **Get-SPOSite** , vous obtiendrez un message d’erreur comme suit.</span><span class="sxs-lookup"><span data-stu-id="aad23-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="aad23-310">Impossible de récupérer les informations de site, car vous êtes connecté n’est plus sur SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="aad23-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="aad23-p142">Comme pour votre connexion à Office 365, bien qu’il existe une applet de commande **Connect-MsolService** , il n’y a aucune cmdlet **Disconnect-MsolService** correspondant. Par conséquent, pour Office 365, fermez la fenêtre Windows PowerShell. Néanmoins, il est toujours judicieux de ce dernier afin que vous puissiez correctement déconnecter à partir de SharePoint en ligne, Skype pour Business Online, Exchange Online et la sécurité &amp; centre de conformité.</span><span class="sxs-lookup"><span data-stu-id="aad23-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="aad23-314">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="aad23-314">New to Office 365?</span></span>
<span data-ttu-id="aad23-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="aad23-315"></span></span>

||
|:-----|
|<span data-ttu-id="aad23-p143">![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les [professionnels de l’informatique et les administrateurs d’Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="aad23-p143">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="aad23-318">See also</span><span class="sxs-lookup"><span data-stu-id="aad23-318">See also</span></span>

#### 

[<span data-ttu-id="aad23-319">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad23-319">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="aad23-320">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="aad23-320">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="aad23-321">Gestion de SharePoint Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad23-321">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="aad23-322">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad23-322">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="aad23-323">Utilisez Windows PowerShell pour créer des rapports dans Office 365</span><span class="sxs-lookup"><span data-stu-id="aad23-323">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

