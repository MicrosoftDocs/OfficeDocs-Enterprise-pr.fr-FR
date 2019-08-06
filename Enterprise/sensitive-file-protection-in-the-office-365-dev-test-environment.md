---
title: Protection des fichiers sensibles dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Résumé: configurez et montrez comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu’ils sont publiés dans une collection de sites SharePoint Online incorrecte.'
ms.openlocfilehash: 9608bf68ced2f286f788dd94dfc27755f5ff23c0
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782494"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="bf0a0-103">Protection des fichiers sensibles dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="bf0a0-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="bf0a0-104">**Résumé:** Configurez et montrez comment Office 365 Information Rights Management protège vos fichiers sensibles, même s’ils sont publiés dans une collection de sites SharePoint Online incorrecte.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="bf0a0-105">La gestion des droits relatifs à l’information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger des documents qui sont téléchargés à partir de bibliothèques et de listes SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-105">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists.</span></span> <span data-ttu-id="bf0a0-106">Les fichiers téléchargés sont chiffrés et contiennent les autorisations ouvrir, copier, enregistrer et imprimer qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-106">Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="bf0a0-107">Les instructions de cet article vous permettent d’activer et de tester la gestion des droits relatifs à l’information (IRM) dans Office 365 pour les fichiers contenant des informations sensibles possibles dans votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="bf0a0-108">Cliquez sur[ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="bf0a0-109">Phase 1: créer votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="bf0a0-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="bf0a0-110">Si vous souhaitez simplement tester la protection des fichiers sensibles avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="bf0a0-111">Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="bf0a0-112">Le test de la protection des fichiers sensibles ne nécessite pas l’environnement de développement/test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="bf0a0-113">Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des fichiers sensibles et de l’expérimenter dans un environnement qui représente une organisation typique.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="bf0a0-114">Phase 2: montrer comment les documents provenant de sites protégés par des autorisations peuvent être divulgués</span><span class="sxs-lookup"><span data-stu-id="bf0a0-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="bf0a0-115">Dans cette phase, vous démontrez qu’une personne peut télécharger un document à partir d’un site protégé par des autorisations, puis le télécharger vers un site disposant d’autorisations étendues.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="bf0a0-116">Tout d’abord, vous ajoutez trois nouveaux comptes d’utilisateur qui représentent les cadres et affectez-leur des licences Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="bf0a0-117">Suivez les instructions de la procédure [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (si nécessaire) et vous connecter à votre nouvel abonnement Office 365 à partir de:</span><span class="sxs-lookup"><span data-stu-id="bf0a0-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="bf0a0-118">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="bf0a0-119">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="bf0a0-120">Dans la boîte de dialogue **demande d’informations d’identification Windows PowerShell** , tapez le nom de l’administrateur général Office 365 (par exemple: jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe de votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="bf0a0-121">Renseignez le nom de votre organisation (par exemple: contosotoycompany) et le code pays à deux caractères pour votre emplacement, puis exécutez les commandes suivantes à partir de l’invite module Windows Azure Active Directory pour Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bf0a0-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="bf0a0-122">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte PDG et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="bf0a0-123">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="bf0a0-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="bf0a0-124">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte directeur financier et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="bf0a0-125">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="bf0a0-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="bf0a0-126">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte directeur de directeur de sécurité et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="bf0a0-127">Ensuite, créez un groupe de cadres privés et ajoutez-y les nouveaux comptes exécutifs.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="bf0a0-128">Dans votre navigateur, accédez au portail Office [http://admin.microsoft.com](http://admin.microsoft.com) et connectez-vous à votre abonnement d’évaluation Office 365 avec votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="bf0a0-129">Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer ou de votre navigateur, puis connectez-vous à partir de votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="bf0a0-130">Si vous utilisez l’environnement de développement/test Office 365 entreprise simulé, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="bf0a0-131">Dans l’onglet **Accueil Microsoft Office** , cliquez sur **administrateurs > groupes > groupes**, puis cliquez sur **Ajouter un groupe**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="bf0a0-132">Dans **Ajouter un groupe**, sélectionnez **groupe Office 365** pour le type de groupe, tapez **cadres** dans **nom** et **ID de groupe**, sélectionnez **privé** pour la **confidentialité**, puis cliquez sur **Sélectionner le propriétaire**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="bf0a0-133">Dans la liste, cliquez sur le nom de votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="bf0a0-134">Cliquez sur **Ajouter**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="bf0a0-135">Dans la liste des groupes, cliquez sur **cadres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="bf0a0-136">Cliquez sur **Modifier pour les membres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="bf0a0-137">Cliquez sur **Ajouter des membres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-137">Click **Add members**.</span></span> <span data-ttu-id="bf0a0-138">Dans la liste des membres, sélectionnez les comptes d’utilisateur suivants:</span><span class="sxs-lookup"><span data-stu-id="bf0a0-138">In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="bf0a0-139">Directeur général</span><span class="sxs-lookup"><span data-stu-id="bf0a0-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="bf0a0-140">Directeur financier</span><span class="sxs-lookup"><span data-stu-id="bf0a0-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="bf0a0-141">Directeur des opérations</span><span class="sxs-lookup"><span data-stu-id="bf0a0-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="bf0a0-142">Cliquez sur **Enregistrer**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="bf0a0-143">Fermez l’onglet **Centre d’administration Office** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="bf0a0-144">Ensuite, vous créez une collection de sites Executives et autorisez uniquement les membres du groupe cadres à y accéder.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="bf0a0-145">Dans l’onglet **Accueil Microsoft Office** , cliquez sur la vignette **administrateur** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="bf0a0-146">Dans l’onglet **Centre d’administration Office** , cliquez sur centres d’administration **> SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="bf0a0-147">Dans l’onglet **Centre d’administration SharePoint** , cliquez sur **nouvelle > collection de sites privée**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="bf0a0-148">Dans le volet nouvelle collection de sites, tapez **cadres** dans **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d’administrateur général dans **administrateur**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="bf0a0-149">Patientez jusqu’à ce que la collection de sites ait été créée.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="bf0a0-150">Lorsque vous avez terminé, copiez l’URL de la nouvelle collection de sites Executives et collez-la dans un nouvel onglet de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="bf0a0-151">Dans le coin supérieur droit de la collection de sites **cadres** , cliquez sur l’icône des paramètres, puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="bf0a0-152">Dans **partager «cadres»**, cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="bf0a0-153">Dans la liste des groupes SharePoint, cliquez sur membres de la **direction**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="bf0a0-154">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="bf0a0-155">Dans **partager «cadres»**, tapez **cadres**, cliquez sur le groupe **cadres** , puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="bf0a0-156">Fermez l’onglet **personnes et groupes** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="bf0a0-157">Ensuite, vous autorisez tout le monde à accéder à la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="bf0a0-158">À partir de l’onglet **Centre d’administration SharePoint** , copiez l’URL de la collection de sites de ventes et collez-la dans un nouvel onglet de votre navigateur..</span><span class="sxs-lookup"><span data-stu-id="bf0a0-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="bf0a0-159">Dans le coin supérieur droit, cliquez sur l’icône des paramètres, puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="bf0a0-160">Dans **partager «collection de sites de ventes»**, cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="bf0a0-161">Dans la liste des groupes SharePoint, cliquez sur membres de la **collection de sites de ventes**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="bf0a0-162">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="bf0a0-163">Dans **partager «collection de sites de ventes»**, tapez **tout le monde**, cliquez sur **tout le monde sauf les utilisateurs externes**, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="bf0a0-164">Fermez les onglets **collection de sites de ventes** et **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="bf0a0-165">Ensuite, connectez-vous avec un compte exécutif et créez un document dans la collection de sites cadres.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="bf0a0-166">Dans l’onglet **Accueil Microsoft Office** , cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, \*\*\*\* puis cliquez sur Déconnexion.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bf0a0-167">Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="bf0a0-168">Sur la page **de connexion à Office 365** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="bf0a0-169">Tapez le nom du compte **PDG** et son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="bf0a0-170">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites cadres (>**https://**\< **. SharePoint.com/sites/Executives**).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="bf0a0-171">Cliquez sur **documents**, sur **nouveau,** puis sur **document Word**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="bf0a0-172">Cliquez dans la barre de titre et tapez **sensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="bf0a0-173">Cliquez dans le corps du document et tapez le compte- **rendu de la dernière réunion**, puis cliquez sur **cadres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="bf0a0-174">Vous devriez voir **sensitiveData-beforeirm. docx** dans le dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="bf0a0-175">Ensuite, téléchargez une copie locale du document sensitiveData-beforeirm. docx, puis publiez-le accidentellement dans la collection de sites Sales.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="bf0a0-176">Sur votre ordinateur local, créez un dossier (par exemple, C:\\guides\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="bf0a0-177">Dans l’onglet **documents** de votre navigateur, sélectionnez le document **sensitiveData-beforeirm. docx** , cliquez sur les ellipses, puis cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="bf0a0-178">Stockez le document **sensitiveData-beforeirm. docx** dans le dossier créé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="bf0a0-179">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de \*\*\*\*\<vente (>https:// **. SharePoint.com/sites/Sales**).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="bf0a0-180">Cliquez sur le dossier **documents** de la **collection de sites de ventes**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="bf0a0-181">Cliquez sur **Télécharger**, puis spécifiez **sensitiveData-beforeirm. docx** dans le dossier créé à l’étape 1, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="bf0a0-182">Vérifiez que le document **sensitiveData-beforeirm. docx** se trouve dans le dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="bf0a0-183">Fermez les onglets **ventes** et **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="bf0a0-184">Ensuite, connectez-vous en tant que utilisateur 5 et essayez d’ouvrir le document sensitiveData-beforeirm. docx dans la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="bf0a0-185">Dans l’onglet **Accueil Microsoft Office** , cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, \*\*\*\* puis cliquez sur Déconnexion.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bf0a0-186">Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="bf0a0-187">Sur la page **de connexion à Office 365** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="bf0a0-188">Tapez le nom du compte utilisateur 5 et son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="bf0a0-189">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="bf0a0-190">Dans le dossier **documents** de la **collection de sites de ventes**, cliquez sur le **sensitiveData-beforeirm. docx** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="bf0a0-191">Vous devriez voir son contenu.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="bf0a0-192">Fermez les onglets **documents** et **collection de sites de ventes** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="bf0a0-193">En publiant accidentellement le document sensitiveData-beforeirm. docx sur la collection de sites de ventes, le PDG a contourné la sécurité des autorisations de la collection de sites cadres.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="bf0a0-194">Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="bf0a0-195">Dans l’onglet **Accueil Microsoft Office** , cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, \*\*\*\* puis cliquez sur Déconnexion.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bf0a0-196">Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="bf0a0-197">Sur la page **de connexion Office 365** , cliquez sur le nom du compte d’administrateur général, tapez son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="bf0a0-198">Dans l’onglet **Accueil Microsoft Office** , cliquez sur **centres d’administration > administrateur > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="bf0a0-199">Dans l’onglet **Centre d’administration SharePoint** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="bf0a0-200">Dans la page, dans la section gestion des droits relatifs à l' **information (IRM)** , sélectionnez **utiliser le service IRM spécifié dans votre configuration**, puis actualiser les **paramètres IRM**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="bf0a0-201">Fermez l’onglet **Centre d’administration SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="bf0a0-202">Phase 3: utiliser la gestion des droits relatifs à l’information (IRM) SharePoint avec un groupe privé Office 365</span><span class="sxs-lookup"><span data-stu-id="bf0a0-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="bf0a0-203">Dans cette phase, vous utilisez la gestion des droits relatifs à l’information (IRM) de SharePoint avec un groupe privé Office 365 pour protéger l’accès à un document avec des informations sensibles, même s’il est publié sur un site avec des autorisations ouvertes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="bf0a0-204">Tout d’abord, vous activez et configurez la gestion des droits relatifs à l’information pour la bibliothèque de documents de la collection de sites cadres.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="bf0a0-205">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites cadres.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="bf0a0-206">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="bf0a0-207">Dans le coin supérieur droit, cliquez sur l’icône Paramètres, puis cliquez sur paramètres de la **bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="bf0a0-208">Sur la page **paramètres** , sous **autorisations et gestion**, cliquez sur **gestion des droits relatifs**à l’information.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="bf0a0-209">Sur la page **paramètres de gestion des droits relatifs** à l’information:</span><span class="sxs-lookup"><span data-stu-id="bf0a0-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="bf0a0-210">Sélectionnez **restreindre l’autorisation aux documents de cette bibliothèque au téléchargement**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="bf0a0-211">Pour **créer un titre de stratégie d’autorisation**, tapez **dirigeants**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="bf0a0-212">Pour **Ajouter une description de stratégie d’autorisation**, tapez **IRM pour les cadres**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="bf0a0-213">Cliquez sur **Afficher les options**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="bf0a0-214">Sous **définir d’autres paramètres de la bibliothèque IRM**, sélectionnez **ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge IRM**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="bf0a0-215">Sous **configurer les droits d’accès au document**, sélectionnez **autoriser les visualiseurs à imprimer** et **autoriser les utilisateurs à écrire sur une copie du document téléchargé**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="bf0a0-216">Sous **définir la protection de groupe et l’intervalle des informations d’identification**, sélectionnez **autoriser la protection de groupe. Groupe par défaut**, puis tapez **Executives**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="bf0a0-217">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-217">Click **OK**.</span></span>
    
<span data-ttu-id="bf0a0-218">Ensuite, en tant que PDG, vous chargez un nouveau document dans le dossier de documents cadres, le télécharger, puis le charger accidentellement dans le dossier des documents de vente.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="bf0a0-219">Ouvrez le dossier local dans lequel vous avez stocké le document **sensitiveData-beforeirm. docx** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="bf0a0-220">Cliquez avec le bouton droit sur **sensitiveData-beforeirm. docx**, puis cliquez sur **copier**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="bf0a0-221">Cliquez avec le bouton droit dans le dossier, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="bf0a0-222">Renommez le nouveau fichier **sensitiveData-BeforeIRM-Copy. docx** en **sensitiveData-AfterIRM. docx**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="bf0a0-223">À partir de l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur \*\*\*\* droit, puis cliquez sur Déconnexion.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="bf0a0-224">Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="bf0a0-225">Sur la page **de connexion à Office 365** , cliquez sur le nom du compte PDG, tapez son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="bf0a0-226">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites cadres.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="bf0a0-227">Sur la page **documents** , cliquez sur **charger**, spécifiez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="bf0a0-228">Sélectionnez le nouveau document **sensitiveData-AfterIRM. docx** dans la page **documents** , cliquez sur les points de suspension (...) dans la barre de menus, puis cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="bf0a0-229">Lorsque vous y êtes invité, enregistrez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, en remplaçant la version d’origine.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="bf0a0-230">Fermez l’onglet de la page **documents** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="bf0a0-231">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="bf0a0-232">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="bf0a0-233">Sur la page **documents** , cliquez sur **charger**, spécifiez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="bf0a0-234">Fermez les onglets **collection de sites de ventes** et **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="bf0a0-235">Ensuite, en tant qu’utilisateur normal, vous tentez d’accéder au document **sensitiveData-AfterIRM. docx** dans le dossier Sales document.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="bf0a0-236">À partir de l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur \*\*\*\* droit, puis cliquez sur Déconnexion.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bf0a0-237">Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf0a0-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="bf0a0-238">Sur la page **de connexion à Office 365** , cliquez sur le nom du compte utilisateur 5, tapez son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="bf0a0-239">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="bf0a0-240">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="bf0a0-241">Sur la page **documents** , ouvrez le document **sensitiveData-AfterIRM. docx** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="bf0a0-242">Un message indiquant «Désolé, Word ne peut pas ouvrir ce document s’affiche car il est protégé par la gestion des droits relatifs à l’information (IRM).»</span><span class="sxs-lookup"><span data-stu-id="bf0a0-242">You should see a message that states, "Sorry, Word can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="bf0a0-243">Cliquez sur **modifier dans Word**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-243">Click **Edit in Word**.</span></span> <span data-ttu-id="bf0a0-244">Vous êtes invité à indiquer si vous souhaitez ouvrir le fichier.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-244">You are prompted if you want to open the file.</span></span> <span data-ttu-id="bf0a0-245">Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-245">Click **Yes**.</span></span>
    
8. <span data-ttu-id="bf0a0-246">Vous êtes invité à vous connecter.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-246">You are prompted to sign-in.</span></span> <span data-ttu-id="bf0a0-247">Tapez le nom de compte du compte utilisateur 5, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-247">Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="bf0a0-248">Vous êtes invité à fournir le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-248">You are prompted to provide the password.</span></span> <span data-ttu-id="bf0a0-249">Tapez le mot de passe du compte utilisateur 5, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-249">Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="bf0a0-250">Le message suivant doit s’afficher: «vous ne disposez pas des informations d’identification qui vous permettent d’ouvrir ce document».</span><span class="sxs-lookup"><span data-stu-id="bf0a0-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="bf0a0-251">Cliquez sur **non**.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-251">Click **No**.</span></span>
    
<span data-ttu-id="bf0a0-252">Une autre façon d’afficher la protection IRM consiste à examiner les fichiers figurant dans votre dossier local.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-252">Another way to see the IRM protection is to look at the files in your local folder.</span></span> <span data-ttu-id="bf0a0-253">**SensitiveData-AfterIRM. docx** doit être plus volumineux que le fichier **sensitiveData-beforeirm. docx** .</span><span class="sxs-lookup"><span data-stu-id="bf0a0-253">The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file.</span></span> <span data-ttu-id="bf0a0-254">Le fichier **sensitiveData-AfterIRM. docx** est chiffré et les informations de protection IRM sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="bf0a0-254">The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf0a0-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf0a0-255">See Also</span></span>

[<span data-ttu-id="bf0a0-256">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="bf0a0-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="bf0a0-257">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="bf0a0-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="bf0a0-258">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="bf0a0-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="bf0a0-259">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="bf0a0-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


