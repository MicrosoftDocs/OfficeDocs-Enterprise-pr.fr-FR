---
title: Afficher le statut de synchronisation d’annuaires dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Découvrez comment désactiver la synchronisation d’annuaires. Vous pouvez également afficher son statut.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540633"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="62bd6-104">Afficher le statut de synchronisation d’annuaires dans Office 365</span><span class="sxs-lookup"><span data-stu-id="62bd6-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="62bd6-105">Si vous avez intégré Active Directory local avec Azure AD par la synchronisation de votre environnement sur site avec Office 365, vous pouvez également vérifier l’état de la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="62bd6-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="62bd6-106">Afficher l’état de la synchronisation des annuaires</span><span class="sxs-lookup"><span data-stu-id="62bd6-106">View directory synchronization status</span></span>
- <span data-ttu-id="62bd6-107">Se connecter au centre d’administration Office 365 et choisissez **l’État de synchronisation d’annuaire** dans la page d’accueil.</span><span class="sxs-lookup"><span data-stu-id="62bd6-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="62bd6-p102">Sinon, vous pouvez accéder aux **utilisateurs** \> **utilisateurs actifs**, dans la page **utilisateurs actifs** , cliquez sur **plus de** \> **la synchronisation d’annuaires**. Dans le volet de **La synchronisation d’annuaires** , choisissez **accédez à gestion de la synchronisation d’annuaire**.</span><span class="sxs-lookup"><span data-stu-id="62bd6-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="62bd6-110">Pour plus d’informations sur la page de la synchronisation d’annuaire gérer</span><span class="sxs-lookup"><span data-stu-id="62bd6-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="62bd6-111">Le tableau suivant répertorie les fonctionnalités que vous pouvez obtenir des informations à propos de la page.</span><span class="sxs-lookup"><span data-stu-id="62bd6-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="62bd6-p103">Si il existe un problème avec votre la synchronisation d’annuaires, les erreurs sont répertoriés sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, voir [identifier des erreurs de synchronisation d’annuaire dans Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="62bd6-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="62bd6-114">**Élément**</span><span class="sxs-lookup"><span data-stu-id="62bd6-114">**Item**</span></span>|<span data-ttu-id="62bd6-115">**Elle concerne**</span><span class="sxs-lookup"><span data-stu-id="62bd6-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62bd6-116">**Domaines vérifiés**</span><span class="sxs-lookup"><span data-stu-id="62bd6-116">**Domains verified**</span></span> | <span data-ttu-id="62bd6-117">Nombre de domaines dans votre organisation cliente Office 365 que vous avez vérifié vous possédez.</span><span class="sxs-lookup"><span data-stu-id="62bd6-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="62bd6-118">**Domaines non vérifiées**</span><span class="sxs-lookup"><span data-stu-id="62bd6-118">**Domains not verified**</span></span> | <span data-ttu-id="62bd6-119">Vous avez ajouté, mais n’a ne pas vérifié les domaines.</span><span class="sxs-lookup"><span data-stu-id="62bd6-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="62bd6-120">**Synchronisation d’annuaires**</span><span class="sxs-lookup"><span data-stu-id="62bd6-120">**Directory sync enabled**</span></span> |<span data-ttu-id="62bd6-p104">La valeur True ou False. Spécifie si vous avez activé la synchronisation d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="62bd6-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="62bd6-123">**Synchronisation d’annuaire le plus récent**</span><span class="sxs-lookup"><span data-stu-id="62bd6-123">**Latest directory sync**</span></span> | <span data-ttu-id="62bd6-p105">Heure de la dernière exécution de la synchronisation d’annuaire. Affiche un message d’avertissement et un lien vers un outil de dépannage si la dernière synchronisation a plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="62bd6-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="62bd6-126">**Synchronisation de mot de passe activée**</span><span class="sxs-lookup"><span data-stu-id="62bd6-126">**Password sync enabled**</span></span> | <span data-ttu-id="62bd6-p106">La valeur True ou False. Spécifie si vous disposez de synchronisation de hachage de mot de passe entre notre locale et votre client Office 365.</span><span class="sxs-lookup"><span data-stu-id="62bd6-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="62bd6-129">**Dernière synchronisation de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="62bd6-129">**Last Password Sync**</span></span> | <span data-ttu-id="62bd6-p107">Heure de la dernière exécution de la synchronisation de hachage de mot de passe. Affiche un message d’avertissement et un lien vers un outil de dépannage si la dernière synchronisation a plus de trois jours.</span><span class="sxs-lookup"><span data-stu-id="62bd6-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="62bd6-132">**Version de client de synchronisation de répertoire**</span><span class="sxs-lookup"><span data-stu-id="62bd6-132">**Directory sync client version**</span></span> | <span data-ttu-id="62bd6-133">Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée.</span><span class="sxs-lookup"><span data-stu-id="62bd6-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="62bd6-134">**Outil IDFix**</span><span class="sxs-lookup"><span data-stu-id="62bd6-134">**IDFix Tool**</span></span> | <span data-ttu-id="62bd6-135">Télécharger le lien sur [IDFix](install-and-run-idfix.md), un outil qui vous permet de vérifier votre annuaire Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="62bd6-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="62bd6-136">**Compte de service de synchronisation de répertoire**</span><span class="sxs-lookup"><span data-stu-id="62bd6-136">**Directory sync service account**</span></span> | <span data-ttu-id="62bd6-137">Affiche le nom de votre compte de service de synchronisation de répertoire Office 365.</span><span class="sxs-lookup"><span data-stu-id="62bd6-137">Displays the name of you Office 365 directory sync service account.</span></span> |