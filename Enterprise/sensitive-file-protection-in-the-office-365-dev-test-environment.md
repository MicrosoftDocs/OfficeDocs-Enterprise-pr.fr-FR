---
title: "Protection des fichiers sensibles dans l’environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Résumé : Configuration et montrez comment Information Rights Management d’Office 365 protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte."
ms.openlocfilehash: 236272a90bb6ff7f310c95f1494b68750e363f40
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="12f25-103">Protection des fichiers sensibles dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="12f25-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="12f25-104">**Résumé :** Configurer et illustrer comment Information Rights Management d’Office 365 protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.</span><span class="sxs-lookup"><span data-stu-id="12f25-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="12f25-p101">La Gestion des droits relatifs à l’information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger les documents qui sont téléchargés à partir de listes et bibliothèques SharePoint Online. Les fichiers téléchargés sont chiffrés et contiennent les autorisations d’ouverture, de copie, d’enregistrement et d’impression qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.</span><span class="sxs-lookup"><span data-stu-id="12f25-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="12f25-107">Grâce aux instructions fournies dans cet article, vous activez et testez IRM dans Office 365 pour les fichiers contenant d’éventuelles informations sensibles dans votre abonnement à la version d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="12f25-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="12f25-108">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="12f25-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="12f25-109">Phase 1 : créer votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="12f25-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="12f25-110">Si vous souhaitez juste tester la protection des fichiers sensibles de façon légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="12f25-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="12f25-111">Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="12f25-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="12f25-p102">Le test de la protection des fichiers sensibles ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection des fichiers sensibles et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="12f25-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="12f25-114">Phase 2 : Démontrez comment une fuite de documents est possible à partir de sites protégés par des autorisations</span><span class="sxs-lookup"><span data-stu-id="12f25-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="12f25-115">Lors de cette phase, vous démontrez qu’une personne peut télécharger un document à partir d’un site protégé par des autorisations, puis le télécharger sur un site disposant d’autorisations élargies.</span><span class="sxs-lookup"><span data-stu-id="12f25-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="12f25-116">Tout d’abord, vous ajoutez trois nouveaux comptes d’utilisateur qui représentent les cadres et vous leur affectez des licences Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="12f25-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="12f25-117">Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (si nécessaire) et de vous connecter à votre nouvel abonnement Office 365 à partir de :</span><span class="sxs-lookup"><span data-stu-id="12f25-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="12f25-118">Votre ordinateur (pour l’environnement de développement/test Office 365 léger).</span><span class="sxs-lookup"><span data-stu-id="12f25-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="12f25-119">La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).</span><span class="sxs-lookup"><span data-stu-id="12f25-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="12f25-120">Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe de votre abonnement d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="12f25-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="12f25-121">Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="12f25-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12f25-122">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur général et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="12f25-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12f25-123">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="12f25-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12f25-124">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur financier et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="12f25-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12f25-125">Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="12f25-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12f25-126">À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur des opérations et l’enregistrer dans un emplacement sûr.</span><span class="sxs-lookup"><span data-stu-id="12f25-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12f25-127">Ensuite, créez un groupe de cadres privé et ajoutez les nouveaux comptes d’encadrement.</span><span class="sxs-lookup"><span data-stu-id="12f25-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="12f25-128">Dans votre navigateur, accédez au portail Office à [http://portal.office.com](http://portal.office.com) et connectez-vous à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="12f25-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="12f25-129">Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer ou votre navigateur et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="12f25-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="12f25-130">Si vous utilisez l’environnement de développement/test Office 365 avec entreprise simulée, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="12f25-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="12f25-131">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin > groupes > groupes de**, puis cliquez sur **Ajouter un groupe**.</span><span class="sxs-lookup"><span data-stu-id="12f25-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="12f25-132">Dans **Ajouter un groupe**, sélectionnez **groupe d’Office 365** pour le type de groupe tapez **dirigeants** dans le **nom** et l' **Id de groupe**, sélectionnez **privé** pour la **confidentialité**, puis cliquez sur **Sélectionner un propriétaire**.</span><span class="sxs-lookup"><span data-stu-id="12f25-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="12f25-133">Dans la liste, cliquez sur le nom de votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="12f25-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="12f25-134">Cliquez sur **Ajouter**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="12f25-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="12f25-135">Dans la liste groupes, cliquez sur **cadres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="12f25-136">Cliquez sur **Modifier pour les membres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="12f25-p103">Cliquez sur **Ajouter des membres**. Dans la liste des membres, sélectionnez les comptes d’utilisateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="12f25-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="12f25-139">Directeur général</span><span class="sxs-lookup"><span data-stu-id="12f25-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="12f25-140">Directeur financier</span><span class="sxs-lookup"><span data-stu-id="12f25-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="12f25-141">Directeur des opérations</span><span class="sxs-lookup"><span data-stu-id="12f25-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="12f25-142">Cliquez sur **Enregistrer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="12f25-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="12f25-143">Fermez l’onglet **Centre d’administration de l’Office** .</span><span class="sxs-lookup"><span data-stu-id="12f25-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="12f25-144">Ensuite, créez une collection de sites de cadres et autorisez uniquement les membres du groupe de cadres à y accéder.</span><span class="sxs-lookup"><span data-stu-id="12f25-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="12f25-145">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="12f25-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="12f25-146">Dans l’onglet **Centre d’administration d’Office** , cliquez sur **Centre d’administration > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="12f25-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="12f25-147">Dans l’onglet **Centre d’administration de SharePoint** , cliquez sur **Nouveau > collection de sites privé**.</span><span class="sxs-lookup"><span data-stu-id="12f25-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="12f25-148">Dans le nouveau volet de collection de sites, tapez **dirigeants** dans le **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d’administrateur global dans **l’administrateur**et puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="12f25-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="12f25-p104">Attendez que la nouvelle collection de site a été créée. Lorsque vous avez terminé, copiez l’URL de la collection de sites de cadres et les coller dans un nouvel onglet de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="12f25-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="12f25-151">Dans le coin supérieur droit de la collection de sites de **cadres** , cliquez sur l’icône de paramètres, puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="12f25-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="12f25-152">Dans **partage 'Dirigeants'**, cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="12f25-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="12f25-153">Dans la liste des groupes SharePoint, cliquez sur **Membres de la direction**.</span><span class="sxs-lookup"><span data-stu-id="12f25-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="12f25-154">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="12f25-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="12f25-155">Dans **partage 'Dirigeants'**, tapez des **cadres**, cliquez sur le groupe de **cadres** , puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="12f25-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="12f25-156">Fermez l’onglet **personnes et groupes** .</span><span class="sxs-lookup"><span data-stu-id="12f25-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="12f25-157">Ensuite, autorisez tout le monde à accéder à la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="12f25-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="12f25-158">Dans l’onglet **Centre d’administration SharePoint** , copiez l’URL de la collection de sites de vente et le coller dans un nouvel onglet de votre navigateur...</span><span class="sxs-lookup"><span data-stu-id="12f25-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="12f25-159">Dans le coin supérieur droit, cliquez sur l’icône de paramètres, puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="12f25-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="12f25-160">Dans **partage « Collection de sites ventes »**, cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="12f25-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="12f25-161">Dans la liste des groupes SharePoint, cliquez sur **membres de collection de sites de vente**.</span><span class="sxs-lookup"><span data-stu-id="12f25-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="12f25-162">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="12f25-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="12f25-163">Dans **partage « Collection de sites de vente »**, tapez **tout le monde**, cliquez sur **tout le monde excepté les utilisateurs externes**, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="12f25-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="12f25-164">Fermer les onglets de la **collection de sites de vente** et de **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="12f25-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12f25-165">Ensuite, connectez-vous avec un compte de cadre et créez un document dans la collection de sites Cadres.</span><span class="sxs-lookup"><span data-stu-id="12f25-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="12f25-166">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12f25-167">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="12f25-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12f25-168">Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="12f25-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="12f25-169">Tapez le nom du compte **PDG** et son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="12f25-170">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="12f25-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="12f25-171">Cliquez sur **Documents**et cliquez sur **Nouveau,** puis cliquez sur **Document Word**.</span><span class="sxs-lookup"><span data-stu-id="12f25-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="12f25-172">Cliquez sur dans la barre de titre, tapez **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="12f25-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="12f25-173">Cliquez dans le corps du document et tapez **Minutes à partir de la dernière réunion du Conseil**, puis cliquez sur **cadres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="12f25-174">Vous devriez voir **SensitiveData-BeforeIRM.docx** dans le dossier **Documents** .</span><span class="sxs-lookup"><span data-stu-id="12f25-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="12f25-175">Ensuite, vous téléchargez une copie locale du document SensitiveData-BeforeIRM.docx et la publiez accidentellement dans la collection de sites Ventes.</span><span class="sxs-lookup"><span data-stu-id="12f25-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="12f25-176">Sur votre ordinateur local, créez un nouveau dossier (par exemple, C:\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="12f25-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="12f25-177">Sous l’onglet **Documents** de votre navigateur, sélectionnez le document **SensitiveData-BeforeIRM.docx** , cliquez sur le bouton de sélection, puis cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="12f25-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="12f25-178">Stocker le document **SensitiveData-BeforeIRM.docx** dans le dossier créé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="12f25-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="12f25-179">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="12f25-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="12f25-180">Cliquez sur le dossier de **Documents** de la **collection de sites de vente**.</span><span class="sxs-lookup"><span data-stu-id="12f25-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="12f25-181">Cliquez sur **Télécharger**, puis spécifiez **SensitiveData-BeforeIRM.docx** document dans le dossier créé à l’étape 1 et puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="12f25-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="12f25-182">Vérifiez que le document **SensitiveData-BeforeIRM.docx** est dans le dossier **Documents** .</span><span class="sxs-lookup"><span data-stu-id="12f25-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="12f25-183">Fermer les onglets **ventes** et **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="12f25-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12f25-184">Ensuite, connectez-vous en tant que Utilisateur 5 et essayez d’ouvrir le document SensitiveData-BeforeIRM.docx dans la collection de sites de ventes.</span><span class="sxs-lookup"><span data-stu-id="12f25-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="12f25-185">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12f25-186">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="12f25-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12f25-187">Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="12f25-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="12f25-188">Tapez le nom de compte de User5 et de son mot de passe, puis cliquez sur **se connecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="12f25-189">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.</span><span class="sxs-lookup"><span data-stu-id="12f25-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="12f25-190">Dans le dossier **Documents** de la **collection de sites de vente**, cliquez sur le document **SensitiveData-BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="12f25-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="12f25-191">Vous devriez voir son contenu.</span><span class="sxs-lookup"><span data-stu-id="12f25-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="12f25-192">Fermer les onglets de **Documents** et de **collection de sites de vente** .</span><span class="sxs-lookup"><span data-stu-id="12f25-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="12f25-193">En publiant accidentellement le document SensitiveData-BeforeIRM.docx sur la collection de sites de ventes, le directeur général a ignoré la sécurité des autorisations de la collection de sites Cadres.</span><span class="sxs-lookup"><span data-stu-id="12f25-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="12f25-194">Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="12f25-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="12f25-195">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12f25-196">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="12f25-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12f25-197">Dans la page **Office 365 se connecter** , cliquez sur le nom du compte administrateur global, tapez son mot de passe, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="12f25-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="12f25-198">Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin > centres d’administration > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="12f25-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="12f25-199">Dans l’onglet **Centre d’administration de SharePoint** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="12f25-200">Dans la page **paramètres** , dans la section **Gestion des droits relatifs à l’Information (IRM)** , sélectionnez **utiliser le service IRM spécifié dans votre configuration**et sélectionnez **Actualiser les paramètres IRM**.</span><span class="sxs-lookup"><span data-stu-id="12f25-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="12f25-201">Fermez l’onglet **Centre d’administration SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="12f25-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="12f25-202">Phase 3 : Utiliser la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365</span><span class="sxs-lookup"><span data-stu-id="12f25-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="12f25-203">Lors de cette phase, vous utilisez la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365 pour protéger l’accès à un document contenant des informations sensibles, même lorsqu’il est publié sur un site avec des autorisations d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="12f25-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="12f25-204">Tout d’abord, vous activez et configurez IRM pour la bibliothèque de documents de la collection de sites Cadres. </span><span class="sxs-lookup"><span data-stu-id="12f25-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="12f25-205">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.</span><span class="sxs-lookup"><span data-stu-id="12f25-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="12f25-206">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="12f25-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="12f25-207">Dans l’angle supérieur droit, cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="12f25-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="12f25-208">Dans la page **paramètres** , sous **autorisations et gestion**, cliquez sur **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="12f25-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="12f25-209">Dans la page **Paramètres de gestion des droits d’informations** :</span><span class="sxs-lookup"><span data-stu-id="12f25-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="12f25-210">Sélectionnez **restreindre l’accès aux documents de cette bibliothèque au téléchargement**.</span><span class="sxs-lookup"><span data-stu-id="12f25-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="12f25-211">Pour **créer un titre de stratégie d’autorisation**, tapez **dirigeants**.</span><span class="sxs-lookup"><span data-stu-id="12f25-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="12f25-212">Pour **Ajouter une description de stratégie d’autorisation**, tapez **IRM pour les cadres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="12f25-213">Cliquez sur **Afficher les Options**.</span><span class="sxs-lookup"><span data-stu-id="12f25-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="12f25-214">Sous **définir les paramètres de la bibliothèque supplémentaires IRM**, sélectionnez **ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge les IRM**.</span><span class="sxs-lookup"><span data-stu-id="12f25-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="12f25-215">Sous **Configuration des droits d’accès document**, sélectionnez **Autoriser les utilisateurs à imprimer** et **Autoriser les utilisateurs à écrire sur une copie du document téléchargé**.</span><span class="sxs-lookup"><span data-stu-id="12f25-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="12f25-216">Sous **définir le groupe de protection et intervalle d’informations d’identification**, sélectionnez **Autoriser du groupe de protection** et pour le **groupe par défaut**, tapez des **cadres**.</span><span class="sxs-lookup"><span data-stu-id="12f25-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="12f25-217">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="12f25-217">Click **OK**.</span></span>
    
