---
title: Permet de réduire la mémoire utilisée lors de la lecture des messages vocaux popouts maigre
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Cet article contient des informations pour améliorer les performances de téléchargement de message dans Outlook sur le web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540401"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Permet de réduire la mémoire utilisée lors de la lecture des messages vocaux popouts maigre

Cet article contient des informations pour améliorer les performances de téléchargement de message dans Outlook sur le web. Cet article fait partie du projet [de planification du réseau et de réglage des performances pour Office 365](https://aka.ms/tune) .
   
Un administrateur global d’Office 365, vous pouvez configurer Outlook sur le web afin d’offrir *popouts maigre* , un plus petit, moins la version gourmandes en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer. Maigre popouts sont configurés pour Outlook sur le web, composants de rendu côté serveur sont chargés qui optimisent les performances. 
  
> [!NOTE]
> À compter de mars 2018, popouts maigre n’est actuellement pas disponibles pour les messages qui spécifient les restrictions de droits d’utilisation, telles que Information Rights Management (IRM). 
  
Ces fonctionnalités continueront de fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans maigre popouts :
  
- Compléments Outlook
    
- Skype pour présence commerciale
    
 **Pour configurer maigre popouts pour tous les utilisateurs au sein de votre organisation Office 365**
  
1. [Se connecter à Exchange Online à l’aide de PowerShell à distance](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Exécutez l’applet de commande [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) avec le paramètre LeanPopoutEnabled comme suit : 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Par exemple, pour activer maigre popouts pour tous les utilisateurs de votre organisation :
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Pour désactiver maigre popouts pour tous les utilisateurs de votre organisation :
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


