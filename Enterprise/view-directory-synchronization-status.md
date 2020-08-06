---
title: Afficher l’état de la synchronisation d’annuaires dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d’annuaires. Vous pouvez également afficher son état.
ms.openlocfilehash: 4c2f0baf6d3657e3eb9974ff7d4f8109e52e603b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571037"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="55e9d-104">Afficher l’état de la synchronisation d’annuaires dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="55e9d-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="55e9d-105">Si vous avez intégré Active Directory sur site à Azure AD en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.</span><span class="sxs-lookup"><span data-stu-id="55e9d-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="55e9d-106">Consulter l’état de synchronisation des annuaires</span><span class="sxs-lookup"><span data-stu-id="55e9d-106">View directory synchronization status</span></span>

- <span data-ttu-id="55e9d-107">Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d’accueil.</span><span class="sxs-lookup"><span data-stu-id="55e9d-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="55e9d-108">Vous pouvez également **accéder à utilisateurs** \> **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner plus de **More** \> **synchronisation d’annuaires**.</span><span class="sxs-lookup"><span data-stu-id="55e9d-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="55e9d-109">Dans le volet **synchronisation d’annuaires** , sélectionnez **accéder à la gestion DirSync**.</span><span class="sxs-lookup"><span data-stu-id="55e9d-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="55e9d-110">Informations sur la page gérer la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="55e9d-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="55e9d-111">Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.</span><span class="sxs-lookup"><span data-stu-id="55e9d-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="55e9d-112">En cas de problème avec la synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page.</span><span class="sxs-lookup"><span data-stu-id="55e9d-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="55e9d-113">Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="55e9d-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="55e9d-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="55e9d-114">**Item**</span></span>|<span data-ttu-id="55e9d-115">**Objet**</span><span class="sxs-lookup"><span data-stu-id="55e9d-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="55e9d-116">**Domaines vérifiés**</span><span class="sxs-lookup"><span data-stu-id="55e9d-116">**Domains verified**</span></span> | <span data-ttu-id="55e9d-117">Nombre de domaines de votre client Microsoft 365 que vous avez vérifié.</span><span class="sxs-lookup"><span data-stu-id="55e9d-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="55e9d-118">**Domaines non vérifiés**</span><span class="sxs-lookup"><span data-stu-id="55e9d-118">**Domains not verified**</span></span> | <span data-ttu-id="55e9d-119">Les domaines que vous avez ajoutés, mais qui n’ont pas été vérifiés.</span><span class="sxs-lookup"><span data-stu-id="55e9d-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="55e9d-120">**Synchronisation d’annuaires activée**</span><span class="sxs-lookup"><span data-stu-id="55e9d-120">**Directory sync enabled**</span></span> |<span data-ttu-id="55e9d-121">True ou false.</span><span class="sxs-lookup"><span data-stu-id="55e9d-121">True or False.</span></span> <span data-ttu-id="55e9d-122">Indique si la synchronisation d’annuaires est activée.</span><span class="sxs-lookup"><span data-stu-id="55e9d-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="55e9d-123">**Dernière synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="55e9d-123">**Latest directory sync**</span></span> | <span data-ttu-id="55e9d-124">Dernière exécution de la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="55e9d-124">Last time directory sync ran.</span></span> <span data-ttu-id="55e9d-125">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="55e9d-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="55e9d-126">**Synchronisation de mot de passe activée**</span><span class="sxs-lookup"><span data-stu-id="55e9d-126">**Password sync enabled**</span></span> | <span data-ttu-id="55e9d-127">True ou false.</span><span class="sxs-lookup"><span data-stu-id="55e9d-127">True or False.</span></span> <span data-ttu-id="55e9d-128">Indique si la synchronisation de hachage de mot de passe s’est déplacée entre notre client local et votre client Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="55e9d-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="55e9d-129">**Dernière synchronisation de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="55e9d-129">**Last Password Sync**</span></span> | <span data-ttu-id="55e9d-130">Dernière exécution de la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="55e9d-130">Last time password hash sync ran.</span></span> <span data-ttu-id="55e9d-131">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="55e9d-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="55e9d-132">**Version du client de synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="55e9d-132">**Directory sync client version**</span></span> | <span data-ttu-id="55e9d-133">Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée.</span><span class="sxs-lookup"><span data-stu-id="55e9d-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="55e9d-134">**Compte de service de synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="55e9d-134">**Directory sync service account**</span></span> | <span data-ttu-id="55e9d-135">Affiche le nom de votre compte de service de synchronisation d’annuaires Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="55e9d-135">Displays the name of your Microsoft 365 directory sync service account.</span></span> |