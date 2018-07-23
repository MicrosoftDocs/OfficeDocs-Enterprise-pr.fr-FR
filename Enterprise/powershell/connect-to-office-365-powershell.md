---
title: Se connecter à Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
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
description: 'Résumé : Se connecter à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches du centre d’administration à partir de la ligne de commande.'
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720400"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="36f66-103">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f66-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="36f66-104">**Résumé :** Se connecter à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches d’administration à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="36f66-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="36f66-p101">Office 365 PowerShell vous permet pour gérer vos paramètres de Office 365 à partir de la ligne de commande. Connexion à Office 365 PowerShell est un processus en trois étapes simple où vous installez les logiciels requis, exécuter des logiciels requis et puis connectez à votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="36f66-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="36f66-p102">**Nouveau PowerShell ?** Consultez une [Présentation vidéo de PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), proposée par apprentissage LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="36f66-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="36f66-109">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="36f66-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="36f66-110">Durée d'exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="36f66-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="36f66-111">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="36f66-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="36f66-112">10 Windows, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="36f66-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="36f66-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="36f66-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="36f66-p103">Utilisez une version 64 bits de Windows. Prise en charge pour la version 32 bits du Microsoft Azure Active Directory Module pour Windows PowerShell a été abandonné en octobre de 2014.</span><span class="sxs-lookup"><span data-stu-id="36f66-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="36f66-p104">Ces procédures sont destinés aux utilisateurs qui sont membres d’un rôle d’administration d’Office 365. Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="36f66-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="36f66-118">Se connecter avec Azure Active Directory PowerShell pour le module de graphique</span><span class="sxs-lookup"><span data-stu-id="36f66-118">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="36f66-119">Commandes dans le module [Azure Active Directory PowerShell graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ont **AzureAD** dans leur nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36f66-119">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="36f66-120">Pour les procédures qui nécessitent les nouvelles applets de commande dans Azure Active Directory PowerShell pour module graphique, suivez ces étapes pour installer le module et se connecter à votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="36f66-120">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="36f66-121">Pour plus d’informations sur la prise en charge pour les différentes versions de Microsoft Windows, voir [Windows Azure Active Directory PowerShell pour le module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="36f66-121">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="36f66-122">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="36f66-122">Step 1: Install required software</span></span>

<span data-ttu-id="36f66-p105">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="36f66-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="36f66-125">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutée Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="36f66-125">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="36f66-126">Dans la **administrateur : Windows PowerShell** fenêtre de commande, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="36f66-126">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="36f66-127">Si vous y êtes invité sur l’installation d’un module à partir d’un référentiel non approuvé, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="36f66-127">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="36f66-128">Étape 2 : Se connecter à Azure AD pour votre abonnement à Office 365</span><span class="sxs-lookup"><span data-stu-id="36f66-128">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="36f66-129">Pour vous connecter à AD Azure pour Office 365 abonnement avec un nom de compte et le mot de passe ou *l’authentification multifacteur (MFA)* exécutez cette commande à partir d’une invite de commandes Windows PowerShell (il ne doit pas être avec élévation de privilèges) :</span><span class="sxs-lookup"><span data-stu-id="36f66-129">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)* run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="36f66-130">Dans la boîte de dialogue **se connecter à votre compte** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36f66-130">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="36f66-131">Si vous utilisez MFA, suivez les instructions indiquées dans les boîtes de dialogue supplémentaires pour fournir plus d’informations d’authentification, par exemple un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="36f66-131">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>
    
<span data-ttu-id="36f66-132">Une fois connecté, vous pouvez utiliser les nouvelles applets de commande pour [Azure Active Directory PowerShell pour le module de graphique](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="36f66-132">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="36f66-133">Se connecter avec le Module d’Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f66-133">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="36f66-134">Commandes dans le Microsoft Azure Active Directory Module pour Windows PowerShell ont **Msol** dans leur nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36f66-134">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="36f66-135">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="36f66-135">Step 1: Install required software</span></span>

<span data-ttu-id="36f66-p106">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="36f66-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="36f66-138">Installer la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant connexion de Microsoft Online Services pour les professionnels de l’informatique RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="36f66-138">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="36f66-139">Installer le Microsoft Azure Active Directory Module pour Windows PowerShell en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="36f66-139">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="36f66-140">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutée Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="36f66-140">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="36f66-141">Exécutez la commande **Install-Module MSOnline** .</span><span class="sxs-lookup"><span data-stu-id="36f66-141">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="36f66-142">Si vous êtes invité à installer le fournisseur NuGet, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="36f66-142">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="36f66-143">Si vous êtes invité à installer le module de PSGallery, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="36f66-143">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="36f66-144">Étape 2 : Se connecter à Azure AD pour votre abonnement à Office 365</span><span class="sxs-lookup"><span data-stu-id="36f66-144">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="36f66-145">Pour vous connecter à Azure AD pour votre abonnement à Office 365 avec un nom de compte et le mot de passe ou *l’authentification multifacteur (MFA)*, exécutez cette commande à partir d’une invite de commandes Windows PowerShell (il ne doit pas être avec élévation de privilèges) :</span><span class="sxs-lookup"><span data-stu-id="36f66-145">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="36f66-146">Dans la boîte de dialogue **se connecter à votre compte** , tapez votre bureau Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36f66-146">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="36f66-147">Si vous utilisez MFA, suivez les instructions indiquées dans les boîtes de dialogue supplémentaires pour fournir plus d’informations d’authentification, par exemple un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="36f66-147">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="36f66-148">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="36f66-148">How do you know this worked?</span></span>

<span data-ttu-id="36f66-p107">Si vous ne recevez des erreurs, vous connecté avec succès. Un test rapide consiste à exécuter une applet de commande Office 365 — par exemple, **Get-MsolUser** — et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="36f66-p107">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="36f66-151">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="36f66-151">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="36f66-p108">**Un mot de passe incorrect est un problème courant**. Exécutez à nouveau l’étape 3 et portez une attention particulière au nom d’utilisateur et au mot de passe que vous saisissez.</span><span class="sxs-lookup"><span data-stu-id="36f66-p108">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="36f66-p109">\* *Le Microsoft Azure Active Directory Module pour Windows PowerShell requiert que Microsoft .NET Framework 3.5.* fonctionnalité de x est activée sur votre ordinateur \**. Il est probable qu’une version plus récente est installée sur votre ordinateur (par exemple, 4 ou 4.5.* x \*), mais à compatibilité descendante compatibilité avec les versions antérieures du .NET Framework peut être activée ou désactivée. Pour plus d’informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="36f66-p109">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="36f66-157">Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Activer .NET Framework 3.5 à l’aide de l’ajout de rôles et fonctionnalités Assistant](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="36f66-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="36f66-158">Pour Windows 8 ou Windows 8.1, voir [installation de .NET Framework 3.5 sur Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="36f66-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="36f66-159">Pour Windows 7 ou Windows Server 2008 R2, voir [vous ne peuvent pas ouvrir les Azure Active Directory Module pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="36f66-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="36f66-160">Pour Windows 10, Windows 8 et Windows 8.1, voir [installer .NET Framework 3.5 sur 10 Windows, Windows 8.1 et Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="36f66-160">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="36f66-p110">**Votre version de la Microsoft Azure Active Directory Module pour Windows PowerShell est peut-être obsolète.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le Microsoft Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="36f66-p110">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="36f66-163">Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Microsoft Azure Active Directory Module pour Windows PowerShell et installez la dernière version à partir du lien à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="36f66-163">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="36f66-164">**Si vous recevez une erreur de connexion, consultez la rubrique suivante :** [« Connect-MsolService : a levé une Exception de type « erreur](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="36f66-164">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="36f66-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36f66-165">See also</span></span>

- [<span data-ttu-id="36f66-166">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f66-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="36f66-167">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="36f66-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="36f66-168">Connexion à tous les services Office 365 à l'aide d'une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36f66-168">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="36f66-169">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="36f66-169">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="36f66-170">Connecter-MsolService</span><span class="sxs-lookup"><span data-stu-id="36f66-170">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

