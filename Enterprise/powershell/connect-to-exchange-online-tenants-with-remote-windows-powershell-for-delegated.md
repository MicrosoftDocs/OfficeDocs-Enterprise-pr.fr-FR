---
title: Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Résumé : Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l’aide de la valeur DelegatedOrg.'
ms.openlocfilehash: 4dfe54088a1b60b0bcf7e7563362c0b2a413f3ad
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069150"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d’accès délégué

 **Résumé :** Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l’aide de la valeur `DelegatedOrg`.

> [!IMPORTANT]
> Les procédures décrites dans cette rubrique sont uniquement destinées aux partenaires avec autorisation d’accès délégué (DAP). Si vous n’êtes pas un partenaire DAP, n’utilisez pas les procédures décrites dans cette rubrique. 
  
Les partenaires avec autorisation d’accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent les abonnements dans leurs offres de services pour les clients. Ils possèdent une location partenaire qui dispose automatiquement des autorisations Administrer au nom de (AOBO) pour leurs locations clientes Office 365, afin de pouvoir administrer et créer des rapports sur toutes leurs locations clientes.

Les partenaires DAP peuvent utiliser Exchange Online PowerShell pour gérer les paramètres Exchange Online des clients et obtenir des rapports Office 365 à partir de la ligne de commande. Vous utilisez Windows PowerShell sur votre ordinateur local pour créer une session PowerShell distante vers Exchange Online. Il s’agit d’un processus simple en trois étapes dans lequel vous entrez vos informations d’identification, vous indiquez les paramètres de connexion requis, puis vous importez les cmdlets Exchange Online dans votre session Windows PowerShell locale afin de pouvoir les utiliser.

> [!NOTE]
> Les partenaires DAP ne peuvent pas utiliser les procédures décrites dans [Connexion à Exchange Online PowerShell avec l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) pour se connecter à leur organisation locataire cliente dans Exchange Online PowerShell. L’authentification multifacteur et le module PowerShell distant Exchange Online ne fonctionnent pas avec l’authentification déléguée.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d’exécution estimée : 5 minutes

- Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 ou Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> Pour les versions antérieures de Windows, vous devez installer Microsoft.NET Framework 4.5 ou version ultérieure, puis une version mise à jour de Windows Management Framework : 3.0, 4.0 ou 5.1 (une seule). Pour plus d’informations, reportez-vous à [Installer le .NET Framework pour les développeurs](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) et [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell doit être configuré pour exécuter des scripts, ce qui n’est pas le cas par défaut. Vous obtenez l’erreur suivante lorsque vous essayez de vous connecter :

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
    
2. Remplacez _\<customer tenant domain name\>_ par le nom du domaine client auquel vous voulez vous connecter, et exécutez la commande suivante :
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    Dans cette commande, l’étape clé consiste à spécifier le client auquel accéder pour les informations de création de rapports. Pour ce faire, fournissez le nom de domaine complet du nom de domaine initial dans le paramètre _ConnectionURI_, en tant que valeur pour `?DelegatedOrg=`. Cette valeur indique le point de terminaison Exchange Online PowerShell approprié auquel se connecter. PowerShell à distance doit se connecter aux rapports Office 365 dans le contexte d’un client spécifique chaque fois qu’un rapport est exécuté. Une fois que vous êtes connecté à Exchange Online PowerShell, toutes les commandes suivantes sont exécutées dans le contexte du client. Cela vous permet d’accéder à tous les rapports disponibles pour ce client.
    
3. Exécutez la commande suivante.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> Trois sessions simultanées peuvent être exécutées sous un seul compte au maximum. N’oubliez pas de déconnecter la session PowerShell distante dès que vous avez terminé. Si vous fermez la fenêtre Windows PowerShell sans déconnecter la session, vous risquez d’épuiser toutes les sessions PowerShell distantes à votre disposition et vous devrez attendre que les sessions expirent. Pour déconnecter la session PowerShell distante, exécutez la commande suivante :

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Après l’étape 3, les cmdlets Exchange Online sont importées dans votre session Windows PowerShell locale comme indiqué par une barre de progression. Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter une cmdlet Exchange Online (par exemple, **Get-Mailbox**) et à consulter les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- Un mot de passe incorrect est un problème courant. Exécutez à nouveau les trois étapes et portez une attention particulière au nom d’utilisateur et au mot de passe que vous entrez à l’étape 1.
    
- Le compte que vous utilisez pour vous connecter à Exchange Online doit être activé pour PowerShell à distance. Pour plus d’informations, reportez-vous à l’article sur la [gestion de l’accès à PowerShell à distance dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- Le trafic du port TCP 80 doit être ouvert entre votre ordinateur local et Exchange Online. Il est probablement ouvert, mais vous devez y penser si votre organisation a une stratégie restrictive d'accès à Internet.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Appel de la cmdlet directement avec la commande Invoke

L’importation d’une session PowerShell distante (étape 3) peut être un processus long, car _toutes_ les cmdlets Exchange Online sont importées. Cela peut représenter un problème dans le cadre du traitement par lots, par exemple, lorsque vous exécutez des rapports ou effectuez des modifications en bloc pour différents clients. En guise d’alternative à l’utilisation d’**Import-PSSession**, vous pouvez appeler les cmdlets que vous voulez utiliser directement avec **Invoke-Command**. Par exemple, pour appeler la cmdlet **Get-Mailbox**, utilisez la syntaxe suivante à la place pour la commande `Import-PSSession $Session` à l’étape 3 :
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Plus de cmdlets de création de rapports

Les cmdlets que vous utilisez dans cette rubrique sont des cmdlets Windows PowerShell. Pour plus d'informations à propos de ces cmdlets, consultez les rubriques suivantes :
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

