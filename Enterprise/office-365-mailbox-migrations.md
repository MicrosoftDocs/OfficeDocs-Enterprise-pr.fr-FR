---
title: Migrations de boîtes aux lettres Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Bref résumé des applets de commande utilisées pour les migrations de boîtes aux lettres Office 365.
ms.openlocfilehash: b3af6d4b392e45a5200917bf5cebf22c601620a2
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843605"
---
# <a name="office-365-mailbox-migrations"></a>Migrations de boîtes aux lettres Office 365

Avec un déploiement hybride basé sur Exchange, les clients peuvent choisir de déplacer des boîtes aux lettres Exchange locales vers une organisation [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) ou de déplacer des boîtes aux lettres Exchange Online vers une organisation [Exchange locale](https://docs.microsoft.com/Exchange/exchange-server) . Les lots de migration sont utilisés lors du déplacement de boîtes aux lettres entre des organisations locales et Exchange Online.

Les clients peuvent consulter les statistiques et d’autres informations sur les migrations de boîtes aux lettres avec les cmdlets suivantes :

- [Get-MoveRequestStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): fournit des statistiques par défaut pour une boîte aux lettres d’utilisateur, qui inclut l’État, la taille de boîte aux lettres, la taille de boîte aux lettres d’archivage et le pourcentage d’achèvement.
- [Get-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): fournit une liste récapitulative des objets et des attributs de boîte aux lettres dans l’organisation.
- [Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): fournit une liste des objets à extension messagerie existants, tels que les boîtes aux lettres, les utilisateurs de messagerie, les contacts et les groupes de distribution.
- [Get-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): fournit un état détaillé de la migration de boîte aux lettres en cours.
- [Get-MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): fournit des informations sur les utilisateurs de migration et de déplacement de boîtes aux lettres.
- [Get-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): fournit des informations sur l’état du lot de migration actuel.
- [Get-MigrationUserStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): fournit des informations détaillées sur l’état de la migration pour un utilisateur spécifique.
- [Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): fournit des informations sur les boîtes aux lettres, telles que la taille, le nombre de messages et l’heure du dernier accès.

Pour plus d’informations sur les applets de commande, voir [Move and migration cmdlets in Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).
