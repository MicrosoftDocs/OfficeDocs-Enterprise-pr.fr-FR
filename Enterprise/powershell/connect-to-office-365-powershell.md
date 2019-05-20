---
title: Se connecter à PowerShell Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Résumé : vous connecter à votre organisation Office 365 à l’aide de PowerShell Office 365 pour effectuer des tâches du centre d’administration à partir de la ligne de commande.'
ms.openlocfilehash: aea7cb638cb866374af6b33d6d1848a7cb6d304c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069090"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="941d5-103">Se connecter à PowerShell Office 365</span><span class="sxs-lookup"><span data-stu-id="941d5-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="941d5-104">**Résumé:** Connectez-vous à votre organisation Office 365 à l’aide de PowerShell Office 365 pour effectuer les tâches d’administration à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="941d5-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="941d5-105">PowerShell Office 365 vous permet de gérer vos paramètres Office 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="941d5-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="941d5-106">La connexion à PowerShell Office 365 est un processus simple dans le cadre duquel vous installez les logiciels requis, puis vous connectez à votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="941d5-106">Connecting to  O365_PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your O365_W14_2nd organization.</span></span> 

<span data-ttu-id="941d5-107">Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Office 365 et administrer les comptes d’utilisateurs, les groupes et les licences :</span><span class="sxs-lookup"><span data-stu-id="941d5-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="941d5-108">Azure Active Directory PowerShell pour Graph (les cmdlets **incluent** AzureAD dans leur nom) ;</span><span class="sxs-lookup"><span data-stu-id="941d5-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="941d5-109">Module Microsoft Azure Active Directory pour Windows PowerShell (les cmdlets incluent **MSol** dans leur nom).</span><span class="sxs-lookup"><span data-stu-id="941d5-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="941d5-110">Au moment de rédiger cet article, le module Azure Active Directory PowerShell pour Graph ne remplace pas complètement la fonctionnalité des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences.</span><span class="sxs-lookup"><span data-stu-id="941d5-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="941d5-111">Dans de nombreux cas, vous devez utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="941d5-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="941d5-112">Vous pouvez installer en toute sécurité les deux versions sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="941d5-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="941d5-113">**Vous débutez avec PowerShell ?**</span><span class="sxs-lookup"><span data-stu-id="941d5-113">**New to PowerShell?**</span></span> <span data-ttu-id="941d5-114">Regardez la [vidéo de présentation de PowerShell](https://support.office.com/fr-FR/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), accessible via LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="941d5-114">See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="941d5-115">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="941d5-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="941d5-116">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="941d5-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="941d5-117">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="941d5-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="941d5-118">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="941d5-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="941d5-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="941d5-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="941d5-120">Utilisez une version 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="941d5-120">Use a 64-bit version of Windows.</span></span> <span data-ttu-id="941d5-121">Le support de la version 32 bits du Module Microsoft Azure Active Directory pour Windows PowerShell a cessé en octobre 2014.</span><span class="sxs-lookup"><span data-stu-id="941d5-121">Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="941d5-122">Ces procédures sont destinées aux utilisateurs qui sont membres d’un rôle d’administrateur Office 365.</span><span class="sxs-lookup"><span data-stu-id="941d5-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="941d5-123">Pour plus d’informations, voir [À propos des rôles d’administrateur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="941d5-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="941d5-124">Se connecter avec le module PowerShell Azure Active Directory pour Graph</span><span class="sxs-lookup"><span data-stu-id="941d5-124">Next, you Connect with the Azure Active Directory PowerShell for Graph module .</span></span>

<span data-ttu-id="941d5-125">Le nom des cmdlets du module [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) contient la chaîne de caractères **AzureAD**.</span><span class="sxs-lookup"><span data-stu-id="941d5-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="941d5-126">Dans le cadre des procédures qui requièrent les nouvelles cmdlets dans le module Microsoft Azure Active Directory PowerShell pour Graph, pour installer le module et vous connecter à votre abonnement Office 365, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="941d5-126">For procedures that require the new cmdlets in the Azure Active Directory V2 PowerShell modulehttps://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory, use these steps to install the module and connect to your Office 365 subscription:</span></span>

>[!Note]
><span data-ttu-id="941d5-127">Pour plus d’informations sur le support de différentes versions de Microsoft Windows, voir [Module Microsoft Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="941d5-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="941d5-128">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="941d5-128">Step 1: Install required software</span></span>

<span data-ttu-id="941d5-p106">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="941d5-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="941d5-131">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="941d5-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="941d5-132">Dans la fenêtre de commande **Administrateur : Windows PowerShell**, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="941d5-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="941d5-133">Si vous êtes invité à installer un module à partir d’un référentiel non approuvé, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="941d5-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="941d5-134">Étape 2 : se connecter à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="941d5-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="941d5-135">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une *authentification multifacteur (MFA)*, exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="941d5-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="941d5-136">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="941d5-136">**Office 365 cloud**</span></span> | <span data-ttu-id="941d5-137">**Commande**</span><span class="sxs-lookup"><span data-stu-id="941d5-137">**Command**</span></span> |
| <span data-ttu-id="941d5-138">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="941d5-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="941d5-139">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="941d5-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="941d5-140">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="941d5-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="941d5-141">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="941d5-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="941d5-142">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="941d5-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="941d5-143">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="941d5-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="941d5-144">Une fois connecté, vous pouvez utiliser les nouvelles cmdlets du [module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="941d5-144">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell modulehttps://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="941d5-145">Se connecter au Module Microsoft Azure Active Directory pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="941d5-145">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="941d5-146">Le nom des cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell contient la chaîne de caractères **MSol**.</span><span class="sxs-lookup"><span data-stu-id="941d5-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="941d5-147">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="941d5-147">Step 1: Install required software</span></span>

<span data-ttu-id="941d5-p107">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="941d5-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="941d5-150">Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Assistant de connexion Microsoft Online Services pour les professionnels des technologies de l’information RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="941d5-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTWhttps://go.microsoft.com/fwlink/p/?LinkId=286152](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="941d5-151">Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="941d5-151">Install the Azure Active Directory Module for Windows PowerShell:</span></span>
    
  - <span data-ttu-id="941d5-152">Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="941d5-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="941d5-153">Exécutez la commande **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="941d5-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="941d5-154">Si vous êtes invité à installer le fournisseur NuGet, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="941d5-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="941d5-155">Si vous êtes invité à installer le module à partir de PSGallery, tapez **O**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="941d5-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="941d5-156">Étape 2 : se connecter à Azure AD pour votre abonnement Office 365</span><span class="sxs-lookup"><span data-stu-id="941d5-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="941d5-157">Pour vous connecter à Azure AD pour votre abonnement Office 365 avec un nom et un mot de passe de compte ou avec une *authentification multifacteur (MFA)*, exécutez l’une des commandes suivantes à partir d’une invite de commandes Windows PowerShell (ne nécessite pas d’élévation de privilèges).</span><span class="sxs-lookup"><span data-stu-id="941d5-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="941d5-158">**Cloud Office 365**</span><span class="sxs-lookup"><span data-stu-id="941d5-158">**Office 365 cloud**</span></span> | <span data-ttu-id="941d5-159">**Commande**</span><span class="sxs-lookup"><span data-stu-id="941d5-159">**Command**</span></span> |
| <span data-ttu-id="941d5-160">Office 365 dans le monde (+GCC)</span><span class="sxs-lookup"><span data-stu-id="941d5-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="941d5-161">Office 365 géré par 21 ViaNet</span><span class="sxs-lookup"><span data-stu-id="941d5-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="941d5-162">Office 365 Allemagne</span><span class="sxs-lookup"><span data-stu-id="941d5-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="941d5-163">Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="941d5-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="941d5-164">Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Office 365, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="941d5-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="941d5-165">Si vous utilisez une authentification multifacteur, suivez les instructions des boîtes de dialogue suivantes pour fournir des informations d’authentification supplémentaires telles qu’un code de vérification.</span><span class="sxs-lookup"><span data-stu-id="941d5-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="941d5-166">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="941d5-166">How do you know this worked?</span></span>

<span data-ttu-id="941d5-167">Si aucun message d’erreur ne s’affiche, cela signifie que la connexion a été correctement établie.</span><span class="sxs-lookup"><span data-stu-id="941d5-167">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="941d5-168">Pour effectuer un test rapide, vous pouvez exécuter une cmdlet Office 365 (par exemple, **Get-MsolUser**) et en examiner les résultats.</span><span class="sxs-lookup"><span data-stu-id="941d5-168">A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="941d5-169">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="941d5-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="941d5-170">**L’inexactitude du mot de passe est un problème courant**.</span><span class="sxs-lookup"><span data-stu-id="941d5-170">A common problem is an incorrect password.</span></span> <span data-ttu-id="941d5-171">Exécutez à nouveau l’étape 2</span><span class="sxs-lookup"><span data-stu-id="941d5-171">Run Step 2 again.</span></span> <span data-ttu-id="941d5-172">en étant attentif aux nom d’utilisateur et mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="941d5-172">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="941d5-173">**Le Module Microsoft Azure Active Directory pour Windows PowerShell requiert que la fonctionnalité Microsoft .NET Framework 3.5.* x* soit activée sur votre ordinateur**. Il est probable qu’une version plus récente soit installée sur votre ordinateur (par exemple, 4 ou 4.5.* x*), mais la compatibilité descendante avec des versions antérieures du .NET Framework peut être activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="941d5-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="941d5-174">Pour plus d’informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="941d5-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="941d5-175">Pour Windows Server 2012 ou Windows Server 2012 R2, voir [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368) (Activer .NET Framework 3.5 à l’aide de l’Assistant Ajout de rôles et de fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="941d5-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="941d5-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="941d5-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="941d5-177">Pour Windows 10, Windows 8.1 et Windows 8, voir [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](https://docs.microsoft.com/fr-FR/dotnet/framework/install/dotnet-35-windows-10).</span><span class="sxs-lookup"><span data-stu-id="941d5-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="941d5-178">**Votre version du Module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.**</span><span class="sxs-lookup"><span data-stu-id="941d5-178">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="941d5-179">Pour vérifier cela, exécutez la commande suivante dans PowerShell Office 365 ou le Module Microsoft Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="941d5-179">To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="941d5-180">Si le numéro de version renvoyé est inférieur à la valeur 1.0.8070.2, désinstallez le Module Microsoft Azure Active Directory pour Windows PowerShell, puis installez la dernière version à partir du lien fourni à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="941d5-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Azure_AD_Module, and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="941d5-181">\*\*Si un message d’erreur de connexion s’affiche, voir \*\* [Erreur « Connect-MsolService: Une exception de type a été levée »](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="941d5-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" errorhttps://go.microsoft.com/fwlink/p/?LinkId=532377](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="941d5-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="941d5-182">See also</span></span>

- [<span data-ttu-id="941d5-183">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="941d5-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="941d5-184">Mise en route d’Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="941d5-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="941d5-185">Connexion à tous les services Office 365 à l’aide d’une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="941d5-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="941d5-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="941d5-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="941d5-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="941d5-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

