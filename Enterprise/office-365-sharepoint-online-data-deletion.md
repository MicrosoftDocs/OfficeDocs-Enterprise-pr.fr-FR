---
title: Suppression des données SharePoint Online d’Office 365
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
description: Explication de la suppression de données dans SharePoint Online.
ms.openlocfilehash: ff219654387a17598f1ada8c866a005d8d4f5449
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067404"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a><span data-ttu-id="c572c-103">Suppression des données SharePoint Online dans Office 365</span><span class="sxs-lookup"><span data-stu-id="c572c-103">SharePoint Online Data Deletion in Office 365</span></span>

<span data-ttu-id="c572c-104">SharePoint Online stocke les objets en tant que code abstrait dans les bases de données d’application.</span><span class="sxs-lookup"><span data-stu-id="c572c-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="c572c-105">Lorsqu’un utilisateur télécharge un fichier vers SharePoint Online, ce fichier est décomposé et converti en code d’application et stocké dans plusieurs tables sur plusieurs bases de données.</span><span class="sxs-lookup"><span data-stu-id="c572c-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="c572c-106">Dans SharePoint Online, tout le contenu qu’un client télécharge est divisé en segments, chiffrés (éventuellement avec plusieurs clés AES 256 bits) et distribué dans le centre de données.</span><span class="sxs-lookup"><span data-stu-id="c572c-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="c572c-107">Pour plus d’informations sur le processus de segmentation et de chiffrement, voir [chiffrement dans le Cloud Microsoft](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c572c-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).</span></span> 

<span data-ttu-id="c572c-108">Dans SharePoint Online, les éléments sont conservés pendant 93 jours après leur suppression de leur emplacement d’origine.</span><span class="sxs-lookup"><span data-stu-id="c572c-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="c572c-109">Elles restent dans la corbeille de site à l’heure entière, sauf si quelqu’un les supprime de cette corbeille ou la vide.</span><span class="sxs-lookup"><span data-stu-id="c572c-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="c572c-110">Dans ce cas, les éléments sont placés dans la corbeille de la collection de sites, où ils restent pendant les 93 jours.</span><span class="sxs-lookup"><span data-stu-id="c572c-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="c572c-111">Pour plus d’informations sur la restauration des éléments supprimés, voir [restaurer des éléments dans la corbeille d’un site SharePoint](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) et [restaurer des éléments supprimés de la corbeille de la collection de sites](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span><span class="sxs-lookup"><span data-stu-id="c572c-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="c572c-112">La durée de rétention de la Corbeille n’est pas configurable dans SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c572c-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="c572c-113">Lorsque vous supprimez une collection de sites, vous supprimez également la hiérarchie des sites de la collection et tout le contenu qu’elles contiennent :</span><span class="sxs-lookup"><span data-stu-id="c572c-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>
- <span data-ttu-id="c572c-114">les documents et bibliothèques de documents ;</span><span class="sxs-lookup"><span data-stu-id="c572c-114">Documents and document libraries</span></span>
- <span data-ttu-id="c572c-115">Listes et données de liste</span><span class="sxs-lookup"><span data-stu-id="c572c-115">Lists and list data</span></span>
- <span data-ttu-id="c572c-116">Paramètres de configuration de site</span><span class="sxs-lookup"><span data-stu-id="c572c-116">Site configuration settings</span></span>
- <span data-ttu-id="c572c-117">Informations de rôle et de sécurité liées au site ou à ses sous-sites</span><span class="sxs-lookup"><span data-stu-id="c572c-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="c572c-118">Sous-sites du site Web de niveau supérieur, leur contenu et les informations utilisateur</span><span class="sxs-lookup"><span data-stu-id="c572c-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="c572c-119">Si vous supprimez accidentellement une collection de sites, elle peut être restaurée par un administrateur global ou SharePoint à l’aide du centre d’administration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c572c-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span> 

<span data-ttu-id="c572c-120">La suppression matérielle se produit lorsqu’un utilisateur purge les éléments supprimés de la corbeille de la collection de sites, lorsque les périodes de rétention et de sauvegarde expirent, ou lorsqu’un administrateur supprime définitivement une collection de sites à l’aide de la [cmdlet Remove-spodeletedsit](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="c572c-120">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="c572c-121">Quand un utilisateur supprime (supprime définitivement ou purge) le contenu de SharePoint Online, toutes les clés de chiffrement pour les segments supprimés sont également supprimées.</span><span class="sxs-lookup"><span data-stu-id="c572c-121">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="c572c-122">Les blocs sur les disques qui stockaient les segments supprimés précédemment sont marqués comme inutilisés et disponibles pour une réutilisation.</span><span class="sxs-lookup"><span data-stu-id="c572c-122">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>