---
title: "Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "Résumé : Utilisez Windows PowerShell distant pour vous connecter à Exchange Online à l'aide du paramètre DelegatedOrg."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué

 **Résumé :** Utilisation à distance de Windows PowerShell pour se connecter à Exchange Online à l’aide du paramètre _DelegatedOrg_ .
  
Windows PowerShell distant vous permet de gérer vos paramètres Exchange Online à partir de la ligne de commande. Vous pouvez utiliser Windows PowerShell sur votre ordinateur local pour créer une session distante vers Exchange Online. Il s'agit d'un processus simple en trois étapes, dans lequel vous entrez vos informations d'identification Exchange Online, vous indiquez les paramètres de connexion requis, puis vous importez les cmdlets Exchange Online dans votre session Windows PowerShell locale afin de pouvoir les utiliser.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d'exécution estimée : 5 minutes
    
- Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Vous devez installer .NET Framework 4.5.1 ou .NET Framework 4.5, puis Windows Management Framework 4.0 ou Windows Management Framework 3.0. Pour plus d'informations, consultez les ressources suivantes :
    
  - [Installation de NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Pour des informations sur les raccourcis clavier applicables aux procédures de cette rubrique, consultez la rubrique [Raccourcis clavier dans le Centre d'administration Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Cette procédure est destinée uniquement aux partenaires avec autorisation d'accès délégué. Si vous n'êtes pas un partenaire avec autorisation d'accès délégué, n'utilisez pas cette procédure. 
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s'agit souvent de fournisseurs de réseau ou de télécommunication pour d'autres sociétés. Ils regroupent les abonnements dans leurs offres de services pour les clients. Ils possèdent une location partenaire qui dispose automatiquement des autorisations Administrer au nom de (AOBO) pour leurs Office 365locations clientes, afin de pouvoir administrer et créer des rapports sur toutes leurs locations clientes.
  
## <a name="connect-to-exchange-online"></a>Vous connecter à Exchange Online

1. Sur votre ordinateur local, ouvrez Windows PowerShell et exécutez la commande suivante.
    
  ```
  $UserCredential = Get-Credential
  ```

    Dans la boîte de dialogue **Demande d'informations d'identification Windows PowerShell**, saisissez vos nom d'utilisateur et mot de passe d'administrateur DAP, puis cliquez sur **OK**.
    
2. Exécutez la commande suivante en remplaçant  _<customer tenant domain name>_ par le nom du domaine client auquel vous voulez vous connecter.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    Dans cette commande, l'étape clé consiste à spécifier le client auquel accéder pour les informations de création de rapports. Pour ce faire, vous fournissez le nom de domaine complet du nom de domaine initial dans le paramètre  _ConnectionURI_, en tant que valeur du paramètre  _DelegatedOrg_. Cela indique à Windows PowerShell distant pour Exchange Online PowerShell Windows PowerShell distant le point de terminaison auquel se connecter. Windows PowerShell distant doit se connecter aux rapports Office 365 dans le contexte d'un client spécifique chaque fois qu'un rapport est exécuté. Une fois que ce client est spécifié, toutes les commandes suivantes sont exécutées dans le contexte de ce client. Cela permet au partenaire d'accéder à tous les rapports disponibles pour ce client.
    
3. Exécutez la commande suivante.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> Trois sessions simultanées peuvent être exécutées sous un seul compte au maximum. N'oubliez pas de déconnecter la session Windows PowerShell distante dès que vous avez terminé. Si vous fermez la fenêtre Windows PowerShell sans déconnecter la session, vous risquez d'épuiser toutes les sessions Windows PowerShell distantes à votre disposition et vous devrez attendre que les sessions expirent. Pour déconnecter la session Windows PowerShell distante, exécutez la commande suivante. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Après l'étape 3, les cmdlets Exchange Online sont importées dans votre session Windows PowerShell locale comme indiqué par une barre de progression. Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter une cmdlet Exchange Online (par exemple, **Get-Mailbox** ) et à consulter les résultats.
  
Si vous recevez des erreurs, vérifiez les conditions requises suivantes :
  
- Un mot de passe incorrect est un problème courant. Exécutez à nouveau les trois étapes et portez une attention particulière au nom d'utilisateur et au mot de passe que vous entrez à l'étape 1.
    
- Pour éviter les attaques par déni de service, vous ne pouvez ouvrir que trois sessions Windows PowerShell distantes vers votre organisation Exchange Online.
    
- Windows PowerShell doit être configuré pour l'exécution de scripts. Vous devez configurer ce paramètre une fois seulement sur votre ordinateur, pas à chaque connexion. Pour activer l'exécution de scripts signés dans Windows PowerShell, exécutez la commande suivante dans une fenêtre Windows PowerShell élevée (fenêtre Windows PowerShell ouverte en sélectionnant **Exécuter en tant qu'administrateur**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Le compte que vous utilisez pour vous connecter à Exchange Online doit être activé pour Windows PowerShell distant. Pour plus d'informations, voir [Gérer l'accès à Remote PowerShell dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- Le trafic du port TCP 80 doit être ouvert entre votre ordinateur local et Exchange Online. Il est probablement ouvert, mais vous devez y penser si votre organisation a une stratégie restrictive d'accès à Internet.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Appel de la cmdlet directement avec la commande Invoke

L'importation d'une session Windows PowerShell distante peut être un processus long, car toutes les cmdlets Exchange Online sont importées. Cela peut représenter un problème dans le cadre du traitement par lots, par exemple, lorsque vous exécutez des rapports ou effectuez des modifications en bloc pour différents clients. En guise d'alternative à l'utilisation d' **Import-PSSession**, vous pouvez appeler des cmdlets que vous voulez utiliser directement avec **Invoke-Command**. Par exemple, pour appeler la cmdlet **get-mailbox**, remplacez la syntaxe suivante par `Import-PSSession $Session`.
  
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
    

