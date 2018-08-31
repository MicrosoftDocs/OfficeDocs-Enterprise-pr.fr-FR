---
title: Protection des fichiers sensibles dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
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
description: 'Résumé : Configurer et démontrer comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.'
ms.openlocfilehash: d866c8ef9d81ec3a80c466040dab34de8af2c1de
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915699"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="6771c-103">Protection des fichiers sensibles dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="6771c-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="6771c-104">**Résumé :** Configurer et illustrer comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.</span><span class="sxs-lookup"><span data-stu-id="6771c-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="6771c-p101">La Gestion des droits relatifs à l’information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger les documents qui sont téléchargés à partir de listes et bibliothèques SharePoint Online. Les fichiers téléchargés sont chiffrés et contiennent les autorisations d’ouverture, de copie, d’enregistrement et d’impression qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.</span><span class="sxs-lookup"><span data-stu-id="6771c-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="6771c-107">Grâce aux instructions fournies dans cet article, vous activez et testez IRM dans Office 365 pour les fichiers contenant d’éventuelles informations sensibles dans votre abonnement à la version d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="6771c-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="6771c-108">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="6771c-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="6771c-109">Phase 1 : créer votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="6771c-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="6771c-110">Si vous souhaitez simplement tester la protection des fichiers sensibles avec une configuration minimale, suivez les instructions des étapes 2 et 3 de [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6771c-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="6771c-111">Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="6771c-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6771c-p102">Le test de la protection des fichiers sensibles ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection des fichiers sensibles et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="6771c-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="6771c-114">Phase 2 : Démontrez comment une fuite de documents est possible à partir de sites protégés par des autorisations</span><span class="sxs-lookup"><span data-stu-id="6771c-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="6771c-115">Lors de cette phase, vous démontrez qu’une personne peut télécharger un document à partir d’un site protégé par des autorisations, puis le télécharger sur un site disposant d’autorisations élargies.</span><span class="sxs-lookup"><span data-stu-id="6771c-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="6771c-116">Tout d’abord, vous ajoutez trois nouveaux comptes d’utilisateur qui représentent les cadres et vous leur affectez des licences Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="6771c-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="6771c-117">Utilisez les instructions indiquées dans [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (le cas échéant) et de se connecter à votre nouvel abonnement Office 365 à partir de :</span><span class="sxs-lookup"><span data-stu-id="6771c-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="6771c-118">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="6771c-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="6771c-119">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="6771c-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="6771c-120">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez le nom de l’administrateur général Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe de votre abonnement à la version d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="6771c-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="6771c-121">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6771c-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6771c-122">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte CEO et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6771c-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6771c-123">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6771c-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6771c-124">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte CFO et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6771c-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6771c-125">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6771c-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="6771c-126">Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte COO et enregistrez-le dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6771c-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="6771c-127">Ensuite, créez un groupe de cadres privé et ajoutez les nouveaux comptes d’encadrement.</span><span class="sxs-lookup"><span data-stu-id="6771c-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="6771c-128">Dans votre navigateur, accédez au portail Office à [http://portal.office.com](http://portal.office.com) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="6771c-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="6771c-129">Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer ou votre navigateur et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6771c-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="6771c-130">Si vous utilisez l’environnement de développement/test Office 365 avec entreprise simulée, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="6771c-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="6771c-131">Dans l’onglet **Accueil Microsoft Office** , cliquez sur **Administration > Groupes > Groupes**, puis cliquez sur **Ajouter un groupe**.</span><span class="sxs-lookup"><span data-stu-id="6771c-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="6771c-132">Dans **Ajouter un groupe**, sélectionnez **Groupe Office 365** pour le type de groupe, tapez **Cadres** dans **Nom** et **ID de groupe**, sélectionnez **Privé** pour **Confidentialité**, puis cliquez sur **Sélectionner le propriétaire**.</span><span class="sxs-lookup"><span data-stu-id="6771c-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="6771c-133">Dans la liste, cliquez sur le nom de votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="6771c-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="6771c-134">Cliquez sur **Ajouter**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="6771c-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="6771c-135">Dans la liste de groupes, cliquez sur **Cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="6771c-136">Cliquez sur **Modifier pour les membres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="6771c-p103">Cliquez sur **Ajouter des membres**. Dans la liste des membres, sélectionnez les comptes d’utilisateur suivants :</span><span class="sxs-lookup"><span data-stu-id="6771c-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="6771c-139">Directeur général</span><span class="sxs-lookup"><span data-stu-id="6771c-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="6771c-140">Directeur financier</span><span class="sxs-lookup"><span data-stu-id="6771c-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="6771c-141">Directeur des opérations</span><span class="sxs-lookup"><span data-stu-id="6771c-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="6771c-142">Cliquez sur **Enregistrer**, puis sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="6771c-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="6771c-143">Fermez l’onglet **Centre d’administration Office**.</span><span class="sxs-lookup"><span data-stu-id="6771c-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="6771c-144">Ensuite, créez une collection de sites de cadres et autorisez uniquement les membres du groupe de cadres à y accéder.</span><span class="sxs-lookup"><span data-stu-id="6771c-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="6771c-145">Dans l’onglet **Accueil Microsoft Office**, cliquez sur la mosaïque **Admin**.</span><span class="sxs-lookup"><span data-stu-id="6771c-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="6771c-146">Dans l’onglet **Centre d’administration d’Office** , cliquez sur **centres d’administration > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="6771c-147">Dans l’onglet **Centre d’administration SharePoint** , cliquez sur **Nouveau > collection de sites privée**.</span><span class="sxs-lookup"><span data-stu-id="6771c-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="6771c-148">Dans le volet nouvelle collection de sites, tapez **cadres** dans **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d’administrateur général dans **administrateur**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6771c-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="6771c-p104">Attendez que la nouvelle collection de sites a été créée. Lorsque vous avez terminé, copiez l’URL de la nouvelle collection de sites responsables et collez-le dans un nouvel onglet de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="6771c-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="6771c-151">Dans le coin supérieur droit de la collection de sites **Cadres**, cliquez sur l’icône des paramètres, puis cliquez sur **Partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="6771c-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="6771c-152">Dans **partage de « Responsables »**, cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="6771c-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="6771c-153">Dans la liste des groupes SharePoint, cliquez sur **Membres de cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="6771c-154">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="6771c-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="6771c-155">Dans **partage de « Responsables »**, tapez **cadres**, cliquez sur le groupe de **cadres** , puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="6771c-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="6771c-156">Fermez l’onglet **personnes et groupes** .</span><span class="sxs-lookup"><span data-stu-id="6771c-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="6771c-157">Ensuite, autorisez tout le monde à accéder à la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="6771c-158">Sous l’onglet **Centre d’administration SharePoint** , copiez l’URL de la collection de sites ventes et collez-le dans un nouvel onglet de votre navigateur...</span><span class="sxs-lookup"><span data-stu-id="6771c-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="6771c-159">Dans le coin supérieur droit, cliquez sur l’icône Paramètres, puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="6771c-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="6771c-160">Dans **partage de « Collection de sites ventes »**, cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="6771c-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="6771c-161">Dans la liste des groupes SharePoint, cliquez sur **Membres de la collection de sites de ventes**.</span><span class="sxs-lookup"><span data-stu-id="6771c-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="6771c-162">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="6771c-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="6771c-163">Dans **partage de « Collection de sites ventes »**, tapez **tout le monde**, cliquez sur **tout le monde, à l’exception des utilisateurs externes**, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="6771c-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="6771c-164">Fermez les onglets **Collection de sites de ventes** et **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6771c-165">Ensuite, connectez-vous avec un compte de cadre et créez un document dans la collection de sites Cadres.</span><span class="sxs-lookup"><span data-stu-id="6771c-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="6771c-166">Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="6771c-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6771c-167">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6771c-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6771c-168">Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="6771c-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="6771c-169">Entrez le nom du compte **CEO** et le mot de passe associé, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6771c-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="6771c-170">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="6771c-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="6771c-171">Cliquez sur **Documents**et cliquez sur **Nouveau,** puis cliquez sur **Document Word**.</span><span class="sxs-lookup"><span data-stu-id="6771c-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="6771c-172">Cliquez dans la barre de titre et tapez **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="6771c-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="6771c-173">Cliquez dans le corps du document et tapez **Compte-rendu du dernier conseil d’administration**, puis cliquez sur **Cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="6771c-174"> Vous devriez voir **SensitiveData-BeforeIRM.docx** dans le dossier **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="6771c-175">Ensuite, vous téléchargez une copie locale du document SensitiveData-BeforeIRM.docx et la publiez accidentellement dans la collection de sites Ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="6771c-176">Sur votre ordinateur local, créez un nouveau dossier (par exemple, c :\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="6771c-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="6771c-177">Dans l’onglet **Documents** de votre navigateur, sélectionnez le document **SensitiveData-BeforeIRM.docx** et cliquez sur les points de suspension, puis sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="6771c-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="6771c-178">Rangez le document **SensitiveData-BeforeIRM.docx** dans le dossier créé dans l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="6771c-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="6771c-179">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="6771c-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="6771c-180">Cliquez sur le dossier **Documents** de la **collection de sites de ventes**.</span><span class="sxs-lookup"><span data-stu-id="6771c-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="6771c-181">Cliquez sur **Télécharger**, puis spécifiez le document **SensitiveData-BeforeIRM.docx** dans le dossier créé à l’étape 1, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6771c-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="6771c-182">Vérifiez que le document **SensitiveData-BeforeIRM.docx** se trouve dans le dossier **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="6771c-183">Fermez les onglets **Ventes** et **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6771c-184">Ensuite, connectez-vous en tant que Utilisateur 5 et essayez d’ouvrir le document SensitiveData-BeforeIRM.docx dans la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="6771c-185">Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="6771c-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6771c-186">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6771c-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6771c-187">Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="6771c-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="6771c-188">Entrez le nom du compte Utilisateur 5 et le mot de passe associé, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6771c-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="6771c-189">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="6771c-190">Dans le dossier **Documents** de la **Collection de sites de ventes**, cliquez sur le document **SensitiveData-BeforeIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="6771c-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="6771c-191">Vous devriez voir son contenu.</span><span class="sxs-lookup"><span data-stu-id="6771c-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="6771c-192">Fermez les onglets **Documents** et **Collection de sites de ventes**.</span><span class="sxs-lookup"><span data-stu-id="6771c-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="6771c-193">En publiant accidentellement le document SensitiveData-BeforeIRM.docx sur la collection de sites de ventes, le directeur général a ignoré la sécurité des autorisations de la collection de sites Cadres.</span><span class="sxs-lookup"><span data-stu-id="6771c-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="6771c-194">Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6771c-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="6771c-195">Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="6771c-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6771c-196">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6771c-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6771c-197">Sur la page **Connexion à Office 365**, cliquez sur le nom de compte de l’administrateur général, tapez son mot de passe, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6771c-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="6771c-198">Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Administrateur > Centres d’administration > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="6771c-199">Dans l’onglet **Centre d’administration SharePoint**, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="6771c-200">Sur la page **Paramètres**, dans la section **Gestion des droits relatifs à l’information (IRM)**, sélectionnez **Utiliser le service IRM spécifié dans votre configuration**, puis sélectionnez **Actualiser les paramètres IRM**.</span><span class="sxs-lookup"><span data-stu-id="6771c-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="6771c-201">Fermez l’onglet **Centre d’administration SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="6771c-202">Phase 3 : Utiliser la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6771c-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="6771c-203">Lors de cette phase, vous utilisez la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365 pour protéger l’accès à un document contenant des informations sensibles, même lorsqu’il est publié sur un site avec des autorisations d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="6771c-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="6771c-204">Tout d’abord, vous activez et configurez IRM pour la bibliothèque de documents de la collection de sites Cadres. </span><span class="sxs-lookup"><span data-stu-id="6771c-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="6771c-205">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.</span><span class="sxs-lookup"><span data-stu-id="6771c-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="6771c-206">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="6771c-207">Dans le coin supérieur droit, cliquez sur l’icône des paramètres, puis sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="6771c-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="6771c-208">Sur la page **Paramètres**, sous **Autorisations et gestion**, cliquez sur **Gestion des droits relatifs à l’information**.</span><span class="sxs-lookup"><span data-stu-id="6771c-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="6771c-209">Dans la page **Paramètres de gestion des droits relatifs à l’information** :</span><span class="sxs-lookup"><span data-stu-id="6771c-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="6771c-210">Sélectionnez **Restreindre l’accès aux documents de cette bibliothèque au téléchargement**.</span><span class="sxs-lookup"><span data-stu-id="6771c-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="6771c-211">Pour **Créer un titre de la stratégie d’autorisation**, tapez **Cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="6771c-212">Pour **Ajouter une description de la stratégie d’autorisation**, tapez **IRM pour les cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="6771c-213">Cliquez sur **Afficher les options**.</span><span class="sxs-lookup"><span data-stu-id="6771c-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="6771c-214">Sous **Définir d’autres paramètres de la bibliothèque IRM**, sélectionnez **Ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge IRM**.</span><span class="sxs-lookup"><span data-stu-id="6771c-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="6771c-215">Sous **Configurer les droits d’accès aux documents**, sélectionnez **Autoriser les utilisateurs à imprimer** et **Autoriser les utilisateurs à écrire sur une copie du document téléchargé**.</span><span class="sxs-lookup"><span data-stu-id="6771c-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="6771c-216">Sous **Définir la protection de groupe et l’intervalle d’informations d’identification**, sélectionnez **Autoriser la protection de groupe** et pour **Groupe par défaut**, tapez **Cadres**.</span><span class="sxs-lookup"><span data-stu-id="6771c-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="6771c-217">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6771c-217">Click **OK**.</span></span>
    
<span data-ttu-id="6771c-218">Ensuite, en jouant le rôle du directeur général, vous chargez un nouveau document dans le dossier de documents Cadres, le téléchargez, puis le chargez accidentellement dans le dossier de documents Ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="6771c-219">Ouvrez le dossier local où est stocké le document **SensitiveData-BeforeIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="6771c-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="6771c-220">	Cliquez avec le bouton droit sur **SensitiveData-BeforeIRM.docx**, puis cliquez sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="6771c-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="6771c-221">Cliquez avec le bouton droit dans le dossier, puis cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="6771c-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="6771c-222">Renommez le nouveau fichier **SensitiveData-BeforeIRM - Copy.docx** **- AfterIRM.docx SensitiveData**.</span><span class="sxs-lookup"><span data-stu-id="6771c-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="6771c-223">Dans l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="6771c-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="6771c-224">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6771c-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="6771c-225">Sur la page **Connexion à Office 365**, cliquez sur le nom du compte CEO, tapez son mot de passe, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6771c-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="6771c-226">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.</span><span class="sxs-lookup"><span data-stu-id="6771c-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="6771c-227">Sur la page **Documents**, cliquez sur **Charger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="6771c-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="6771c-228">Sélectionnez le nouveau document **SensitiveData-AfterIRM.docx** dans la page **Documents** et cliquez sur les points de suspension (...) dans la barre de menus, puis cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="6771c-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="6771c-229">Lorsque vous y êtes invité, enregistrez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, en remplaçant la version d’origine.</span><span class="sxs-lookup"><span data-stu-id="6771c-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="6771c-230">Fermez l’onglet de la page **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="6771c-231">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="6771c-232">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="6771c-233">Sur la page **Documents**, cliquez sur **Charger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="6771c-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="6771c-234">Fermez les onglets **Collection de sites de ventes** et **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6771c-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="6771c-235">Ensuite, en tant qu’utilisateur normal, essayez d’accéder au document **SensitiveData-AfterIRM.docx** dans le dossier de documents Ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="6771c-236">Dans l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="6771c-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="6771c-237">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="6771c-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="6771c-238">Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5, tapez son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6771c-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="6771c-239">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.</span><span class="sxs-lookup"><span data-stu-id="6771c-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="6771c-240">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="6771c-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="6771c-241">Sur la page **Documents**, ouvrez le document **SensitiveData-AfterIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="6771c-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="6771c-242">Vous devez voir un message indiquant « Désolé, Word Online ne peut pas ouvrir ce document, car il est protégé par la Gestion des droits relatifs à l’information (IRM). » </span><span class="sxs-lookup"><span data-stu-id="6771c-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="6771c-p105">Cliquez sur **Modifier dans Word**. Vous êtes invité à indiquer si vous souhaitez ouvrir le fichier. Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="6771c-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="6771c-p106">Vous êtes invité à vous connecter. Tapez le nom du compte Utilisateur 5, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="6771c-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="6771c-p107">Vous êtes invité à fournir le mot de passe. Tapez le mot de passe du compte Utilisateur 5, puis cliquez sur **Se connecter**. </span><span class="sxs-lookup"><span data-stu-id="6771c-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="6771c-250">Vous devez voir un message indiquant ce qui suit : « Vous ne disposez pas des informations d’identification requises pour ouvrir ce document. »</span><span class="sxs-lookup"><span data-stu-id="6771c-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="6771c-251">Cliquez sur **Non**.</span><span class="sxs-lookup"><span data-stu-id="6771c-251">Click **No**.</span></span>
    
<span data-ttu-id="6771c-p108">Pour afficher la protection IRM, vous pouvez également examiner les fichiers dans votre dossier local. Le fichier **SensitiveData-AfterIRM.docx** doit être beaucoup plus volumineux que le fichier **SensitiveData-BeforeIRM.docx**. Le fichier **SensitiveData-AfterIRM.docx** est chiffré et contient les informations sur la protection IRM.</span><span class="sxs-lookup"><span data-stu-id="6771c-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6771c-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6771c-255">See Also</span></span>

[<span data-ttu-id="6771c-256">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="6771c-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="6771c-257">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="6771c-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="6771c-258">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="6771c-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="6771c-259">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="6771c-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


