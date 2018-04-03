---
title: Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "Résumé : Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l'aide du paramètre DelegatedOrg."
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="5df77-103">Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="5df77-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="5df77-104">**Résumé :** Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l'aide du paramètre _DelegatedOrg_.</span><span class="sxs-lookup"><span data-stu-id="5df77-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="5df77-p101">Windows PowerShell distant vous permet de gérer vos paramètres Exchange Online à partir de la ligne de commande. Vous pouvez utiliser Windows PowerShell sur votre ordinateur local pour créer une session distante vers Exchange Online. Il s'agit d'un processus simple en trois étapes, dans lequel vous entrez vos informations d'identification Exchange Online, vous indiquez les paramètres de connexion requis, puis vous importez les cmdlets Exchange Online dans votre session Windows PowerShell locale afin de pouvoir les utiliser.</span><span class="sxs-lookup"><span data-stu-id="5df77-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="5df77-108">Ce qu’il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="5df77-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="5df77-109">Durée d’exécution estimée : 5 minutes</span><span class="sxs-lookup"><span data-stu-id="5df77-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="5df77-110">Vous pouvez utiliser les versions de Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df77-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="5df77-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5df77-111">Windows 10</span></span>
    
  - <span data-ttu-id="5df77-112">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="5df77-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="5df77-113">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5df77-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="5df77-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="5df77-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="5df77-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="5df77-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="5df77-p102">\* Installez .NET Framework 4.5.1 ou .NET Framework 4.5, puis Windows Management Framework 4.0 ou Windows Management Framework 3.0. Pour en savoir plus, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df77-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="5df77-118">Installation de NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5df77-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="5df77-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="5df77-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="5df77-120">Pour des informations sur les raccourcis clavier applicables aux procédures de cette rubrique, consultez la rubrique [Raccourcis clavier dans le Centre d'administration Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="5df77-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="5df77-p103">Cette procédure est destinée uniquement aux partenaires avec autorisation d'accès délégué. Si vous n'êtes pas un partenaire avec autorisation d'accès délégué, n'utilisez pas cette procédure.</span><span class="sxs-lookup"><span data-stu-id="5df77-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="5df77-p104">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements dans leurs offres de services pour les clients. Ils possèdent une location partenaire qui dispose automatiquement des autorisations Administrer au nom de (AOBO) pour leurs Office 365locations clientes, afin de pouvoir administrer et créer des rapports sur toutes leurs locations clientes.</span><span class="sxs-lookup"><span data-stu-id="5df77-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="5df77-127">Vous connecter à Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5df77-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="5df77-128">Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="5df77-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="5df77-129">Dans la boîte de dialogue **Demande d'informations d'identification Windows PowerShell**, saisissez vos nom d'utilisateur et mot de passe d'administrateur DAP, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5df77-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="5df77-130">Exécutez la commande suivante en remplaçant  _<customer tenant domain name>_ par le nom du domaine client auquel vous voulez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="5df77-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="5df77-p105">Dans cette commande, l'étape clé consiste à spécifier le client auquel accéder pour les informations de création de rapports. Pour ce faire, vous fournissez le nom de domaine complet du nom de domaine initial dans le paramètre  _ConnectionURI_, en tant que valeur du paramètre  _DelegatedOrg_. Cela indique à Windows PowerShell distant pour Exchange Online PowerShell Windows PowerShell distant le point de terminaison auquel se connecter. Windows PowerShell distant doit se connecter aux rapports Office 365 dans le contexte d'un client spécifique chaque fois qu'un rapport est exécuté. Une fois que ce client est spécifié, toutes les commandes suivantes sont exécutées dans le contexte de ce client. Cela permet au partenaire d'accéder à tous les rapports disponibles pour ce client.</span><span class="sxs-lookup"><span data-stu-id="5df77-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="5df77-137">Exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="5df77-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="5df77-p106">Trois sessions simultanées peuvent être exécutées sous un seul compte au maximum. N'oubliez pas de déconnecter la session Windows PowerShell distante dès que vous avez terminé. Si vous fermez la fenêtre Windows PowerShell sans déconnecter la session, vous risquez d'épuiser toutes les sessions Windows PowerShell distantes à votre disposition et vous devrez attendre que les sessions expirent. Pour déconnecter la session Windows PowerShell distante, exécutez la commande suivante. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="5df77-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="5df77-142">Comment savoir si cela a fonctionné ?</span><span class="sxs-lookup"><span data-stu-id="5df77-142">How do you know this worked?</span></span>

<span data-ttu-id="5df77-p107">Après l'étape 3, les cmdlets Exchange Online sont importées dans votre session Windows PowerShell locale comme indiqué par une barre de progression. Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter une cmdlet Exchange Online (par exemple, **Get-Mailbox** ) et à consulter les résultats.</span><span class="sxs-lookup"><span data-stu-id="5df77-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="5df77-146">Si vous recevez des erreurs, vérifiez les conditions requises suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df77-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="5df77-p108">Un mot de passe incorrect est un problème courant. Exécutez à nouveau les trois étapes et portez une attention particulière au nom d’utilisateur et au mot de passe que vous entrez à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="5df77-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="5df77-149">Pour éviter les attaques par déni de service, vous ne pouvez ouvrir que trois sessions Windows PowerShell distantes vers votre organisation Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5df77-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="5df77-p109">Windows PowerShell doit être configuré pour l'exécution de scripts. Vous devez configurer ce paramètre une fois seulement sur votre ordinateur, pas à chaque connexion. Pour activer l'exécution de scripts signés dans Windows PowerShell, exécutez la commande suivante dans une fenêtre Windows PowerShell élevée (fenêtre Windows PowerShell ouverte en sélectionnant **Exécuter en tant qu'administrateur**).</span><span class="sxs-lookup"><span data-stu-id="5df77-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="5df77-p110">Le compte que vous utilisez pour vous connecter à Exchange Online doit être activé pour Windows PowerShell distant. Pour plus d'informations, voir [Gérer l'accès à Remote PowerShell dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="5df77-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="5df77-p111">Le trafic du port TCP 80 doit être ouvert entre votre ordinateur local et Exchange Online. Il est probablement ouvert, mais vous devez y penser si votre organisation a une stratégie restrictive d'accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="5df77-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="5df77-157">Appel de la cmdlet directement avec la commande Invoke</span><span class="sxs-lookup"><span data-stu-id="5df77-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="5df77-p112">L'importation d'une session Windows PowerShell distante peut être un processus long, car toutes les cmdlets Exchange Online sont importées. Cela peut représenter un problème dans le cadre du traitement par lots, par exemple, lorsque vous exécutez des rapports ou effectuez des modifications en bloc pour différents clients. En guise d'alternative à l'utilisation d' **Import-PSSession**, vous pouvez appeler des cmdlets que vous voulez utiliser directement avec **Invoke-Command**. Par exemple, pour appeler la cmdlet **get-mailbox**, remplacez la syntaxe suivante par `Import-PSSession $Session`.</span><span class="sxs-lookup"><span data-stu-id="5df77-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="5df77-162">Plus de cmdlets de création de rapports</span><span class="sxs-lookup"><span data-stu-id="5df77-162">More reporting cmdlets</span></span>

<span data-ttu-id="5df77-p113">Les cmdlets que vous utilisez dans cette rubrique sont des cmdlets Windows PowerShell. Pour plus d'informations à propos de ces cmdlets, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df77-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="5df77-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="5df77-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="5df77-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5df77-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="5df77-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5df77-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="5df77-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="5df77-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="5df77-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5df77-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

