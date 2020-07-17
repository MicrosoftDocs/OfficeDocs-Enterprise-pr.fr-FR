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
ms.openlocfilehash: d6f3a9f1f4e069716501f58e188daedacbf7e597
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906197"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="18965-104">Afficher l’état de la synchronisation d’annuaires dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="18965-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="18965-105">Si vous avez intégré Active Directory sur site à Azure AD en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.</span><span class="sxs-lookup"><span data-stu-id="18965-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="18965-106">Consulter l’état de synchronisation des annuaires</span><span class="sxs-lookup"><span data-stu-id="18965-106">View directory synchronization status</span></span>

- <span data-ttu-id="18965-107">Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d’accueil.</span><span class="sxs-lookup"><span data-stu-id="18965-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="18965-108">Vous pouvez également **accéder à utilisateurs** \> **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner plus de **More** \> **synchronisation d’annuaires**.</span><span class="sxs-lookup"><span data-stu-id="18965-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="18965-109">Dans le volet **synchronisation d’annuaires** , sélectionnez **accéder à la gestion DirSync**.</span><span class="sxs-lookup"><span data-stu-id="18965-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="18965-110">Informations sur la page gérer la synchronisation d’annuaires</span><span class="sxs-lookup"><span data-stu-id="18965-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="18965-111">Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.</span><span class="sxs-lookup"><span data-stu-id="18965-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="18965-112">En cas de problème avec la synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page.</span><span class="sxs-lookup"><span data-stu-id="18965-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="18965-113">Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="18965-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="18965-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="18965-114">**Item**</span></span>|<span data-ttu-id="18965-115">**Objet**</span><span class="sxs-lookup"><span data-stu-id="18965-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="18965-116">**Domaines vérifiés**</span><span class="sxs-lookup"><span data-stu-id="18965-116">**Domains verified**</span></span> | <span data-ttu-id="18965-117">Nombre de domaines de votre client Microsoft 365 que vous avez vérifié.</span><span class="sxs-lookup"><span data-stu-id="18965-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="18965-118">**Domaines non vérifiés**</span><span class="sxs-lookup"><span data-stu-id="18965-118">**Domains not verified**</span></span> | <span data-ttu-id="18965-119">Les domaines que vous avez ajoutés, mais qui n’ont pas été vérifiés.</span><span class="sxs-lookup"><span data-stu-id="18965-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="18965-120">**Synchronisation d’annuaires activée**</span><span class="sxs-lookup"><span data-stu-id="18965-120">**Directory sync enabled**</span></span> |<span data-ttu-id="18965-121">True ou false.</span><span class="sxs-lookup"><span data-stu-id="18965-121">True or False.</span></span> <span data-ttu-id="18965-122">Indique si la synchronisation d’annuaires est activée.</span><span class="sxs-lookup"><span data-stu-id="18965-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="18965-123">**Dernière synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="18965-123">**Latest directory sync**</span></span> | <span data-ttu-id="18965-124">Dernière exécution de la synchronisation d’annuaires.</span><span class="sxs-lookup"><span data-stu-id="18965-124">Last time directory sync ran.</span></span> <span data-ttu-id="18965-125">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="18965-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="18965-126">**Synchronisation de mot de passe activée**</span><span class="sxs-lookup"><span data-stu-id="18965-126">**Password sync enabled**</span></span> | <span data-ttu-id="18965-127">True ou false.</span><span class="sxs-lookup"><span data-stu-id="18965-127">True or False.</span></span> <span data-ttu-id="18965-128">Indique si la synchronisation de hachage de mot de passe s’est déplacée entre notre client local et votre client Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="18965-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="18965-129">**Dernière synchronisation de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="18965-129">**Last Password Sync**</span></span> | <span data-ttu-id="18965-130">Dernière exécution de la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="18965-130">Last time password hash sync ran.</span></span> <span data-ttu-id="18965-131">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="18965-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="18965-132">**Version du client de synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="18965-132">**Directory sync client version**</span></span> | <span data-ttu-id="18965-133">Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée.</span><span class="sxs-lookup"><span data-stu-id="18965-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="18965-134">**Outil IDFix**</span><span class="sxs-lookup"><span data-stu-id="18965-134">**IDFix Tool**</span></span> | <span data-ttu-id="18965-135">Téléchargez le lien vers [IDFix](install-and-run-idfix.md), un outil que vous pouvez utiliser pour vérifier l’Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="18965-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="18965-136">**Compte de service de synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="18965-136">**Directory sync service account**</span></span> | <span data-ttu-id="18965-137">Affiche le nom de votre compte de service de synchronisation d’annuaires Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="18965-137">Displays the name of your Microsoft 365 directory sync service account.</span></span> |