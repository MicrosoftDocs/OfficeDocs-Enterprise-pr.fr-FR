---
title: Office 365 IdFix journal des transactions
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fournit un exemple et décrit la Convention d’affectation de noms et le niveau de journalisation par défaut du journal des transactions d’Office 365 IdFix.
ms.openlocfilehash: fb294095dc5b163965660546f5033a845d6cb0b4
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840111"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix journal des transactions

*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.

Fournit un exemple et décrit la Convention d’affectation de noms et le niveau de journalisation par défaut du journal des transactions d’Office 365 IdFix.
  
## <a name="idfix-transaction-log-location"></a>Emplacement du journal des transactions IdFix

L’outil IdFix Office 365 crée un nouveau journal des transactions chaque fois que vous cliquez sur **appliquer** dans IdFix et que vous appliquez les modifications à la forêt Active Directory. Le journal des transactions est enregistré dans le dossier où vous avez installé IdFix. Par défaut, ce dossier est C:\Deployment Tools\IDFix. Le nom du fichier journal des transactions utilise un format de date et d’heure, par exemple, verbose 6-1-2018 6-17-22 PM indique un fichier qui a été généré le 1er juin 2018 à 6:17:22 PM. Verbose indique le niveau de journalisation. 
  
## <a name="idfix-transaction-log-logging-level"></a>Niveau d’enregistrement du journal des transactions IdFix

Le mot détaillé dans le nom du fichier journal des transactions indique le niveau de journalisation dans le fichier. Verbose signifie que la quantité maximale d’informations est capturée dans le journal. Il s’agit du niveau de journalisation par défaut. Pour le moment, vous ne pouvez pas modifier le niveau de journalisation.
  
## <a name="idfix-transaction-log-format"></a>Format de journal des transactions IdFix

IdFix écrit les résultats de chaque action de **mise à jour** dans un journal des transactions, comme illustré dans l’exemple suivant :
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE
```