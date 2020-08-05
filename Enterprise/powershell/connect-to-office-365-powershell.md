---
title: Connexion à Microsoft 365 à l’aide de PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
description: Connectez-vous à votre client Microsoft 365 à l’aide de PowerShell pour Microsoft 365 afin d’effectuer des tâches de Centre d’administration à partir de la ligne de commande.
ms.openlocfilehash: 117d8d983d1baffa1ee5b85b7451c5fd2b0e30e7
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230810"
---
# <a name="connect-to-microsoft-365-with-powershell"></a><span data-ttu-id="8b92b-103">Connexion à Microsoft 365 à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b92b-103">Connect to Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="8b92b-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="8b92b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="8b92b-105">PowerShell pour Microsoft 365 vous permet de gérer vos paramètres Microsoft 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8b92b-105">PowerShell for Microsoft 365 lets you manage your Microsoft 365 settings from the command line.</span></span> <span data-ttu-id="8b92b-106">La connexion à PowerShell est un processus simple dans le cadre duquel vous installez les logiciels requis, puis vous vous connectez au compte Microsoft 365 de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="8b92b-106">Connecting to PowerShell is a simple process where you install the required software and then connect to your Microsoft 365 organization.</span></span> 

<span data-ttu-id="8b92b-107">Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Microsoft 365 et administrer les comptes d’utilisateurs, les groupes et les licences :</span><span class="sxs-lookup"><span data-stu-id="8b92b-107">There are two versions of the PowerShell module that you use to connect to Microsoft 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="8b92b-108">Azure Active Directory PowerShell pour Graph (les cmdlets **incluent** AzureAD dans leur nom) ;</span><span class="sxs-lookup"><span data-stu-id="8b92b-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="8b92b-109">Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSol** dans leur nom).</span><span class="sxs-lookup"><span data-stu-id="8b92b-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="8b92b-110">Au moment de rédiger cet article, le module Azure Active Directory PowerShell pour Graph ne remplace pas complètement la fonctionnalité des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences.</span><span class="sxs-lookup"><span data-stu-id="8b92b-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="8b92b-111">Dans certains cas, vous devez utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="8b92b-111">In some cases, you need to use both versions.</span></span> <span data-ttu-id="8b92b-112">Vous pouvez installer en toute sécurité les deux versions sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8b92b-112">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="8b92b-113">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="8b92b-113">What do you need to know before you begin?</span></span>