<span data-ttu-id="12f25-218">Ensuite, en jouant le rôle du directeur général, vous chargez un nouveau document dans le dossier de documents Cadres, le téléchargez, puis le chargez accidentellement dans le dossier de documents Ventes.</span><span class="sxs-lookup"><span data-stu-id="12f25-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="12f25-219">Ouvrez le dossier local dans lequel est stocké le document **SensitiveData-BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="12f25-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="12f25-220">Droit **SensitiveData-BeforeIRM.docx**, puis cliquez sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="12f25-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="12f25-221">Avec le bouton droit dans le dossier, puis cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="12f25-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="12f25-222">Renommez le nouveau fichier **SensitiveData-BeforeIRM - Copy.docx** **AfterIRM.docx-SensitiveData**.</span><span class="sxs-lookup"><span data-stu-id="12f25-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="12f25-223">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="12f25-224">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="12f25-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="12f25-225">Dans la page **Office 365 se connecter** , cliquez sur le nom de compte de PDG, tapez son mot de passe, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="12f25-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="12f25-226">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.</span><span class="sxs-lookup"><span data-stu-id="12f25-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="12f25-227">Sur la page **Documents** , cliquez sur **Télécharger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="12f25-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="12f25-228">Sélectionnez le nouveau document **SensitiveData-AfterIRM.docx** dans la page **Documents** et cliquez sur le bouton de sélection (...) dans la barre de menus, puis cliquez sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="12f25-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="12f25-229">Lorsque vous y êtes invité, enregistrez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, en remplaçant la version d’origine.</span><span class="sxs-lookup"><span data-stu-id="12f25-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="12f25-230">Fermer l’onglet de la page de **Documents** .</span><span class="sxs-lookup"><span data-stu-id="12f25-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="12f25-231">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.</span><span class="sxs-lookup"><span data-stu-id="12f25-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="12f25-232">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="12f25-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="12f25-233">Sur la page **Documents** , cliquez sur **Télécharger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="12f25-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="12f25-234">Fermer les onglets de la **collection de sites de vente** et de **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="12f25-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12f25-235">Agissant comme un utilisateur normal, vous essayez ensuite d’accéder au document **SensitiveData-AfterIRM.docx** dans le dossier de document de vente.</span><span class="sxs-lookup"><span data-stu-id="12f25-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="12f25-236">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="12f25-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12f25-237">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="12f25-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12f25-238">Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5, tapez son mot de passe, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="12f25-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="12f25-239">Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.</span><span class="sxs-lookup"><span data-stu-id="12f25-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="12f25-240">Cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="12f25-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="12f25-241">Sur la page **Documents** , ouvrez le document **SensitiveData-AfterIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="12f25-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="12f25-242">Vous devez voir un message indiquant « Désolé, Word Online ne peut pas ouvrir ce document, car il est protégé par la Gestion des droits relatifs à l’information (IRM). » </span><span class="sxs-lookup"><span data-stu-id="12f25-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="12f25-p105">Cliquez sur **Modifier dans Word**. Vous êtes invité si vous souhaitez ouvrir le fichier. Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="12f25-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="12f25-p106">Vous êtes invité à connexion tapez le nom de compte du compte User5, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="12f25-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="12f25-p107">Vous êtes invité à fournir le mot de passe. Tapez le mot de passe pour le compte User5 et puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="12f25-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="12f25-250">Vous devez voir un message indiquant ce qui suit : « Vous ne disposez pas des informations d’identification requises pour ouvrir ce document. »</span><span class="sxs-lookup"><span data-stu-id="12f25-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="12f25-251">Cliquez sur **non**.</span><span class="sxs-lookup"><span data-stu-id="12f25-251">Click **No**.</span></span>
    
<span data-ttu-id="12f25-p108">Une autre façon de voir la protection IRM consiste à rechercher les fichiers dans votre dossier local. **SensitiveData-AfterIRM.docx** doit être beaucoup plus volumineux que le fichier **SensitiveData-BeforeIRM.docx** . Le fichier **AfterIRM.docx-SensitiveData** est crypté et possède les informations de protection IRM ajoutés.</span><span class="sxs-lookup"><span data-stu-id="12f25-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12f25-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12f25-255">See Also</span></span>

[<span data-ttu-id="12f25-256">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="12f25-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="12f25-257">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="12f25-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="12f25-258">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="12f25-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="12f25-259">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="12f25-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


