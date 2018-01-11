---
title: "Se connecter à Office 365 PowerShell"
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
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Résumé : Connexion à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches de centre d’administration Office 365 à partir de la ligne de commande."
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="0f7c3-103">Se connecter à Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7c3-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="0f7c3-104">**Résumé :** Se connecter à votre organisation d’Office 365 à l’aide d’Office 365 PowerShell pour effectuer les tâches d’administration Office 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="0f7c3-p101">Office 365 PowerShell vous permet pour gérer vos paramètres Office 365 à partir de la ligne de commande. Se connecter à Office 365 PowerShell est un processus en trois étapes simple où vous installez les logiciels requis, exécuter les logiciels requis et puis connectez à votre organisation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="0f7c3-107">Notez que ces instructions de connexion sont les mêmes que ceux de la rubrique [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="0f7c3-p102">**Nouveau PowerShell ?** Voir une [Présentation vidéo de PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="0f7c3-110">Ce qu’il faut savoir avant de commencer ?</span><span class="sxs-lookup"><span data-stu-id="0f7c3-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="0f7c3-111">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="0f7c3-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="0f7c3-112">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="0f7c3-113">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="0f7c3-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="0f7c3-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="0f7c3-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="0f7c3-p103">Utilisez une version 64 bits de Windows. Prise en charge de la version 32 bits du Microsoft Azure Active Directory Module pour Windows PowerShell a été interrompu en octobre de 2014.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="0f7c3-p104">L’Office 365 fonctionne ou l’école de compte que vous l’utilisation de ces procédures doit pour être membre d’un rôle d’administrateur Office 365. Pour plus d’informations, consultez [rôles d’administrateur à propos d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="0f7c3-119">Étape 1 : Installer les logiciels requis</span><span class="sxs-lookup"><span data-stu-id="0f7c3-119">Step 1: Install required software</span></span>

<span data-ttu-id="0f7c3-p105">Ces étapes sont nécessaires une seule fois sur votre ordinateur, pas chaque fois que vous vous connectez. Toutefois, vous devrez probablement installer régulièrement des versions plus récentes du logiciel.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="0f7c3-122">Installez la version 64 bits de l’Assistant de connexion Microsoft Online Services : [Microsoft Online Services - Assistant de connexion pour la version RTW de professionnels de l’informatique](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="0f7c3-123">Installez la version 64 bits de la Microsoft Azure Active Directory Module pour Windows PowerShell avec ces étapes :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="0f7c3-124">Ouvrez la page web de [Connexion à Active Directory Azure](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) .</span><span class="sxs-lookup"><span data-stu-id="0f7c3-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="0f7c3-125">Dans **les fichiers de téléchargement** en bas de la page, cliquez sur **Télécharger** le fichier **AdministrationConfig-V1.1.166.0-GA.msi** et installez-le.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="0f7c3-126">Étape 2 : Ouvrir le module Windows Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="0f7c3-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="0f7c3-127">Recherchez et ouvrez le Microsoft Azure Active Directory Module pour Windows PowerShell en utilisant l’une des méthodes suivantes selon votre version de Windows :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="0f7c3-128">**Menu Démarrer** À partir du bureau, cliquez sur **Démarrer**et tapez Azure.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="0f7c3-129">**Menu Démarrer de N°** ForAzure de recherche à l’aide d’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="0f7c3-130">Sur l’écran de démarrage, cliquez sur une zone vide et tapez Azure.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="0f7c3-p106">Sur le bureau ou l’écran de démarrage, appuyez sur la touche Windows + touche Q. Dans l’icône de recherche, tapez Azure.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="0f7c3-p107">Sur le bureau ou l’écran de démarrage, déplacez votre curseur dans le coin supérieur droit, ou faites défiler le bord droit de l’écran pour afficher les icônes de gauche. Cliquez sur l’icône de recherche et tapez **Azure**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="0f7c3-135">Dans les résultats, cliquez sur **Microsoft Azure Active Directory Module pour Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="0f7c3-136">Étape 3 : Se connecter à votre abonnement à Office 365</span><span class="sxs-lookup"><span data-stu-id="0f7c3-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="0f7c3-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="0f7c3-137"></span></span>

<span data-ttu-id="0f7c3-138">Se connecter avec seulement un *nom de compte et de mot de passe* :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="0f7c3-139">Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="0f7c3-140">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="0f7c3-141">Se connecter avec *l’authentification par plusieurs facteur (AMF)* :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="0f7c3-142">Dans la fenêtre de commande **Microsoft Azure Active Directory Module pour Windows PowerShell** , exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="0f7c3-143">Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="0f7c3-144">Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="0f7c3-145">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="0f7c3-145">How do you know this worked?</span></span>
<span data-ttu-id="0f7c3-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="0f7c3-146"></span></span>

<span data-ttu-id="0f7c3-p108">Si vous ne recevez pas d’erreurs, vous est connecté correctement. Un test rapide est d’exécuter une applet de commande d’Office 365, par exemple, **Get-MsolUser** et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="0f7c3-149">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="0f7c3-p109">**Un problème courant est un mot de passe incorrect**. Réexécutez l’étape 3. et faites attention pour le nom d’utilisateur et le mot de passe que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="0f7c3-p110">**Le Microsoft Azure Active Directory Module pour Windows PowerShell requiert que le Microsoft.NET Framework 3.5. fonctionnalité de _x_ est activée sur votre ordinateur**. Il est probable que votre ordinateur dispose d’une version plus récente est installée (par exemple, 4 ou 4.5. _x_), mais en arrière la compatibilité avec les versions antérieures du.NET Framework peut être activée ou désactivée. Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="0f7c3-157">Pour Windows Server 2012 ou de Windows Server 2012 R2, voir [Activer le.NET Framework 3.5 à l’aide de l’ajout de rôles et fonctionnalités Assistant](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="0f7c3-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="0f7c3-158">Pour Windows 8 ou Windows 8.1, consultez [installer le 3.5 de.NET Framework sur Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="0f7c3-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="0f7c3-159">Pour Windows 7 ou Windows Server 2008 R2, consultez [Impossible d’ouvrir le Module Azure pour annuaire Active pour Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="0f7c3-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="0f7c3-p111">**Votre version de la Microsoft Azure Active Directory Module pour Windows PowerShell est peut-être périmée.** Pour vérifier, exécutez la commande suivante dans Office 365 PowerShell ou le Microsoft Azure Active Directory Module pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="0f7c3-162">Si le numéro de version retourné est inférieur à la valeur 1.0.8070.2, désinstallez le Microsoft Azure Active Directory Module pour Windows PowerShell et installer la dernière version à partir du lien à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="0f7c3-163">**Si vous recevez une erreur de connexion, consultez la rubrique suivante :** [« Connect-MsolService : la levée de l’Exception de type » erreur](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="0f7c3-164">Se connecter au module Azure Active Directory V2 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7c3-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="0f7c3-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="0f7c3-165"></span></span>

<span data-ttu-id="0f7c3-166">Pour les procédures nécessitant les nouvelles applets de commande du [module PowerShell de Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), suivez cette procédure pour installer le module et le connecter à votre abonnement à Office 365 :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="0f7c3-167">Ouvrez une invite de commande Windows PowerShell avec élévation de privilèges (d’exécution Windows PowerShell en tant qu’administrateur).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="0f7c3-168">Dans la **administrateur : Windows PowerShell** fenêtre de commande, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="0f7c3-169">Si vous êtes invité à propos de l’installation d’un module à partir d’un référentiel non approuvé, tapez **o** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="0f7c3-170">Une fois l’installation du nouveau module terminée, utilisez ces commandes pour vous connecter à votre abonnement Office 365 :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="0f7c3-171">Avec un *nom de compte et de mot de passe* :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="0f7c3-172">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="0f7c3-173">Avec une *authentification à facteurs multiples (AMF)* :</span><span class="sxs-lookup"><span data-stu-id="0f7c3-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="0f7c3-174">Dans la boîte de dialogue **Azure Active Directory PowerShell** , tapez votre travail d’Office 365 ou le nom de l’école compte utilisateur et le mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="0f7c3-175">Suivez les instructions dans la boîte de dialogue **Azure Active Directory PowerShell** pour fournir des informations d’authentification supplémentaires, comme un code de vérification, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="0f7c3-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="0f7c3-176">Une fois connecté, vous pouvez utiliser les nouvelles applets de commande du [module PowerShell de Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="0f7c3-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0f7c3-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f7c3-177">See also</span></span>

#### 

[<span data-ttu-id="0f7c3-178">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7c3-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0f7c3-179">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="0f7c3-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="0f7c3-180">Connexion à tous les services Office 365 à l'aide d'une seule fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7c3-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="0f7c3-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="0f7c3-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="0f7c3-182">MsolService de connexion</span><span class="sxs-lookup"><span data-stu-id="0f7c3-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

