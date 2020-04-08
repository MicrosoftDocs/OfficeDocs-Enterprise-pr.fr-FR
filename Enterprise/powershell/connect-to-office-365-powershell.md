---
title: Se connecter à PowerShell Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/31/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Connectez-vous à votre organisation Office 365 à l’aide de PowerShell Office 365 pour effectuer les tâches d’administration à partir de la ligne de commande.
ms.openlocfilehash: 00c4e303faa7a182a9bd5c859a09ad150fc0b8d4
ms.sourcegitcommit: b1042fa2d02f1bc74586751c542776325d3a170f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "43170612"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="38f5f-103">Se connecter à PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="38f5f-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="38f5f-104">PowerShell Office 365 vous permet de gérer vos paramètres Office 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="38f5f-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="38f5f-105">La connexion à PowerShell Office 365 est un processus simple dans le cadre duquel vous installez les logiciels requis, puis vous connectez à votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="38f5f-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="38f5f-106">Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Office 365 et administrer les comptes d’utilisateurs, les groupes et les licences :</span><span class="sxs-lookup"><span data-stu-id="38f5f-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="38f5f-107">Azure Active Directory PowerShell pour Graph (les cmdlets **incluent** AzureAD dans leur nom) ;</span><span class="sxs-lookup"><span data-stu-id="38f5f-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="38f5f-108">Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSol** dans leur nom).</span><span class="sxs-lookup"><span data-stu-id="38f5f-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="38f5f-109">Au moment de rédiger cet article, le module Azure Active Directory PowerShell pour Graph ne remplace pas complètement la fonctionnalité des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences.</span><span class="sxs-lookup"><span data-stu-id="38f5f-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="38f5f-110">Dans de nombreux cas, vous devez utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="38f5f-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="38f5f-111">Vous pouvez installer en toute sécurité les deux versions sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38f5f-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="38f5f-112">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="38f5f-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="38f5f-113">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="38f5f-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="38f5f-114">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="38f5f-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="38f5f-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="38f5f-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="38f5f-116">Pour le module Graph d'Azure Active Directory PowerShell, vous devez utiliser PowerShell version 5.1 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="38f5f-116">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="38f5f-117">Vous devez utiliser PowerShell version 5.1 ou ultérieure jusqu’à PowerShell version 6 pour le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f5f-117">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="38f5f-118">Vous ne pouvez pas utiliser la version 7 de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f5f-118">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="38f5f-119">Pour Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 et Windows Server 2008 R2 SP1, téléchargez et installez [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="38f5f-119">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="38f5f-120">Utilisez une version 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="38f5f-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="38f5f-121">Le support de la version 32 bits du Module Microsoft Azure Active Directory pour Windows PowerShell a cessé en octobre 2014.</span><span class="sxs-lookup"><span data-stu-id="38f5f-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="38f5f-122">Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="38f5f-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="38f5f-123">Pour plus d’informations, voir [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="38f5f-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="38f5f-124">Se connecter avec le module PowerShell Azure Active Directory pour Graph</span><span class="sxs-lookup"><span data-stu-id="38f5f-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="38f5f-125">Le nom des cmdlets du module Azure Active Directory PowerShell pour Graph contient la chaîne de caractères **AzureAD**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-125">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="38f5f-126">Vous pouvez installer le module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ou [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span><span class="sxs-lookup"><span data-stu-id="38f5f-126">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="38f5f-127">Dans le cadre des procédures qui requièrent les nouvelles cmdlets dans le module Microsoft Azure Active Directory PowerShell pour Graph, pour installer le module et vous connecter à votre abonnement Office 365, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="38f5f-127">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="38f5f-128">Pour plus d’informations sur le support de différentes versions de Microsoft Windows, voir [Module Microsoft Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="38f5f-128">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="38f5f-129">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="38f5f-129">Step 1: Install required software</span></span>

<span data-ttu-id="38f5f-p107">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="38f5f-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="38f5f-132">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="38f5f-132">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="38f5f-133">Dans la fenêtre de commande **Administrateur : Windows PowerShell**, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="38f5f-133">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="38f5f-134">Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="38f5f-134">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="38f5f-135">Étape 2 : se connecter à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="38f5f-135">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="38f5f-136">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une authentification multifacteur (MFA), exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="38f5f-136">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="38f5f-137">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="38f5f-137">**Office 365 cloud**</span></span> | <span data-ttu-id="38f5f-138">**Commande**</span><span class="sxs-lookup"><span data-stu-id="38f5f-138">**Command**</span></span> |
| <span data-ttu-id="38f5f-139">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="38f5f-139">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="38f5f-140">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="38f5f-140">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="38f5f-141">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="38f5f-141">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="38f5f-142">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="38f5f-142">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="38f5f-143">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-143">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="38f5f-144">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="38f5f-144">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="38f5f-145">Une fois connecté, vous pouvez utiliser les cmdlets du [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="38f5f-145">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="38f5f-146">Se connecter au Module Microsoft Azure Active Directory pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f5f-146">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="38f5f-147">Le nom des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell contient la chaîne de caractères **MSol**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-147">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="38f5f-148">PowerShell version 7 ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="38f5f-148">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="38f5f-149">Pour PowerShell version 7 ou ultérieure, vous devez utiliser le module Azure Active Directory PowerShell pour Graph ou Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f5f-149">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="38f5f-150">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="38f5f-150">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="38f5f-151">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f5f-151">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="38f5f-152">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="38f5f-152">Step 1: Install required software</span></span>

<span data-ttu-id="38f5f-p110">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="38f5f-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="38f5f-155">Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant de connexion Microsoft Online Services pour les professionnels des technologies de l’information RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="38f5f-155">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="38f5f-156">Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="38f5f-156">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="38f5f-157">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="38f5f-157">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="38f5f-158">Exécutez la commande **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-158">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="38f5f-159">Si vous êtes invité à installer le fournisseur NuGet, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="38f5f-159">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="38f5f-160">Si vous êtes invité à installer le module à partir de PSGallery, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="38f5f-160">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="38f5f-161">Étape 2 : se connecter à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="38f5f-161">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="38f5f-162">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une authentification multifacteur (MFA), exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="38f5f-162">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="38f5f-163">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="38f5f-163">**Office 365 cloud**</span></span> | <span data-ttu-id="38f5f-164">**Commande**</span><span class="sxs-lookup"><span data-stu-id="38f5f-164">**Command**</span></span> |
| <span data-ttu-id="38f5f-165">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="38f5f-165">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="38f5f-166">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="38f5f-166">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="38f5f-167">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="38f5f-167">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="38f5f-168">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="38f5f-168">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="38f5f-169">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-169">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="38f5f-170">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="38f5f-170">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="38f5f-171">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="38f5f-171">How do you know this worked?</span></span>

<span data-ttu-id="38f5f-172">Si aucun message d’erreur ne s’affiche, cela signifie que la connexion a été correctement établie.</span><span class="sxs-lookup"><span data-stu-id="38f5f-172">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="38f5f-173">Pour effectuer un test rapide, vous pouvez exécuter une cmdlet Office 365 (par exemple, **Get-MsolUser**) et en examiner les résultats.</span><span class="sxs-lookup"><span data-stu-id="38f5f-173">A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="38f5f-174">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="38f5f-174">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="38f5f-175">**L’inexactitude du mot de passe est un problème courant**.</span><span class="sxs-lookup"><span data-stu-id="38f5f-175">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="38f5f-176">Exécutez à nouveau l’étape 2</span><span class="sxs-lookup"><span data-stu-id="38f5f-176">Run Step 2 again.</span></span> <span data-ttu-id="38f5f-177">en étant attentif aux nom d’utilisateur et mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="38f5f-177">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="38f5f-178">**Le Module Microsoft Azure Active Directory pour Windows PowerShell requiert que la fonctionnalité Microsoft .NET Framework 3.5.* x* soit activée sur votre ordinateur**. Il est probable qu’une version plus récente soit installée sur votre ordinateur (par exemple, 4 ou 4.5.* x*), mais la compatibilité descendante avec des versions antérieures du .NET Framework peut être activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="38f5f-178">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="38f5f-179">Pour plus d’informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="38f5f-179">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="38f5f-180">Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Activer .NET Framework 3.5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="38f5f-180">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="38f5f-181">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="38f5f-181">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="38f5f-182">Pour Windows 10, Windows 8.1 et Windows 8, voir [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10).</span><span class="sxs-lookup"><span data-stu-id="38f5f-182">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="38f5f-183">**Votre version du Module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.**</span><span class="sxs-lookup"><span data-stu-id="38f5f-183">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="38f5f-184">Pour vérifier cela, exécutez la commande suivante dans PowerShell Office 365 ou le Module Microsoft Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="38f5f-184">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="38f5f-185">Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Module Microsoft Azure Active Directory pour Windows PowerShell, puis installez la dernière version à partir du lien fourni à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="38f5f-185">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>

- <span data-ttu-id="38f5f-186">\*\*Si un message d’erreur de connexion s’affiche, voir \*\* [Erreur « Connect-MsolService: Une exception de type a été levée »](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="38f5f-186">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="38f5f-187">**Si vous recevez un message d’erreur « Get-Item : Chemin introuvable », utilisez la commande suivante :**</span><span class="sxs-lookup"><span data-stu-id="38f5f-187">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a><span data-ttu-id="38f5f-188">Voir également</span><span class="sxs-lookup"><span data-stu-id="38f5f-188">See also</span></span>

- [<span data-ttu-id="38f5f-189">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f5f-189">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="38f5f-190">Mise en route d’Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f5f-190">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="38f5f-191">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f5f-191">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
