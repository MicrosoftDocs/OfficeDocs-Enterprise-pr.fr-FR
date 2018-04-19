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
description: 'Résumé : Connexion à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches de centre d’administration Office 365 à partir de la ligne de commande.'
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="838fd-103">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="838fd-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="838fd-104">**Résumé :** Se connecter à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches d’administration Office 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="838fd-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="838fd-p101">Office 365 PowerShell vous permet pour gérer vos paramètres Office 365 à partir de la ligne de commande. Se connecter à Office 365 PowerShell est un processus en trois étapes simple où vous installez les logiciels requis, exécuter les logiciels requis et puis connectez à votre organisation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="838fd-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="838fd-p102">**Nouveau PowerShell ?** Voir une [Présentation vidéo de PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="838fd-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="838fd-109">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="838fd-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="838fd-110">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="838fd-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="838fd-111">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="838fd-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="838fd-112">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="838fd-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="838fd-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="838fd-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="838fd-p103">Utilisez une version 64 bits de Windows. Prise en charge de la version 32 bits du Microsoft Azure Active Directory Module pour Windows PowerShell a été interrompu en octobre de 2014.</span><span class="sxs-lookup"><span data-stu-id="838fd-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="838fd-p104">Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="838fd-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="838fd-118">Se connecter avec le Module Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="838fd-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="838fd-119">Commandes dans la Microsoft Azure Active Directory Module pour Windows PowerShell ont **Msol** dans leur nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="838fd-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="838fd-120">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="838fd-120">Step 1: Install required software</span></span>

<span data-ttu-id="838fd-p105">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="838fd-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="838fd-123">Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Microsoft Online Services - Assistant de connexion pour la version RTW de professionnels de l’informatique](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="838fd-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="838fd-124">Installez le Microsoft Azure Active Directory Module pour Windows PowerShell avec ces étapes :</span><span class="sxs-lookup"><span data-stu-id="838fd-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="838fd-125">Ouvrez une invite de commandes de PowerShell de niveau administrateur.</span><span class="sxs-lookup"><span data-stu-id="838fd-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="838fd-126">Exécutez la commande **MSOnline du Module d’installation** .</span><span class="sxs-lookup"><span data-stu-id="838fd-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="838fd-127">Si vous êtes invité à installer le fournisseur de NuGet, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="838fd-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="838fd-128">Si vous êtes invité à installer le module à partir de PSGallery, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="838fd-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="838fd-129">Après l’installation, fermez la fenêtre de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="838fd-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="838fd-130">Étape 2 : Se connecter à votre abonnement à Office 365</span><span class="sxs-lookup"><span data-stu-id="838fd-130">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="838fd-131"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="838fd-131"></span></span>

<span data-ttu-id="838fd-132">Se connecter avec seulement un *nom de compte et de mot de passe*:</span><span class="sxs-lookup"><span data-stu-id="838fd-132">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="838fd-133">Exécuter à une invite de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="838fd-133">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="838fd-134">Dans la fenêtre de commande **Windows PowerShell** , exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="838fd-134">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="838fd-135">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="838fd-135">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="838fd-136">Se connecter avec *l’authentification par plusieurs facteur (AMF)*:</span><span class="sxs-lookup"><span data-stu-id="838fd-136">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="838fd-137">Exécuter à une invite de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="838fd-137">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="838fd-138">Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="838fd-138">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="838fd-139">Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="838fd-139">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="838fd-140">Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="838fd-140">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="838fd-141">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="838fd-141">How do you know this worked?</span></span>
<span data-ttu-id="838fd-142"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="838fd-142"></span></span>

