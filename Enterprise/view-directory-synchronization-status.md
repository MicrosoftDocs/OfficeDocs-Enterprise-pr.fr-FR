---
title: Consulter l’état de synchronisation des annuaires dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d'annuaires. Vous pouvez également afficher son état.
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492100"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="659c1-104">Consulter l’état de synchronisation des annuaires dans Office 365</span><span class="sxs-lookup"><span data-stu-id="659c1-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="659c1-105">Si vous avez intégré Active Directory sur site à Azure AD en synchronisant votre environnement local avec Office 365, vous pouvez également vérifier l'état de votre synchronisation.</span><span class="sxs-lookup"><span data-stu-id="659c1-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="659c1-106">Afficher l'état de la synchronisation d'annuaires</span><span class="sxs-lookup"><span data-stu-id="659c1-106">View directory synchronization status</span></span>

- <span data-ttu-id="659c1-107">Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d'accueil.</span><span class="sxs-lookup"><span data-stu-id="659c1-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="659c1-108">Vous pouvez également accéder à \*\*\*\* \> utilisateurs **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner **plus** \> de synchronisation d' **annuaires**.</span><span class="sxs-lookup"><span data-stu-id="659c1-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="659c1-109">Dans le volet **synchronisation** d'annuaires, sélectionnez **accéder à la gestion DirSync**.</span><span class="sxs-lookup"><span data-stu-id="659c1-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="659c1-110">Informations sur la page gérer la synchronisation d'annuaires</span><span class="sxs-lookup"><span data-stu-id="659c1-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="659c1-111">Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.</span><span class="sxs-lookup"><span data-stu-id="659c1-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="659c1-112">En cas de problème avec la synchronisation d'annuaires, les erreurs sont également répertoriées sur cette page.</span><span class="sxs-lookup"><span data-stu-id="659c1-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="659c1-113">Pour plus d'informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d'annuaires dans Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="659c1-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="659c1-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="659c1-114">**Item**</span></span>|<span data-ttu-id="659c1-115">**Objet**</span><span class="sxs-lookup"><span data-stu-id="659c1-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="659c1-116">**Domaines vérifiés**</span><span class="sxs-lookup"><span data-stu-id="659c1-116">**Domains verified**</span></span> | <span data-ttu-id="659c1-117">Nombre de domaines dans votre client 365 Office que vous avez vérifié.</span><span class="sxs-lookup"><span data-stu-id="659c1-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="659c1-118">**Domaines non vérifiés**</span><span class="sxs-lookup"><span data-stu-id="659c1-118">**Domains not verified**</span></span> | <span data-ttu-id="659c1-119">Les domaines que vous avez ajoutés, mais qui n'ont pas été vérifiés.</span><span class="sxs-lookup"><span data-stu-id="659c1-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="659c1-120">**Synchronisation d'annuaires activée**</span><span class="sxs-lookup"><span data-stu-id="659c1-120">**Directory sync enabled**</span></span> |<span data-ttu-id="659c1-121">True ou false.</span><span class="sxs-lookup"><span data-stu-id="659c1-121">True or False.</span></span> <span data-ttu-id="659c1-122">Indique si la synchronisation d'annuaires est activée.</span><span class="sxs-lookup"><span data-stu-id="659c1-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="659c1-123">**Dernière synchronisation d'annuaires**</span><span class="sxs-lookup"><span data-stu-id="659c1-123">**Latest directory sync**</span></span> | <span data-ttu-id="659c1-124">Dernière exécution de la synchronisation d'annuaires.</span><span class="sxs-lookup"><span data-stu-id="659c1-124">Last time directory sync ran.</span></span> <span data-ttu-id="659c1-125">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="659c1-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="659c1-126">**Synchronisation de mot de passe activée**</span><span class="sxs-lookup"><span data-stu-id="659c1-126">**Password sync enabled**</span></span> | <span data-ttu-id="659c1-127">True ou false.</span><span class="sxs-lookup"><span data-stu-id="659c1-127">True or False.</span></span> <span data-ttu-id="659c1-128">Spécifie si la synchronisation de hachage de mot de passe entre notre client local et votre client 365 Office est terminée.</span><span class="sxs-lookup"><span data-stu-id="659c1-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="659c1-129">**Dernière synchronisation de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="659c1-129">**Last Password Sync**</span></span> | <span data-ttu-id="659c1-130">Dernière exécution de la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="659c1-130">Last time password hash sync ran.</span></span> <span data-ttu-id="659c1-131">Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="659c1-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="659c1-132">**Version du client de synchronisation d'annuaires**</span><span class="sxs-lookup"><span data-stu-id="659c1-132">**Directory sync client version**</span></span> | <span data-ttu-id="659c1-133">Contient un lien de téléchargement si une nouvelle version d'Azure AD Connect a été publiée.</span><span class="sxs-lookup"><span data-stu-id="659c1-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="659c1-134">**Outil IDFix**</span><span class="sxs-lookup"><span data-stu-id="659c1-134">**IDFix Tool**</span></span> | <span data-ttu-id="659c1-135">Téléchargez le lien vers [IDFix](install-and-run-idfix.md), un outil que vous pouvez utiliser pour vérifier l'Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="659c1-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="659c1-136">**Compte de service de synchronisation d'annuaires**</span><span class="sxs-lookup"><span data-stu-id="659c1-136">**Directory sync service account**</span></span> | <span data-ttu-id="659c1-137">Affiche le nom de votre compte de service de synchronisation d'annuaires Office 365.</span><span class="sxs-lookup"><span data-stu-id="659c1-137">Displays the name of you Office 365 directory sync service account.</span></span> |