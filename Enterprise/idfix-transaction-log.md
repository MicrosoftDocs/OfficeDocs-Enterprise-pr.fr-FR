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
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="e4b8a-103">Office 365 IdFix journal des transactions</span><span class="sxs-lookup"><span data-stu-id="e4b8a-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="e4b8a-104">*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="e4b8a-105">Fournit un exemple et décrit la Convention d’affectation de noms et le niveau de journalisation par défaut du journal des transactions d’Office 365 IdFix.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-105">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="e4b8a-106">Emplacement du journal des transactions IdFix</span><span class="sxs-lookup"><span data-stu-id="e4b8a-106">IdFix transaction log location</span></span>

<span data-ttu-id="e4b8a-107">L’outil IdFix Office 365 crée un nouveau journal des transactions chaque fois que vous cliquez sur **appliquer** dans IdFix et que vous appliquez les modifications à la forêt Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-107">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="e4b8a-108">Le journal des transactions est enregistré dans le dossier où vous avez installé IdFix.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="e4b8a-109">Par défaut, ce dossier est C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="e4b8a-110">Le nom du fichier journal des transactions utilise un format de date et d’heure, par exemple, verbose 6-1-2018 6-17-22 PM indique un fichier qui a été généré le 1er juin 2018 à 6:17:22 PM.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="e4b8a-111">Verbose indique le niveau de journalisation.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="e4b8a-112">Niveau d’enregistrement du journal des transactions IdFix</span><span class="sxs-lookup"><span data-stu-id="e4b8a-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="e4b8a-113">Le mot détaillé dans le nom du fichier journal des transactions indique le niveau de journalisation dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="e4b8a-114">Verbose signifie que la quantité maximale d’informations est capturée dans le journal.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="e4b8a-115">Il s’agit du niveau de journalisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-115">This is the default logging level.</span></span> <span data-ttu-id="e4b8a-116">Pour le moment, vous ne pouvez pas modifier le niveau de journalisation.</span><span class="sxs-lookup"><span data-stu-id="e4b8a-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="e4b8a-117">Format de journal des transactions IdFix</span><span class="sxs-lookup"><span data-stu-id="e4b8a-117">IdFix transaction log format</span></span>

<span data-ttu-id="e4b8a-118">IdFix écrit les résultats de chaque action de **mise à jour** dans un journal des transactions, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e4b8a-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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