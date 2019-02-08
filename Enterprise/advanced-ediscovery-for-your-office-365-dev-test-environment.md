---
title: Advanced eDiscovery pour votre environnement de développement/test Office 365
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Résumé : Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897507"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="a2431-103">Advanced eDiscovery pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a2431-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="a2431-104">**Résumé :** Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2431-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a2431-p101">EDiscovery avancées Office 365 vous permet de trouver rapidement et analyser les informations pertinentes sur les données stockées dans Office 365, notamment le courrier électronique et des documents. Cette possibilité d’enregistrer quantités énormes de temps et de dépenses, notamment dans le cas de litige. Pour plus d’informations, voir [eDiscovery Office 365 avancés](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="a2431-p101">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="a2431-108">Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="a2431-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="a2431-109">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="a2431-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="a2431-110">Phase 1 : Création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a2431-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="a2431-111">Si vous souhaitez uniquement tester eDiscovery avancée dans une solution légère avec la configuration minimale requise, suivez les instructions de la Phase 2 et 3 de Phase de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a2431-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a2431-112">Si vous souhaitez tester eDiscovery avancée dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a2431-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a2431-p102">Test de découverte électronique avancée ne nécessite pas de l’environnement d’entreprise simulé, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option de sorte que vous pouvez effectuer des tests et l’expérimentation dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="a2431-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="a2431-115">Phase 2 : Création des données d’exemple pour Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="a2431-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="a2431-116">Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="a2431-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="a2431-117">Ouvrez Internet Explorer et vous connecter à [https://outlook.com](https://outlook.com) pour le compte Outlook que vous avez créé dans la Phase 2 de[l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a2431-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="a2431-118">Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a2431-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="a2431-119">Si vous utilisez l’environnement de développement/test entreprise simulé, utiliser le portail Azure ([https://portal.azure.com](https://portal.azure.com)) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="a2431-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="a2431-120">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="a2431-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="a2431-p103">Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="a2431-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="a2431-123">Pour l’objet, saisissez **Message électronique de test 1**.</span><span class="sxs-lookup"><span data-stu-id="a2431-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="a2431-124">Dans le corps, saisissez **Brouillon de contrat Tailspin**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="a2431-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="a2431-125">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="a2431-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="a2431-126">Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="a2431-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="a2431-127">Pour l’objet, saisissez **Message électronique de test 2**.</span><span class="sxs-lookup"><span data-stu-id="a2431-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="a2431-128">Dans le corps, saisissez **Réunion Tailspin à l’heure du déjeuner**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="a2431-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="a2431-129">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="a2431-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="a2431-130">Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="a2431-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="a2431-131">Pour l’objet, saisissez **Message électronique de test 3**.</span><span class="sxs-lookup"><span data-stu-id="a2431-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="a2431-132">Dans le corps, saisissez **Désaccord sur le contrat Tailspin**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="a2431-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="a2431-133">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="a2431-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="a2431-134">Ouvrez un nouvel onglet et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec le nom de compte et mot de passe du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="a2431-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="a2431-135">Dans l’onglet **Portail Office 365**, cliquez sur **Courrier**.</span><span class="sxs-lookup"><span data-stu-id="a2431-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="a2431-136">Sous l’onglet **messagerie - User6 - Outlook** , vérifiez que User6 provenant de tous les messages trois électroniques au compte de messagerie Outlook.</span><span class="sxs-lookup"><span data-stu-id="a2431-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="a2431-137">Revenez à l’**onglet Portail Office 365** pour User6.</span><span class="sxs-lookup"><span data-stu-id="a2431-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="a2431-138">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="a2431-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="a2431-139">Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="a2431-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="a2431-140">Dans la page **Office**, cliquez sur **Se connecter,** puis connectez-vous avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="a2431-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="a2431-141">Dans un nouvel onglet, accéder à l’URL de votre site SharePoint de Production : **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="a2431-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="a2431-142">Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="a2431-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="a2431-143">Sur la page **Word Online**, saisissez **Brouillon de contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet de la page **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="a2431-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="a2431-144">Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="a2431-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="a2431-145">	Dans l’onglet *\*Word Online*\*, saisissez *\*Notes sur le litige lié au contrat Tailspin*\*, patientez jusqu’à ce que le titre affiche *\*Enregistré*\*, puis fermez l’onglet *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="a2431-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="a2431-146">Dans l’onglet **Collection de sites de production**, Vous devriez voir **Document** et **Document1** dans la liste de documents.</span><span class="sxs-lookup"><span data-stu-id="a2431-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="a2431-147">Fermez l’onglet **Collection de sites de production**.</span><span class="sxs-lookup"><span data-stu-id="a2431-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="a2431-148">Phase 3 : Utilisation avancée eDiscovery pour un litige</span><span class="sxs-lookup"><span data-stu-id="a2431-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="a2431-p104">Malheureusement, un litige contrat entre votre organisation et les Tailspin Toys a atteint le point d’action juridique. Dans cette procédure, vous créez et configurez un cas eDiscovery avancé pour rechercher et analyser les e-mails et les documents qui contiennent le texte « Contrat Tailspin ».</span><span class="sxs-lookup"><span data-stu-id="a2431-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="a2431-151">La procédure d’utilisation d’Advanced eDiscovery est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a2431-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="a2431-152">Créer une recherche dans la sécurité &amp; centre de conformité, analyser les résultats et préparer les résultats de la découverte électronique avancée.</span><span class="sxs-lookup"><span data-stu-id="a2431-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="a2431-153">Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="a2431-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="a2431-154">Dans cette procédure, vous créez une recherche dans la sécurité &amp; du centre de « Contrat Tailspin », recherchez les résultats et préparer les résultats de la découverte électronique avancée de conformité.</span><span class="sxs-lookup"><span data-stu-id="a2431-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="a2431-155">Dans l’onglet **Portail Office 365**, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a2431-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="a2431-156">Dans le volet de navigation gauche de l’onglet Centre d’administration, cliquez sur **Centres d’administration > Conformité**.</span><span class="sxs-lookup"><span data-stu-id="a2431-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="a2431-157">Sur le **sécurité &amp; conformité** , cliquez sur **autorisations**.</span><span class="sxs-lookup"><span data-stu-id="a2431-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="a2431-158">Dans la liste **Autorisations**, double-cliquez sur **Gestion de l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="a2431-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="a2431-159">Dans la fenêtre **Groupe de rôles**, sous **Membres**, cliquez sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="a2431-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="a2431-160">Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2431-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="a2431-161">Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a2431-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="a2431-162">Dans la liste **Autorisations**, double-cliquez sur **Gestionnaire eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="a2431-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="a2431-163">Dans la fenêtre **Groupe de rôles**, sous **Administrateur eDiscovery**, cliquez sur l’icône plus.</span><span class="sxs-lookup"><span data-stu-id="a2431-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="a2431-164">Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2431-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="a2431-165">Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a2431-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="a2431-166">Dans la navigation de gauche, cliquez sur **recherche &amp; recherche de contenu enquête >**.</span><span class="sxs-lookup"><span data-stu-id="a2431-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="a2431-167">Cliquez sur l’icône plus pour ajouter une recherche.</span><span class="sxs-lookup"><span data-stu-id="a2431-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="a2431-168">Dans la fenêtre **Nouvelle recherche**, saisissez **Recherche de contrat Tailspin** dans **Nom**.</span><span class="sxs-lookup"><span data-stu-id="a2431-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="a2431-169">Dans **Dans quels emplacements voulez-vous effectuer la recherche ?**, cliquez sur **Rechercher partout**, sélectionnez **Exchange**, **SharePoint** et **Dossiers publics**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="a2431-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="a2431-170">Dans **Que voulez-vous chercher ?**, saisissez **Contrat Tailspin**, puis cliquez sur **Recherche**.</span><span class="sxs-lookup"><span data-stu-id="a2431-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="a2431-171">Dans la liste des recherches, cliquez sur le nom **Recherche de contrat Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="a2431-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="a2431-p105">Dans le volet de **recherche de contrat Tailspin** , cliquez sur **Aperçu des résultats de recherche** sous **résultats**. Vous devez voir une fenêtre répertoriant les deux documents sur le site SharePoint de Production ( **Document** et **Document1**) et les **Test courrier 1** et **Test message électronique 3** les messages électroniques à User6. Fermez la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="a2431-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="a2431-175">Dans le volet **Recherche de contenu**, sous **Analyser les résultats avec Advanced eDiscovery**, cliquez sur **Aperçu des résultats pour l’analyse**.</span><span class="sxs-lookup"><span data-stu-id="a2431-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="a2431-176">Dans la fenêtre **Préparer les résultats de recherche pour la recherche de contrat Tailspin**, cliquez sur **Préparer** et attendez qu’elle se termine.</span><span class="sxs-lookup"><span data-stu-id="a2431-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="a2431-177">Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.</span><span class="sxs-lookup"><span data-stu-id="a2431-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="a2431-178">Dans la navigation de gauche, cliquez sur **eDiscovery** sous **recherche &amp; enquête**.</span><span class="sxs-lookup"><span data-stu-id="a2431-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="a2431-179">Dans le volet **eDiscovery**, cliquez sur **Atteindre Advanced eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="a2431-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="a2431-180">Dans l’onglet **Advanced eDiscovery**, cliquez sur l’icône plus pour ajouter un nouvel incident.</span><span class="sxs-lookup"><span data-stu-id="a2431-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="a2431-p106">	Dans le volet *\*Ajouter un incident*\*, saisissez *\*Litige de contrat Tailspin** dans *\*Nom*\*, puis cliquez sur *\*OK*\*. Attendez que l’incident soit créé.</span><span class="sxs-lookup"><span data-stu-id="a2431-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="a2431-183">Double-cliquez sur l’incident **Litige de contrat Tailspin** dans la liste. </span><span class="sxs-lookup"><span data-stu-id="a2431-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="a2431-p107">Dans la liste du **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis cliquez sur **le processus**. Attendez la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="a2431-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="a2431-186">Lorsque le message **Processus : terminé** apparaît en bas de la fenêtre, cliquez sur **Résumé du processus** dans le volet de navigation de gauche pour afficher un résumé.</span><span class="sxs-lookup"><span data-stu-id="a2431-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="a2431-187">Dans la partie supérieure de la navigation, cliquez sur **Analyser**.</span><span class="sxs-lookup"><span data-stu-id="a2431-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="a2431-188">Dans la page **Installation**, sous **Thèmes**, saisissez **3** dans **Nombre maximal de thèmes**.</span><span class="sxs-lookup"><span data-stu-id="a2431-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="a2431-p108">Cliquez sur **analyser** et attendez que l’analyse à effectuer. Vous devez voir une série de graphiques en secteurs avec l’analyse de la population cible, documents, messages électroniques et les pièces jointes. Pour plus d’informations, voir [affichage analyser les résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="a2431-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="a2431-192">Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2431-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a2431-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2431-193">See Also</span></span>

[<span data-ttu-id="a2431-194">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="a2431-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a2431-195">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="a2431-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a2431-196">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a2431-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a2431-197">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a2431-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="a2431-198">Sécurité des applications cloud pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a2431-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="a2431-199">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="a2431-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="a2431-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="a2431-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


