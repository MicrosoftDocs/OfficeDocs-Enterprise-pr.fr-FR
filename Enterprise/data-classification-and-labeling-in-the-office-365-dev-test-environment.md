---
title: Classification et étiquetage des données dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Résumé : configurez et démontrez la classification et l’étiquetage des données à l’aide du client Azure information protection (AIP) dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: f16fd41aaa454a3f038fd23c890bbf48be2c3e66
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028898"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="11d30-103">Classification et étiquetage des données dans l’environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="11d30-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="11d30-104">**Résumé :** Configurez et démontrez la classification et l’étiquetage des données à l’aide du client Azure information protection (AIP) dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="11d30-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="11d30-105">Le client Azure information protection vous permet de classer un document avant de le télécharger dans un dossier SharePoint Online dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="11d30-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="11d30-106">Avec les instructions de cet article, vous installez le client Azure information protection et démontrez la classification des données.</span><span class="sxs-lookup"><span data-stu-id="11d30-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="11d30-107">Pour plus d’informations, reportez-vous à [Azure information protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="11d30-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="11d30-108">Cliquez sur[ici](https://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.</span><span class="sxs-lookup"><span data-stu-id="11d30-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="11d30-109">Phase 1 : créer votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="11d30-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="11d30-110">Suivez les instructions de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="11d30-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="11d30-111">Phase 2 : ajouter l’abonnement à la version d’évaluation d’Azure information protection</span><span class="sxs-lookup"><span data-stu-id="11d30-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="11d30-112">Dans cette phase, vous allez ajouter Azure information protection à votre environnement de développement/test Office 365 et l’activer pour vos comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11d30-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="11d30-113">Si vous avez configuré l' [environnement de développement/test Office 365 et EMS](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorez cette phase.</span><span class="sxs-lookup"><span data-stu-id="11d30-113">If you have configured the [Office 365 and EMS dev/test environment](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="11d30-114">L’abonnement à la version d’évaluation de Enterprise Mobility suite inclut des licences Azure information protection.</span><span class="sxs-lookup"><span data-stu-id="11d30-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="11d30-115">Tout d’abord, inscrivez-vous pour obtenir un abonnement à la version d’évaluation d’Azure information protection.</span><span class="sxs-lookup"><span data-stu-id="11d30-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="11d30-116">Inscription à un abonnement à la version d’évaluation d’Azure information protection</span><span class="sxs-lookup"><span data-stu-id="11d30-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="11d30-117">Dans Internet Explorer ou votre navigateur, accédez à [https://admin.microsoft.com](https://admin.microsoft.com) et connectez-vous à l’aide de votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="11d30-117">In Internet Explorer or your browser, go to [https://admin.microsoft.com](https://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="11d30-118">Dans l’onglet **Accueil Microsoft Office** , cliquez sur la vignette **administrateur** .</span><span class="sxs-lookup"><span data-stu-id="11d30-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="11d30-119">Dans l’onglet Office 365 admin, dans le volet de navigation de gauche, cliquez sur **facturation > acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="11d30-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="11d30-120">Sur la page **acheter des services** , recherchez l’élément **Azure information protection Premium P2** .</span><span class="sxs-lookup"><span data-stu-id="11d30-120">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item.</span></span> <span data-ttu-id="11d30-121">Placez le pointeur de la souris dessus, puis cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="11d30-121">Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="11d30-122">Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="11d30-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="11d30-123">Dans la page **Réception de la commande**, cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="11d30-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="11d30-124">Ensuite, vous activez la licence Azure information protection pour tous les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11d30-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="11d30-125">Sous l’onglet Centre d’administration Microsoft 365, cliquez sur **utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="11d30-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="11d30-126">Dans la liste des comptes d’utilisateur, sélectionnez votre compte d’administrateur général, puis cliquez sur **modifier** pour **licences de produits**.</span><span class="sxs-lookup"><span data-stu-id="11d30-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="11d30-127">Activez la licence de produit pour **Azure information protection Premium P2** sur **activé**, cliquez sur **enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="11d30-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="11d30-128">Répétez les étapes 2 et 3 pour vos autres comptes d’utilisateur (utilisateur 1 à utilisateur 5).</span><span class="sxs-lookup"><span data-stu-id="11d30-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="11d30-129">Votre environnement de développement/test Office 365 dispose désormais des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="11d30-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="11d30-130">Les abonnements à la version d’évaluation d’Office 365 E5 entreprise et Azure information protection.</span><span class="sxs-lookup"><span data-stu-id="11d30-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="11d30-131">Tous vos comptes d’utilisateur activés pour utiliser Office 365 E5 entreprise et Azure information protection.</span><span class="sxs-lookup"><span data-stu-id="11d30-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="11d30-132">Phase 3 : faire la démonstration de la classification des données</span><span class="sxs-lookup"><span data-stu-id="11d30-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="11d30-133">Dans cette phase, vous démontrez la classification des données à l’aide du client Azure information protection et de la stratégie Azure information protection par défaut.</span><span class="sxs-lookup"><span data-stu-id="11d30-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="11d30-134">Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, vous devez d’abord installer Office 2016 sur CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="11d30-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="11d30-135">Utilisez votre navigateur et accédez au [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="11d30-135">Use your browser and go to the [Azure portal](https://portal.azure.com).</span></span>
    
2. <span data-ttu-id="11d30-136">Cliquez sur **groupes de ressources >** [nom de votre groupe de ressources] **> CLIENT1 > connecter**.</span><span class="sxs-lookup"><span data-stu-id="11d30-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="11d30-137">À partir de CLIENT1, exécutez Internet Explorer, accédez au portail Office [https://admin.microsoft.com](https://admin.microsoft.com)à, puis connectez-vous avec le nom de compte utilisateur 5 et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="11d30-137">From CLIENT1, run Internet Explorer, go to the Office portal at [https://admin.microsoft.com](https://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="11d30-138">Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Installer Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="11d30-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="11d30-139">Exécutez le téléchargement lorsque vous y êtes invité, puis cliquez sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11d30-139">Run the download when prompted and click **Yes** when prompted by User Account Control.</span></span> <span data-ttu-id="11d30-140">Patientez pendant l’installation d’Office.</span><span class="sxs-lookup"><span data-stu-id="11d30-140">Wait for Office to install.</span></span> <span data-ttu-id="11d30-141">Lorsque vous avez terminé, cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="11d30-141">When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="11d30-142">Ensuite, installez le client Azure information protection.</span><span class="sxs-lookup"><span data-stu-id="11d30-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="11d30-143">Dans votre navigateur ou Internet Explorer, accédez à la [page de téléchargement de Microsoft Azure information protection](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="11d30-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="11d30-144">Si vous utilisez la version légère de l’environnement de développement/test Office 365, utilisez le navigateur sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11d30-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="11d30-145">Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, exécutez Internet Explorer à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="11d30-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="11d30-146">Sur la page téléchargement de **Microsoft Azure information protection** , cliquez sur **Télécharger**, sur **AzInfoProtection. exe**, puis sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="11d30-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="11d30-147">Lorsque vous y êtes invité, exécutez AzInfoProtection. exe.</span><span class="sxs-lookup"><span data-stu-id="11d30-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="11d30-148">Dans la zone **installer le client Azure information protection** , cliquez sur **J’accepte**, puis sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11d30-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="11d30-149">Dans la zone **terminé** , cliquez sur **Fermer.**</span><span class="sxs-lookup"><span data-stu-id="11d30-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="11d30-150">Ensuite, vous démontrez la classification des documents.</span><span class="sxs-lookup"><span data-stu-id="11d30-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="11d30-151">Cliquez sur l’icône **Word** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="11d30-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="11d30-152">Lorsque vous y êtes invité, connectez-vous avec le nom de compte utilisateur 5 et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="11d30-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="11d30-153">Si vous venez d’installer Office 2016 sur CLIENT1, dans la **première zone,** cliquez sur **accepter**.</span><span class="sxs-lookup"><span data-stu-id="11d30-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="11d30-154">Cliquez sur **document vierge**.</span><span class="sxs-lookup"><span data-stu-id="11d30-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="11d30-155">Notez la section **protection** du ruban sous l’onglet **Accueil** et la ligne de classifications de documents.</span><span class="sxs-lookup"><span data-stu-id="11d30-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="11d30-156">Dans le document vide, tapez du texte.</span><span class="sxs-lookup"><span data-stu-id="11d30-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="11d30-157">Cliquez sur **fichier > enregistrer**, tapez le nom **BeforeAIP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="11d30-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="11d30-158">Dans la ligne de classes de documents, cliquez sur la flèche vers le bas correspondant à la **clé secrète**, puis cliquez sur **toutes les sociétés**.</span><span class="sxs-lookup"><span data-stu-id="11d30-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="11d30-159">Cliquez sur **fichier > enregistrer sous**, tapez le nom **AfterAIP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="11d30-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="11d30-160">Cliquez sur **Explorateur de fichiers** dans la barre des tâches, puis ouvrez le dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="11d30-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="11d30-161">Notez les différentes tailles de fichier des documents **BeforeAIP** et **AfterAIP** .</span><span class="sxs-lookup"><span data-stu-id="11d30-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="11d30-162">Le document AfterAIP est plus volumineux, car il contient les informations de classification.</span><span class="sxs-lookup"><span data-stu-id="11d30-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="11d30-163">Ensuite, vous autorisez tout le monde à accéder à la collection de sites de support technique.</span><span class="sxs-lookup"><span data-stu-id="11d30-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="11d30-164">Dans l’onglet **Accueil Microsoft Office** , cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="11d30-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="11d30-165">Dans l’onglet **SharePoint** , cliquez sur **collection de sites de support**.</span><span class="sxs-lookup"><span data-stu-id="11d30-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="11d30-166">Dans le coin supérieur droit, cliquez sur l’icône des **paramètres** , puis cliquez sur **partagé avec**.</span><span class="sxs-lookup"><span data-stu-id="11d30-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="11d30-167">Dans **partager « collection de sites prise en charge »**, cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="11d30-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="11d30-168">Dans la liste des groupes SharePoint, cliquez sur membres de la **collection de sites support**.</span><span class="sxs-lookup"><span data-stu-id="11d30-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="11d30-169">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="11d30-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="11d30-170">Dans **partager « collection de sites prise en charge »**, tapez **tout le monde**, cliquez sur **tout le monde sauf les utilisateurs externes**, puis cliquez sur **partager.**</span><span class="sxs-lookup"><span data-stu-id="11d30-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="11d30-171">Fermez l’onglet **personnes et groupes** .</span><span class="sxs-lookup"><span data-stu-id="11d30-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="11d30-172">Ensuite, connectez-vous avec votre compte utilisateur 5 et téléchargez le document protégé par AIP dans le dossier Documents de la collection de sites de support.</span><span class="sxs-lookup"><span data-stu-id="11d30-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="11d30-173">Dans l’onglet **Accueil Microsoft Office** , dans l’angle supérieur droit, cliquez sur l’icône de l’utilisateur, puis cliquez sur **déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="11d30-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="11d30-174">Accédez à [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="11d30-174">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="11d30-175">Sur la page **de connexion à Office 365** , cliquez sur le nom de compte utilisateur 5 et connectez-vous.</span><span class="sxs-lookup"><span data-stu-id="11d30-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="11d30-176">Dans l’onglet **Accueil Microsoft Office** , cliquez sur **SharePoint > support collection de sites**.</span><span class="sxs-lookup"><span data-stu-id="11d30-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="11d30-177">Cliquez sur **documents**, sur **Télécharger**, sur le document **AfterAIP** , puis sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="11d30-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="11d30-178">Vous devriez voir AfterAIP. docx dans le dossier Documents de la collection de sites prise en charge.</span><span class="sxs-lookup"><span data-stu-id="11d30-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="11d30-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11d30-179">See Also</span></span>

[<span data-ttu-id="11d30-180">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="11d30-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="11d30-181">Environnement de développement/test Office 365 et EMS</span><span class="sxs-lookup"><span data-stu-id="11d30-181">Office 365 and EMS dev/test environment</span></span>](https://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="11d30-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="11d30-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