<span data-ttu-id="838fd-p106">Si vous ne recevez pas d’erreurs, vous est connecté correctement. Un test rapide est d’exécuter une applet de commande d’Office 365, par exemple, **Get-MsolUser** et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="838fd-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="838fd-145">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="838fd-145">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="838fd-p107">**Un problème courant est un mot de passe incorrect**. Réexécutez l’étape 3. et faites attention pour le nom d’utilisateur et le mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="838fd-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="838fd-p108">\* *Le Microsoft Azure Active Directory Module pour Windows PowerShell requiert que le Microsoft.NET Framework 3.5.* fonctionnalité de x est activée sur votre ordinateur \**. Il est probable que votre ordinateur dispose d’une version plus récente est installée (par exemple, les 4 ou 4.5.* x \*), mais en arrière la compatibilité avec les versions antérieures du.NET Framework peut être activée ou désactivée. Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="838fd-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="838fd-151">Pour Windows Server 2012 ou de Windows Server 2012 R2, voir [Activer le.NET Framework 3.5 à l’aide de l’ajout de rôles et fonctionnalités Assistant](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="838fd-151">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="838fd-152">Pour Windows 8 ou Windows 8.1, consultez [installer le 3.5 de.NET Framework sur Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="838fd-152">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="838fd-153">Pour Windows 7 ou Windows Server 2008 R2, consultez [Impossible d’ouvrir le Module Azure pour annuaire Active pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="838fd-153">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="838fd-p109">**Votre version de la Microsoft Azure Active Directory Module pour Windows PowerShell est peut-être périmée.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le Microsoft Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="838fd-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="838fd-156">Si le numéro de version retourné est inférieur à la valeur 1.0.8070.2, désinstallez le Microsoft Azure Active Directory Module pour Windows PowerShell et installer la dernière version à partir du lien à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="838fd-156">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="838fd-157">**Si vous recevez une erreur de connexion, consultez la rubrique suivante :** [« Connect-MsolService : la levée de l’Exception de type » erreur](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="838fd-157">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="838fd-158">Se connecter avec Azure Active Directory PowerShell pour module de graphique</span><span class="sxs-lookup"><span data-stu-id="838fd-158">Connect with the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="838fd-159"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="838fd-159"></span></span>

<span data-ttu-id="838fd-160">Commandes dans Azure Active Directory PowerShell pour module de graphique ont « AzureAD » dans leur nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="838fd-160">Commands in the Azure Active Directory PowerShell for Graph module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="838fd-161">Pour les procédures nécessitant les nouvelles applets de commande PowerShell Active Directory Azure pour module de graphique, suivez ces étapes pour installer le module et le connecter à votre abonnement à Office 365.</span><span class="sxs-lookup"><span data-stu-id="838fd-161">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="838fd-162">Pour plus d’informations sur la prise en charge pour les différentes versions de Microsoft Windows, reportez-vous à la section [Azure de Active Directory PowerShell pour module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="838fd-162">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="838fd-163">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="838fd-163">Step 1: Install required software</span></span>

<span data-ttu-id="838fd-p110">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="838fd-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="838fd-166">Ouvrez une invite de commande Windows PowerShell avec élévation de privilèges (d’exécution Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="838fd-166">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="838fd-167">Dans la **administrateur : Windows PowerShell** fenêtre de commande, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="838fd-167">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="838fd-168">Si vous êtes invité à propos de l’installation d’un module à partir d’un référentiel non approuvé, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="838fd-168">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="838fd-169">Étape 2 : Se connecter à Office 365</span><span class="sxs-lookup"><span data-stu-id="838fd-169">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="838fd-170">Pour vous connecter à votre abonnement à Office 365 avec un *nom de compte et de mot de passe*:</span><span class="sxs-lookup"><span data-stu-id="838fd-170">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="838fd-171">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="838fd-171">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="838fd-172">Pour vous connecter à votre abonnement à Office 365 avec *une authentification multifacteur (AMF)*:</span><span class="sxs-lookup"><span data-stu-id="838fd-172">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="838fd-173">Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="838fd-173">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="838fd-174">Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="838fd-174">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="838fd-175">Une fois connecté, vous pouvez utiliser les nouvelles applets de commande pour [Azure de Active Directory PowerShell pour module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="838fd-175">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="838fd-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="838fd-176">See also</span></span>

- [<span data-ttu-id="838fd-177">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="838fd-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="838fd-178">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="838fd-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="838fd-179">Connexion à tous les services Office 365 à l'aide d'une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="838fd-179">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="838fd-180">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="838fd-180">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="838fd-181">MsolService de connexion</span><span class="sxs-lookup"><span data-stu-id="838fd-181">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

