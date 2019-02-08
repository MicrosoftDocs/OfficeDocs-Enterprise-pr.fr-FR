---
title: Classification et étiquetage des données dans l’environnement de développement/test Office 365
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: Résumé :Configurer et démontrer la classification et l’étiquetage de données à l’aide du client Azure Information Protection (AIP) dans votre environnement de développement/test Office 365.
ms.openlocfilehash: 69526f8bf0ae0b6cc7509653cfaa72581e10dbfe
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897437"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="e44ef-103">Classification et étiquetage des données dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="e44ef-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="e44ef-104">**Résumé :** Configurer et démontrer la classification et l’étiquetage de données à l’aide du client Azure Information Protection (AIP) dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="e44ef-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e44ef-p101">Le client de la Protection des informations Azure vous permet de classer un document avant de le télécharger vers un dossier SharePoint Online dans Office 365. Avec les instructions de cet article, vous installez le client de la Protection des informations Azure et démontrer la classification des données. Pour plus d’informations, voir [La Protection des informations Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="e44ef-p101">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="e44ef-108">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="e44ef-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="e44ef-109">Phase 1 : créer votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="e44ef-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="e44ef-110">Suivez les instructions de la rubrique [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e44ef-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="e44ef-111">Phase 2 : ajouter l’abonnement à la version d’évaluation Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e44ef-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="e44ef-p102">Dans cette phase, vous ajoutez Azure Information Protection à votre environnement de développement/test Office 365 et l’activez pour vos comptes d’utilisateurs. Si vous avez configuré l’[Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorez cette phase. L’abonnement à la version d’évaluation Enterprise Mobility Suite inclut des licences Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e44ef-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="e44ef-115">Tout d’abord, souscrivez un abonnement à la version d’évaluation Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e44ef-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="e44ef-116">Souscrire à un abonnement à la version d’évaluation Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e44ef-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="e44ef-117">Dans Internet Explorer ou votre navigateur, accédez à [http://portal.office.com](http://portal.office.com) et connectez-vous avec votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="e44ef-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="e44ef-118">Dans l’onglet **Accueil Microsoft Office**, cliquez sur la mosaïque **Admin**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e44ef-119">Sous l’onglet Admin d’Office 365, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e44ef-p103">Dans la page **Acheter des services**, recherchez l’élément **Azure Information Protection Premium P2**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e44ef-122">Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e44ef-123">Dans la page **Réception de la commande**, cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="e44ef-124">Ensuite, vous activez la licence de Azure Information Protection pour tous les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e44ef-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="e44ef-125">	Sous l’onglet Centre d’administrateur Office 365, cliquez sur *\*Utilisateurs*\*.</span><span class="sxs-lookup"><span data-stu-id="e44ef-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="e44ef-126"> Dans la liste des comptes d’utilisateur, sélectionnez votre compte d’administrateur global, puis cliquez sur *\*Modifier** pour *\*Licences de produits*\*.</span><span class="sxs-lookup"><span data-stu-id="e44ef-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e44ef-127">	Réglez la licence de produit pour *\*Azure Information Protection Premium P2** sur *\*Activé*\*, cliquez sur *\*Enregistrer*\*, puis sur *\*Fermer** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="e44ef-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="e44ef-128">Répétez les étapes 2 et 3 pour d’autres comptes d’utilisateur (Utilisateur 1 à Utilisateur 5).</span><span class="sxs-lookup"><span data-stu-id="e44ef-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="e44ef-129">Votre environnement de développement/test Office 365 comprend désormais :</span><span class="sxs-lookup"><span data-stu-id="e44ef-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="e44ef-130">Abonnements à la version d’évaluation d’Office 365 E5 Entreprise et Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e44ef-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="e44ef-131">Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e44ef-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="e44ef-132">Phase 3 : démontrer la classification des données</span><span class="sxs-lookup"><span data-stu-id="e44ef-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="e44ef-133">Lors de cette phase, vous démontrez la classification des données à l’aide du client Azure Information Protection et de la stratégie Azure Information Protection par défaut.</span><span class="sxs-lookup"><span data-stu-id="e44ef-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="e44ef-134">Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, vous devez tout d’abord installer Office 2016 sur CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e44ef-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="e44ef-135">Utilisez votre navigateur et accédez au [portail Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="e44ef-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="e44ef-136">	Cliquez sur *\*Groupes de ressources >** [nom de votre groupe de ressources] *\*> CLIENT1 > Se connecter*\*.</span><span class="sxs-lookup"><span data-stu-id="e44ef-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="e44ef-137">À partir de CLIENT1, exécutez Internet Explorer, accédez au portail Office à [http://portal.office.com](http://portal.office.com), puis connectez-vous avec le nom du compte User5 et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e44ef-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="e44ef-138">Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Installer Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="e44ef-p104">	Exécutez le fichier téléchargé lorsque vous y êtes invité, puis cliquez sur *\*Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur. Patientez pendant l’installation d’Office. Lorsque vous avez terminé, cliquez sur *\*Fermer** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="e44ef-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="e44ef-142">Ensuite, installez le client Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="e44ef-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="e44ef-143">Dans votre navigateur ou Internet Explorer, accédez à la [page de téléchargement Microsoft Azure la Protection des informations](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="e44ef-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="e44ef-144">Si vous utilisez la version légère de l’environnement de développement/test Office 365, utilisez le navigateur sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e44ef-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="e44ef-145">Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, exécutez Internet Explorer à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e44ef-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="e44ef-146">Sur la page de téléchargement **Microsoft Azure Information Protection**, cliquez sur **Télécharger**, sur **AzInfoProtection.exe**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="e44ef-147">Lorsque vous y êtes invité, exécutez AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="e44ef-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="e44ef-148">Dans la zone client **Installer Azure Information Protection**, cliquez sur **J’accepte**, puis sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e44ef-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="e44ef-149">Dans la zone **Terminé avec succès** , cliquez sur **Fermer.**</span><span class="sxs-lookup"><span data-stu-id="e44ef-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="e44ef-150">Ensuite, démontrez la classification des documents.</span><span class="sxs-lookup"><span data-stu-id="e44ef-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="e44ef-151">Cliquez sur l’icône **Word** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="e44ef-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="e44ef-152">Lorsque vous y êtes invité, connectez-vous avec le nom de compte Utilisateur 5 et le mot de passe associé.</span><span class="sxs-lookup"><span data-stu-id="e44ef-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="e44ef-153">Si vous venez d’installer Office 2016 sur CLIENT1, dans la zone **Commençons par le début** , cliquez sur **Accepter**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="e44ef-154">Cliquez sur **Document vierge**. </span><span class="sxs-lookup"><span data-stu-id="e44ef-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="e44ef-155">Notez la section **Protection** du ruban dans l’onglet **Accueil** et la ligne des classifications de document.</span><span class="sxs-lookup"><span data-stu-id="e44ef-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="e44ef-156">Dans le document vierge, tapez du texte.</span><span class="sxs-lookup"><span data-stu-id="e44ef-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="e44ef-157">Cliquez sur **Fichier > Enregistrer**, tapez le nom **BeforeAIP**, puis cliquez sur **OK**. </span><span class="sxs-lookup"><span data-stu-id="e44ef-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="e44ef-158">Sur la ligne de classes de documents, cliquez sur la flèche vers le bas pour **Secret**, puis cliquez sur **Toute l’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="e44ef-159">Cliquez sur **Fichier > Enregistrer sous**, tapez le nom **AfterAIP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e44ef-160">Cliquez sur l’**Explorateur de fichiers** dans la barre des tâches, puis ouvrez le dossier **Documents**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="e44ef-p105">Notez les tailles de fichier différent des documents **BeforeAIP** et **AfterAIP** . Le document AfterAIP est plus importante car elle contient les informations de classification.</span><span class="sxs-lookup"><span data-stu-id="e44ef-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="e44ef-163">Ensuite, autorisez tout le monde à accéder à la collection de sites Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e44ef-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="e44ef-164">	Dans l’onglet *\*Accueil Microsoft Office*\*, cliquez sur *\*SharePoint*\*.</span><span class="sxs-lookup"><span data-stu-id="e44ef-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="e44ef-165">Dans l’onglet **SharePoint**, cliquez sur **Collection de sites Prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="e44ef-166">Dans le coin supérieur droit, cliquez sur l’icône **Paramètres**, puis cliquez sur **Partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="e44ef-167">Dans **partage de « Collection de sites de prise en charge »**, cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="e44ef-168">Dans la liste des groupes SharePoint, cliquez sur **Membres de la collection de sites Prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="e44ef-169">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="e44ef-170">Dans **partage de « Collection de sites de prise en charge »**, tapez **tout le monde**, cliquez sur **tout le monde, à l’exception des utilisateurs externes**, puis cliquez sur **partager.**</span><span class="sxs-lookup"><span data-stu-id="e44ef-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="e44ef-171">Fermez l’onglet **Personnes et groupes**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="e44ef-172">Ensuite, connectez-vous avec votre compte Utilisateur 5 et chargez le document protégé par AIP dans le dossier Documents de la collection de sites Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e44ef-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="e44ef-173">Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e44ef-174">Accédez à [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="e44ef-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="e44ef-175">Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5 et se connecter.</span><span class="sxs-lookup"><span data-stu-id="e44ef-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="e44ef-176">Dans l’onglet **Accueil Microsoft Office**, cliquez sur **SharePoint > Collection de sites Prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="e44ef-177">Cliquez sur **Documents**, sur **Charger**, sur le document **AfterAIP**, puis sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="e44ef-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="e44ef-178">Vous devriez voir AfterAIP.docx dans le dossier Documents de la collection de sites Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e44ef-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e44ef-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e44ef-179">See Also</span></span>

[<span data-ttu-id="e44ef-180">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="e44ef-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="e44ef-181">Environnement de développement/test Office 365 et EMS</span><span class="sxs-lookup"><span data-stu-id="e44ef-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="e44ef-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e44ef-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