<span data-ttu-id="8b92b-114">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b92b-114">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="8b92b-115">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="8b92b-115">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="8b92b-116">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8b92b-116">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b92b-117">Pour le module Graph d'Azure Active Directory PowerShell, vous devez utiliser PowerShell version 5.1 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8b92b-117">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="8b92b-118">Vous devez utiliser PowerShell version 5.1 ou ultérieure jusqu’à PowerShell version 6 pour le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b92b-118">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="8b92b-119">Vous ne pouvez pas utiliser la version 7 de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b92b-119">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="8b92b-120">Pour Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 et Windows Server 2008 R2 SP1, téléchargez et installez [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="8b92b-120">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="8b92b-121">Utilisez une version 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="8b92b-121">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="8b92b-122">Le support de la version 32 bits du Module Microsoft Azure Active Directory pour Windows PowerShell a cessé en octobre 2014.</span><span class="sxs-lookup"><span data-stu-id="8b92b-122">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="8b92b-123">Ces procédures sont destinées aux utilisateurs qui sont membres d’un groupe de rôles d'administrateur Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8b92b-123">These procedures are intended for users who are members of a Microsoft 365 admin role.</span></span> <span data-ttu-id="8b92b-124">Si vous souhaitez en savoir plus, veuillez consulter la page [À propos des rôles d’administrateur](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="8b92b-124">For more information, see [About admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8b92b-125">Se connecter avec le module PowerShell Azure Active Directory pour Graph</span><span class="sxs-lookup"><span data-stu-id="8b92b-125">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8b92b-126">Le nom des cmdlets du module Azure Active Directory PowerShell pour Graph contient la chaîne de caractères **AzureAD**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-126">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="8b92b-127">Vous pouvez installer le module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) ou [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span><span class="sxs-lookup"><span data-stu-id="8b92b-127">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="8b92b-128">Si vous devez utiliser les nouvelles cmdlets dans le module Microsoft Azure Active Directory PowerShell pour Graph, veuillez suivre cette procédure pour installer le module et vous connecter à votre abonnement Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8b92b-128">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="8b92b-129">Pour plus d’informations sur le support de différentes versions de Microsoft Windows, voir [Module Microsoft Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="8b92b-129">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="8b92b-130">Étape 1 : installez les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="8b92b-130">Step 1: Install required software</span></span>

<span data-ttu-id="8b92b-p107">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="8b92b-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="8b92b-133">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="8b92b-133">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="8b92b-134">Dans la fenêtre de commande **Administrateur : Windows PowerShell**, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8b92b-134">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="8b92b-135">Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8b92b-135">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a><span data-ttu-id="8b92b-136">Étape 2 : connectez-vous à Azure AD avec votre abonnement Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8b92b-136">Step 2: Connect to Azure AD for your Microsoft 365 subscription</span></span>

<span data-ttu-id="8b92b-137">Pour vous connecter à Azure AD avec une authentification multifacteur ou les identifiants d’un compte de votre abonnement Microsoft 365, exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="8b92b-137">To connect to Azure AD for your Microsoft 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="8b92b-138">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="8b92b-138">**Office 365 cloud**</span></span> | <span data-ttu-id="8b92b-139">**Commande**</span><span class="sxs-lookup"><span data-stu-id="8b92b-139">**Command**</span></span> |
| <span data-ttu-id="8b92b-140">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="8b92b-140">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="8b92b-141">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="8b92b-141">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="8b92b-142">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="8b92b-142">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="8b92b-143">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="8b92b-143">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="8b92b-144">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Microsoft 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-144">In the **Sign into your account** dialog box, type your Microsoft 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="8b92b-145">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="8b92b-145">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="8b92b-146">Une fois connecté, vous pouvez utiliser les cmdlets du [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="8b92b-146">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8b92b-147">Se connecter au Module Microsoft Azure Active Directory pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b92b-147">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8b92b-148">Le nom des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell contient la chaîne de caractères **MSol**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-148">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="8b92b-149">PowerShell version 7 ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="8b92b-149">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8b92b-150">Pour PowerShell version 7 ou ultérieure, vous devez utiliser le module Azure Active Directory PowerShell pour Graph ou Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b92b-150">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="8b92b-151">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="8b92b-151">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8b92b-152">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b92b-152">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="8b92b-153">Étape 1 : installez les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="8b92b-153">Step 1: Install required software</span></span>

<span data-ttu-id="8b92b-p110">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="8b92b-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="8b92b-156">Si vous n’exécutez pas Windows 10, installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant de connexion Microsoft Online Services pour les professionnels des technologies de l'information RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="8b92b-156">If you are not running Windows 10, install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="8b92b-157">Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b92b-157">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="8b92b-158">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="8b92b-158">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="8b92b-159">Exécutez la commande **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-159">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="8b92b-160">Si vous êtes invité à installer le fournisseur NuGet, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8b92b-160">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="8b92b-161">Si vous êtes invité à installer le module à partir de PSGallery, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8b92b-161">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a><span data-ttu-id="8b92b-162">Étape 2 : connectez-vous à Azure AD avec votre abonnement Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8b92b-162">Step 2: Connect to Azure AD for your Microsoft 365 subscription</span></span>

<span data-ttu-id="8b92b-163">Pour vous connecter à Azure AD avec une authentification multifacteur ou les identifiants d’un compte de votre abonnement Microsoft 365, exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="8b92b-163">To connect to Azure AD for your Microsoft 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="8b92b-164">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="8b92b-164">**Office 365 cloud**</span></span> | <span data-ttu-id="8b92b-165">**Commande**</span><span class="sxs-lookup"><span data-stu-id="8b92b-165">**Command**</span></span> |
| <span data-ttu-id="8b92b-166">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="8b92b-166">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="8b92b-167">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="8b92b-167">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="8b92b-168">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="8b92b-168">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="8b92b-169">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="8b92b-169">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="8b92b-170">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Microsoft 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-170">In the **Sign into your account** dialog box, type your Microsoft 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="8b92b-171">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue additionnelles pour fournir des informations d’authentification supplémentaires (code de vérification, etc.).</span><span class="sxs-lookup"><span data-stu-id="8b92b-171">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="8b92b-172">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="8b92b-172">How do you know this worked?</span></span>

<span data-ttu-id="8b92b-173">Si vous ne recevez aucune erreur, la connexion est établie.</span><span class="sxs-lookup"><span data-stu-id="8b92b-173">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="8b92b-174">Pour effectuer un test rapide, vous pouvez exécuter une cmdlet Microsoft 365 (par exemple, **Get-MsolUser**) et en examiner les résultats.</span><span class="sxs-lookup"><span data-stu-id="8b92b-174">A quick test is to run a Microsoft 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="8b92b-175">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b92b-175">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="8b92b-176">**L’inexactitude du mot de passe est un problème courant**.</span><span class="sxs-lookup"><span data-stu-id="8b92b-176">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="8b92b-177">Exécutez à nouveau l’étape 2</span><span class="sxs-lookup"><span data-stu-id="8b92b-177">Run Step 2 again.</span></span> <span data-ttu-id="8b92b-178">en étant attentif aux nom d’utilisateur et mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="8b92b-178">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="8b92b-179">**Le Module Microsoft Azure Active Directory pour Windows PowerShell requiert que la fonctionnalité Microsoft .NET Framework 3.5.* x* soit activée sur votre ordinateur**. Il est probable qu’une version plus récente soit installée sur votre ordinateur (par exemple, 4 ou 4.5.* x*), mais la compatibilité descendante avec des versions antérieures du .NET Framework peut être activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="8b92b-179">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="8b92b-180">Pour plus d’informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b92b-180">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="8b92b-181">Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Activer .NET Framework 3.5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="8b92b-181">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="8b92b-182">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="8b92b-182">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="8b92b-183">Pour Windows 10, Windows 8.1 et Windows 8, voir [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10).</span><span class="sxs-lookup"><span data-stu-id="8b92b-183">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="8b92b-184">**Votre version du Module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.**</span><span class="sxs-lookup"><span data-stu-id="8b92b-184">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="8b92b-185">Pour vérifier cela, exécutez la commande suivante dans PowerShell pour Microsoft 365 ou le Module Microsoft Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8b92b-185">To check, run the following command in PowerShell for Microsoft 365 or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="8b92b-186">Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Module Microsoft Azure Active Directory pour Windows PowerShell, puis installez-le en suivant les instructions de l’étape 1, plus haut.</span><span class="sxs-lookup"><span data-stu-id="8b92b-186">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install from Step 1 above.</span></span>

- <span data-ttu-id="8b92b-187">\*\*Si un message d’erreur de connexion s’affiche, voir \*\* [Erreur « Connect-MsolService: Une exception de type a été levée »](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="8b92b-187">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="8b92b-188">**Si vous recevez un message d’erreur « Get-Item : Chemin introuvable », utilisez la commande suivante :**</span><span class="sxs-lookup"><span data-stu-id="8b92b-188">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a><span data-ttu-id="8b92b-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b92b-189">See also</span></span>

- [<span data-ttu-id="8b92b-190">Gestion de Microsoft 365 à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b92b-190">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="8b92b-191">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8b92b-191">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="8b92b-192">Connexion à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b92b-192">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
