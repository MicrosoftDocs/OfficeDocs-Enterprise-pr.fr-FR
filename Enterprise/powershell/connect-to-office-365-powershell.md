---
title: Se connecter à Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Résumé: Connectez-vous à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer des tâches du centre d’administration à partir de la ligne de commande.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639775"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="36578-103">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36578-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="36578-104">**Résumé:** Connectez-vous à votre organisation Office 365 à l’aide d’Office 365 PowerShell pour effectuer des tâches d’administration à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="36578-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="36578-105">Office 365 PowerShell vous permet de gérer vos paramètres Office 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="36578-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="36578-106">La connexion à Office 365 PowerShell est un processus simple qui vous permet d’installer les logiciels requis, puis de vous connecter à votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="36578-106">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="36578-107">Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Office 365 et administrer les comptes d’utilisateurs, les groupes et les licences:</span><span class="sxs-lookup"><span data-stu-id="36578-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="36578-108">Azure Active Directory PowerShell pour Graph (les cmdlets incluent **AzureAD** dans leur nom)</span><span class="sxs-lookup"><span data-stu-id="36578-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="36578-109">Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSOL** dans leur nom)</span><span class="sxs-lookup"><span data-stu-id="36578-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="36578-110">À la date de cet article, le module Azure Active Directory PowerShell for Graph ne remplace pas entièrement les fonctionnalités des applets de commande du module Microsoft Azure Active Directory pour le module Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences. .</span><span class="sxs-lookup"><span data-stu-id="36578-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="36578-111">Dans de nombreux cas, vous devez utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="36578-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="36578-112">Vous pouvez installer les deux versions en toute sécurité sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="36578-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="36578-113">**Vous débutez avec PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="36578-113">**New to PowerShell?**</span></span> <span data-ttu-id="36578-114">Consultez une [Présentation vidéo de PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), qui vous a été proposée par LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="36578-114">See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="36578-115">Ce qu'il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="36578-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="36578-116">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="36578-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="36578-117">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="36578-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="36578-118">Windows 10, Windows 8,1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="36578-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="36578-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="36578-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="36578-120">Utilisez une version 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="36578-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="36578-121">Prise en charge de la version 32 bits le module Microsoft Azure Active Directory pour Windows PowerShell a été abandonné en octobre 2014.</span><span class="sxs-lookup"><span data-stu-id="36578-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="36578-122">Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="36578-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="36578-123">Pour obtenir plus d’informations, consultez l’article [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="36578-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="36578-124">Se connecter avec le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="36578-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="36578-125">Les commandes dans le module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ont **AzureAD** dans leur nom de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36578-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="36578-126">Pour les procédures nécessitant les nouvelles applets de commande dans le module Azure Active Directory PowerShell pour Graph, procédez comme suit pour installer le module et vous connecter à votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="36578-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="36578-127">Consultez la rubrique [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) pour obtenir des informations sur la prise en charge de différentes versions de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="36578-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="36578-128">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="36578-128">Step 1: Install required software</span></span>

<span data-ttu-id="36578-p106">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="36578-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="36578-131">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="36578-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="36578-132">Dans la fenêtre de commande **administrateur: Windows PowerShell** , exécutez la commande suivante:</span><span class="sxs-lookup"><span data-stu-id="36578-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="36578-133">Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **Y** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="36578-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="36578-134">Étape 2: Connectez-vous à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="36578-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="36578-135">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom de compte et un mot de passe ou avec *l’authentification multifacteur (MFA)*, exécutez l’une de ces commandes à partir d’une invite de commandes Windows PowerShell (elle n’a pas besoin d’être élevée).</span><span class="sxs-lookup"><span data-stu-id="36578-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="36578-136">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="36578-136">**Office 365 cloud**</span></span> | <span data-ttu-id="36578-137">**Command**</span><span class="sxs-lookup"><span data-stu-id="36578-137">**Command**</span></span> |
| <span data-ttu-id="36578-138">Office 365 dans le monde entier (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="36578-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="36578-139">Office 365 géré par 21 VIANET</span><span class="sxs-lookup"><span data-stu-id="36578-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="36578-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="36578-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="36578-141">Office 365 gouvernement américain DoD and Office 365 gouvernement américain GCC High</span><span class="sxs-lookup"><span data-stu-id="36578-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="36578-142">Dans la boîte de dialogue **se connecter à votre compte** , entrez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36578-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="36578-143">Si vous utilisez l’authentification multiFACTEUR, suivez les instructions des boîtes de dialogue supplémentaires pour fournir des informations d’authentification supplémentaires, telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="36578-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="36578-144">Une fois la connexion établie, vous pouvez utiliser les nouvelles applets de commande pour le [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="36578-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="36578-145">Se connecter au module Microsoft Azure Active Directory pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36578-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="36578-146">Les commandes du module Microsoft Azure Active Directory pour Windows PowerShell ont **MSOL** dans leur nom de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36578-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="36578-147">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="36578-147">Step 1: Install required software</span></span>

<span data-ttu-id="36578-p107">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="36578-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="36578-150">Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services: Assistant de [connexion Microsoft Online Services pour les professionnels de l’informatique RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="36578-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="36578-151">Installez le module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit:</span><span class="sxs-lookup"><span data-stu-id="36578-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="36578-152">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="36578-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="36578-153">Exécutez la commande **install-module MSONLINE** .</span><span class="sxs-lookup"><span data-stu-id="36578-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="36578-154">Si vous êtes invité à installer le fournisseur NuGet, tapez **Y** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="36578-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="36578-155">Si vous êtes invité à installer le module à partir de PSGallery, tapez **Y** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="36578-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="36578-156">Étape 2: Connectez-vous à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="36578-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="36578-157">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom de compte et un mot de passe ou avec *l’authentification multifacteur (MFA)*, exécutez l’une de ces commandes à partir d’une invite de commandes Windows PowerShell (elle n’a pas besoin d’être élevée).</span><span class="sxs-lookup"><span data-stu-id="36578-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="36578-158">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="36578-158">**Office 365 cloud**</span></span> | <span data-ttu-id="36578-159">**Command**</span><span class="sxs-lookup"><span data-stu-id="36578-159">**Command**</span></span> |
| <span data-ttu-id="36578-160">Office 365 dans le monde entier (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="36578-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="36578-161">Office 365 géré par 21 VIANET</span><span class="sxs-lookup"><span data-stu-id="36578-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="36578-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="36578-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="36578-163">Office 365 gouvernement américain DoD and Office 365 gouvernement américain GCC High</span><span class="sxs-lookup"><span data-stu-id="36578-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="36578-164">Dans la boîte de dialogue **se connecter à votre compte** , entrez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36578-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="36578-165">Si vous utilisez l’authentification multiFACTEUR, suivez les instructions des boîtes de dialogue supplémentaires pour fournir des informations d’authentification supplémentaires, telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="36578-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="36578-166">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="36578-166">How do you know this worked?</span></span>

<span data-ttu-id="36578-167">Si vous ne recevez aucune erreur, la connexion est établie.</span><span class="sxs-lookup"><span data-stu-id="36578-167">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="36578-168">Un test rapide consiste à exécuter une cmdlet Office 365 (par exemple, **Get-MsolUser** ) et à afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="36578-168">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="36578-169">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="36578-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="36578-170">**Un problème courant est un mot de passe incorrect**.</span><span class="sxs-lookup"><span data-stu-id="36578-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="36578-171">Exécutez à nouveau l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="36578-171">Run Step 2 again.</span></span> <span data-ttu-id="36578-172">et faites attention au nom d’utilisateur et au mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="36578-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="36578-173">\* *Le module Microsoft Azure Active Directory pour Windows PowerShell requiert Microsoft .net Framework 3,5.* la fonctionnalité x \* est activée sur votre ordinateur \* *. Il est probable que votre ordinateur dispose d’une version plus récente (par exemple, 4 ou 4,5.* x \*), mais la compatibilité descendante avec les versions antérieures de .NET Framework peut être activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="36578-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="36578-174">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="36578-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="36578-175">Pour Windows Server 2012 ou Windows Server 2012 R2, consultez [la rubrique activer .NET Framework 3,5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités](https://go.microsoft.com/fwlink/p/?LinkId=532368) .</span><span class="sxs-lookup"><span data-stu-id="36578-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="36578-176">Pour Windows 7 ou Windows Server 2008 R2, consultez [l’impossibilité d’ouvrir le module Azure Active Directory pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="36578-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="36578-177">Pour Windows 10, Windows 8,1 et Windows 8, consultez [la rubrique installer .NET Framework 3,5 sur Windows 10, windows 8,1 et Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="36578-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="36578-178">**Votre version du module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.**</span><span class="sxs-lookup"><span data-stu-id="36578-178">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="36578-179">Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le module Microsoft Azure Active Directory pour Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="36578-179">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="36578-180">Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le module Microsoft Azure Active Directory pour Windows PowerShell et installez la version la plus récente à partir du lien à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="36578-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="36578-181">**Si vous recevez une erreur de connexion, reportez-vous à cette rubrique:** [Erreur «Connect-MsolService: exception de type a été levée»](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="36578-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="36578-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36578-182">See also</span></span>

- [<span data-ttu-id="36578-183">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36578-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="36578-184">Mise en route d’Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36578-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="36578-185">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36578-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="36578-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="36578-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="36578-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="36578-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

