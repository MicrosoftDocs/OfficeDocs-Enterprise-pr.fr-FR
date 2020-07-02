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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements dans leurs offres de services pour les clients. Ils possèdent un client qui bénéficie automatiquement des autorisations d’administration pour le compte de (administrateur) pour leurs clients Microsoft 365, afin qu’ils puissent administrer et rendre compte de tous leurs locations de clients.

Les partenaires DAP peuvent utiliser Exchange Online PowerShell pour gérer les paramètres Exchange Online du client et obtenir des rapports Microsoft 365 à partir de la ligne de commande. Vous utilisez Windows PowerShell sur votre ordinateur local pour créer une session PowerShell distante vers Exchange Online. Il s’agit d’un processus simple en trois étapes dans lequel vous entrez vos informations d’identification, fournissez les paramètres de connexion requis, puis importez les applets de commande Exchange Online dans votre session Windows PowerShell locale afin de pouvoir les utiliser.

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

- Durée d’exécution estimée : 5 minutes

- Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 ou Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Pour exiger que tous les scripts PowerShell téléchargés depuis Internet soient signés par un éditeur approuvé, exécutez la commande suivante dans une fenêtre Windows PowerShell avec élévation de privilèges (c’est-à-dire une fenêtre Windows PowerShell ouverte en sélectionnant **Exécuter en tant qu’administrateur**) :

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  Vous devez configurer ce paramètre une fois seulement sur votre ordinateur, pas à chaque connexion.

- Pour des informations sur les raccourcis clavier applicables aux procédures de cette rubrique, consultez la rubrique [Raccourcis clavier dans le Centre d’administration Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Connexion à Exchange Online pour les organisations clientes

1. Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante.
    
    ```
    $UserCredential = Get-Credential
    ```

    Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez vos nom d’utilisateur et mot de passe d’administrateur DAP, puis cliquez sur **OK**.
    
2. Remplacez _\<customer tenant domain name\>_ par le nom du domaine client auquel vous voulez vous connecter, puis exécutez la commande suivante :
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    Dans cette commande, l'étape clé consiste à spécifier le client auquel accéder pour les informations de création de rapports. Pour ce faire, utilisez le paramètre _ConnectionUri_ , dans lequel vous indiquez le nom de domaine complet du nom de domaine initial comme valeur de `?DelegatedOrg=` . Cette valeur indique le point de terminaison Exchange Online PowerShell correct auquel se connecter. Remote PowerShell doit se connecter à Microsoft 365 Reporting dans le contexte d’un client spécifique chaque fois qu’un rapport est exécuté. Une fois que vous vous êtes connecté à Exchange Online PowerShell, toutes les commandes suivantes sont exécutées dans le contexte du client, ce qui vous permet d’accéder à tous les rapports disponibles pour le client.
    
3. Exécutez la commande suivante.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Appel de la cmdlet directement avec la commande Invoke

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Plus de cmdlets de création de rapports

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

