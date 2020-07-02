---
title: Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Résumé : Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l’aide de la valeur DelegatedOrg.'
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997370"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="dd544-103">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="dd544-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd544-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="dd544-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="dd544-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="dd544-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="dd544-106">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="dd544-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="dd544-107">Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="dd544-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="dd544-108">Ils regroupent les abonnements dans leurs offres de services pour les clients.</span><span class="sxs-lookup"><span data-stu-id="dd544-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="dd544-109">Ils possèdent un client qui bénéficie automatiquement des autorisations d’administration pour le compte de (administrateur) pour leurs clients Microsoft 365, afin qu’ils puissent administrer et rendre compte de tous leurs locations de clients.</span><span class="sxs-lookup"><span data-stu-id="dd544-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="dd544-110">Les partenaires DAP peuvent utiliser Exchange Online PowerShell pour gérer les paramètres Exchange Online du client et obtenir des rapports Microsoft 365 à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dd544-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="dd544-111">Vous utilisez Windows PowerShell sur votre ordinateur local pour créer une session PowerShell distante vers Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="dd544-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="dd544-112">Il s’agit d’un processus simple en trois étapes dans lequel vous entrez vos informations d’identification, fournissez les paramètres de connexion requis, puis importez les applets de commande Exchange Online dans votre session Windows PowerShell locale afin de pouvoir les utiliser.</span><span class="sxs-lookup"><span data-stu-id="dd544-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="dd544-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd544-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="dd544-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="dd544-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="dd544-115">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="dd544-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="dd544-116">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="dd544-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="dd544-117">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd544-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="dd544-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="dd544-118">Windows 10</span></span>

  - <span data-ttu-id="dd544-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="dd544-119">Windows 8.1</span></span>

  - <span data-ttu-id="dd544-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="dd544-120">Windows Server 2016</span></span>

  - <span data-ttu-id="dd544-121">Windows Server 2012 ou Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dd544-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="dd544-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="dd544-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="dd544-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="dd544-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="dd544-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="dd544-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="dd544-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="dd544-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="dd544-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="dd544-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="dd544-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="dd544-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="dd544-128">Pour exiger que tous les scripts PowerShell téléchargés depuis Internet soient signés par un éditeur approuvé, exécutez la commande suivante dans une fenêtre Windows PowerShell avec élévation de privilèges (c’est-à-dire une fenêtre Windows PowerShell ouverte en sélectionnant **Exécuter en tant qu’administrateur**) :</span><span class="sxs-lookup"><span data-stu-id="dd544-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="dd544-129">Vous devez configurer ce paramètre une fois seulement sur votre ordinateur, pas à chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="dd544-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="dd544-130">Pour des informations sur les raccourcis clavier applicables aux procédures de cette rubrique, consultez la rubrique [Raccourcis clavier dans le Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="dd544-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="dd544-131">Connexion à Exchange Online pour les organisations clientes</span><span class="sxs-lookup"><span data-stu-id="dd544-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="dd544-132">Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="dd544-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="dd544-133">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez vos nom d’utilisateur et mot de passe d’administrateur DAP, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dd544-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="dd544-134">Remplacez _\<customer tenant domain name\>_ par le nom du domaine client auquel vous voulez vous connecter, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="dd544-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="dd544-135">Dans cette commande, l'étape clé consiste à spécifier le client auquel accéder pour les informations de création de rapports.</span><span class="sxs-lookup"><span data-stu-id="dd544-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="dd544-136">Pour ce faire, utilisez le paramètre _ConnectionUri_ , dans lequel vous indiquez le nom de domaine complet du nom de domaine initial comme valeur de `?DelegatedOrg=` .</span><span class="sxs-lookup"><span data-stu-id="dd544-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="dd544-137">Cette valeur indique le point de terminaison Exchange Online PowerShell correct auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="dd544-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="dd544-138">Remote PowerShell doit se connecter à Microsoft 365 Reporting dans le contexte d’un client spécifique chaque fois qu’un rapport est exécuté.</span><span class="sxs-lookup"><span data-stu-id="dd544-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="dd544-139">Une fois que vous vous êtes connecté à Exchange Online PowerShell, toutes les commandes suivantes sont exécutées dans le contexte du client, ce qui vous permet d’accéder à tous les rapports disponibles pour le client.</span><span class="sxs-lookup"><span data-stu-id="dd544-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="dd544-140">Exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="dd544-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="dd544-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="dd544-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="dd544-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="dd544-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="dd544-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="dd544-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="dd544-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="dd544-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="dd544-145">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="dd544-145">How do you know this worked?</span></span>

<span data-ttu-id="dd544-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="dd544-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="dd544-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="dd544-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="dd544-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="dd544-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="dd544-149">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd544-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="dd544-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="dd544-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="dd544-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="dd544-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="dd544-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd544-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="dd544-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="dd544-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="dd544-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="dd544-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="dd544-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="dd544-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="dd544-156">Appel de la cmdlet directement avec la commande Invoke</span><span class="sxs-lookup"><span data-stu-id="dd544-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="dd544-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dd544-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="dd544-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="dd544-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="dd544-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="dd544-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="dd544-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="dd544-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="dd544-161">Plus de cmdlets de création de rapports</span><span class="sxs-lookup"><span data-stu-id="dd544-161">More reporting cmdlets</span></span>

<span data-ttu-id="dd544-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dd544-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="dd544-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="dd544-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="dd544-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="dd544-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="dd544-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd544-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="dd544-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd544-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="dd544-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd544-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="dd544-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="dd544-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

