---
title: Journal des transactions IdFix Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fournit un exemple et décrit la convention d’affectation de noms et le niveau de journalisation par défaut du journal des transactions IdFix d’Office 365.
ms.openlocfilehash: 016318c7e771ec6c5f90336e11c5dd011144d12e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540476"
---
# <a name="office-365-idfix-transaction-log"></a>Journal des transactions IdFix Office 365

Fournit un exemple et décrit la convention d’affectation de noms et le niveau de journalisation par défaut du journal des transactions IdFix d’Office 365.
  
## <a name="idfix-transaction-log-location"></a>Emplacement du journal des transactions IdFix

L’outil IdFix d’Office 365 crée un nouveau journal chaque fois que vous cliquez sur **Appliquer** dans IdFix et appliquez les modifications à la forêt Active Directory. Le journal des transactions est enregistré dans le même dossier où vous avez installé IdFix. Par défaut, ce dossier est C:\Deployment Tools\IDFix. Le nom du fichier journal des transactions utilise un format de date et date et heure, par exemple, Verbose 6-1-2018 6-17-22 h indique un fichier qui a été généré à 1, juin 2018 à 6:17:22 PM Verbose indique le niveau de journalisation. 
  
## <a name="idfix-transaction-log-logging-level"></a>Niveau de journalisation du journal des transactions IdFix

Le mot « verbose » dans le nom de fichier journal de transactions indique le niveau de journalisation dans le fichier. Verbose signifie que la quantité maximale d'informations est saisie dans le journal. Il s'agit du niveau de journalisation par défaut. À ce stade, vous ne pouvez pas modifier le niveau de journalisation.
  
## <a name="idfix-transaction-log-format"></a>Format du journal des transactions IdFix

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