---
title: Utiliser le la messagerie instantanée épuré pour réduire la mémoire utilisée lors de la lecture des messages électroniques
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Cet article contient des informations sur l’amélioration des performances de téléchargement de messages dans Outlook sur le Web.
ms.openlocfilehash: 49b570da9092ce4fc857757a7da72b2a81fd0090
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843905"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Utiliser le la messagerie instantanée épuré pour réduire la mémoire utilisée lors de la lecture des messages électroniques

Cet article contient des informations sur l’amélioration des performances de téléchargement de messages dans Outlook sur le Web. Cet article fait partie du projet [planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune) .
  
En tant qu’administrateur général Office 365, vous pouvez configurer Outlook sur le Web pour la remise de _la messagerie instantanée_, une version plus petite et moins gourmande en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer. Lorsque les la messagerie instantanée de Lean sont configurés pour Outlook sur le Web, les composants rendus côté serveur sont chargés et optimisent les performances.
  
> [!NOTE]
> Depuis le 2018 mars, le la messagerie instantanée épuré n’est pas disponible pour les messages qui spécifient des restrictions relatives aux droits d’utilisation, tels que la gestion des droits relatifs à l’information (IRM).
  
Ces fonctionnalités continueront à fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans le la messagerie instantanée épuré :
  
- Compléments Outlook
  
- Présence de Skype entreprise
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Pour configurer le Lean la messagerie instantanée pour tous les utilisateurs au sein de votre organisation Office 365
  
1. [Connectez-vous à Exchange Online à l’aide de Remote PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
  
2. Exécutez la cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) avec le paramètre LeanPopoutEnabled comme suit :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Par exemple, pour activer le la messagerie instantanée épuré pour tous les utilisateurs de votre organisation :
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Pour désactiver la la messagerie instantanée épurée pour tous les utilisateurs de votre organisation :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
