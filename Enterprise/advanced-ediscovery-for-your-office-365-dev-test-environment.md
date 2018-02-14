---
title: "Advanced eDiscovery pour votre environnement de développement/test Office 365"
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
- TLG-
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Résumé : Configurer et illustrer l’avancée de Office 365 d’eDiscovery avec des exemples de données dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: a118ec2753d04afb60d13890b7d5da8c07701721
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="70aa5-103">Advanced eDiscovery pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="70aa5-104">**Résumé :** Configurer et illustrer l’avancée de Office 365 d’eDiscovery avec des exemples de données dans votre environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="70aa5-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="70aa5-p101">EDiscovery avancées d’Office 365 vous permet de trouver rapidement et d’analyser les informations pertinentes sur les données stockées dans Office 365, y compris les e-mails et les documents. Cela peut enregistrer des montants considérables de temps et de dépenses, notamment dans le cas de litiges. Pour plus d’informations, reportez-vous à la section [avancée de Office 365 une e-Discovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="70aa5-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="70aa5-108">Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="70aa5-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="70aa5-109">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="70aa5-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="70aa5-110">Phase 1 : Création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="70aa5-111">Si vous souhaitez juste tester eDiscovery avancée dans une solution légère avec la configuration minimale requise, suivez les instructions dans la Phase 2 et 3 de Phase de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="70aa5-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="70aa5-112">Si vous souhaitez tester eDiscovery avancée dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="70aa5-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="70aa5-p102">Test d’e-Discovery avancée ne requiert pas l’environnement simulé enterprise, qui comprend un intranet simulé est connecté à Internet et la synchronisation d’annuaire pour une forêt Active Directory de Windows Server. Il est fourni ici en tant qu’option de sorte que vous pouvez effectuer des tests et l’expérimentation dans un environnement qui représente une organisation typique.</span><span class="sxs-lookup"><span data-stu-id="70aa5-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="70aa5-115">Phase 2 : Création des données d’exemple pour Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="70aa5-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="70aa5-116">Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="70aa5-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="70aa5-117">Ouvrez Internet Explorer et connectez-vous à [https://outlook.com](https://outlook.com) pour le compte de Outlook que vous avez créé à la Phase 2 de[l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="70aa5-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="70aa5-118">Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="70aa5-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="70aa5-119">Si vous utilisez l’environnement de développement/test entreprise simulée, utiliser le portail Azure ([https://portal.azure.com](https://portal.azure.com)) de se connecter à la machine virtuelle de CLIENT1, puis connectez-vous à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="70aa5-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="70aa5-120">Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="70aa5-p103">Dans la zone **à**, tapez l’adresse de messagerie du compte de votre abonnement d’évaluation User6 ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="70aa5-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="70aa5-123">Pour l’objet, tapez **l’e-mail de Test 1**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="70aa5-124">Dans le corps, tapez **Tailspin contrat brouillon**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="70aa5-125">Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="70aa5-126">Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="70aa5-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="70aa5-127">Pour l’objet, tapez **Test message électronique 2**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="70aa5-128">Dans le corps, tapez **réunion déjeuner de Tailspin**et puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="70aa5-129">Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="70aa5-130">Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="70aa5-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="70aa5-131">Pour l’objet, tapez **Test message électronique 3**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="70aa5-132">Dans le corps, tapez **désaccord du contrat Tailspin**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="70aa5-133">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="70aa5-134">Ouvrir un nouvel onglet et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec le nom de compte et le mot de passe du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="70aa5-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="70aa5-135">Dans l’onglet du **portail Office 365** , cliquez sur **courrier**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="70aa5-136">Sous l’onglet **courrier - User6 - Outlook** , vérifiez que User6 a reçu toutes les trois courriers électroniques à partir du compte de messagerie Outlook.</span><span class="sxs-lookup"><span data-stu-id="70aa5-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="70aa5-137">Revenez à l' **onglet de portail Office 365** pour User6.</span><span class="sxs-lookup"><span data-stu-id="70aa5-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="70aa5-138">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **vous déconnecter.**</span><span class="sxs-lookup"><span data-stu-id="70aa5-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="70aa5-139">Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="70aa5-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="70aa5-140">Dans la page **Office** , cliquez sur **se connecter,** la connexion avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="70aa5-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="70aa5-141">Dans un nouvel onglet, accéder à l’URL de votre site de Production : **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="70aa5-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="70aa5-142">Dans l’onglet de la **collection de sites de Production** , de **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="70aa5-143">Sur la page **En ligne de Word** , tapez **brouillon de contrat Tailspin**et attendre jusqu'à ce qu’il affiche **enregistrée** dans le titre puis fermer l’onglet de page de **Word en ligne** .</span><span class="sxs-lookup"><span data-stu-id="70aa5-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="70aa5-144">Dans l’onglet de la **collection de sites de Production** , de **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="70aa5-145">Sous l’onglet **Word en ligne** , tapez **notes de litige de paiement de contrat Tailspin**et attendre jusqu'à ce qu’il affiche **enregistrée** dans le titre puis fermez l’onglet **Word en ligne** .</span><span class="sxs-lookup"><span data-stu-id="70aa5-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="70aa5-146">Sous l’onglet de la **collection de sites de Production** , vous devriez voir le **Document** et **Document1** dans la liste des documents.</span><span class="sxs-lookup"><span data-stu-id="70aa5-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="70aa5-147">Fermer l’onglet de la **collection de sites de Production** .</span><span class="sxs-lookup"><span data-stu-id="70aa5-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="70aa5-148">Phase 3 : Utilisation eDiscovery avancées pour un litige</span><span class="sxs-lookup"><span data-stu-id="70aa5-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="70aa5-p104">Malheureusement, un litige contractuel entre votre organisation et de la société Tailspin Toys a atteint le point d’action en justice. Dans cette procédure, vous créez et configurez un cas d’e-Discovery avancées pour rechercher et analyser les e-mails et les documents qui contiennent le texte « Contrat de Tailspin ».</span><span class="sxs-lookup"><span data-stu-id="70aa5-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="70aa5-151">La procédure d’utilisation d’Advanced eDiscovery est la suivante :</span><span class="sxs-lookup"><span data-stu-id="70aa5-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="70aa5-152">Créer une recherche dans la sécurité &amp; centre de conformité, analyser ses résultats et préparer ensuite les résultats d’eDiscovery avancée.</span><span class="sxs-lookup"><span data-stu-id="70aa5-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="70aa5-153">Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="70aa5-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="70aa5-154">Dans cette procédure, vous créez une recherche dans la sécurité &amp; centre de « Contrat de Tailspin », regardez les résultats, de conformité et eDiscovery avancée puis préparer les résultats.</span><span class="sxs-lookup"><span data-stu-id="70aa5-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="70aa5-155">À partir de l’onglet du **portail Office 365** , cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="70aa5-156">Dans la l’onglet centre Admin de navigation gauche, cliquez sur **les centres Admin > conformité**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="70aa5-157">Sur le **sécurité &amp; la conformité** , cliquez sur **autorisations**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="70aa5-158">Dans la liste des **autorisations** , double-cliquez sur **Gestion de l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="70aa5-159">Dans la fenêtre de **Groupe de rôles** , sous **les membres**, cliquez sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="70aa5-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="70aa5-160">Dans la fenêtre **Sélectionner les membres** , double-cliquez sur le nom de votre compte administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="70aa5-161">Dans la fenêtre de **Groupe de rôles** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="70aa5-162">Dans la liste des **autorisations** , double-cliquez sur **gestionnaire eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="70aa5-163">Dans la fenêtre de **Groupe de rôles** , sous **e-Discovery administrateur**, cliquez sur l’icône de signe plu.</span><span class="sxs-lookup"><span data-stu-id="70aa5-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="70aa5-164">Dans la fenêtre **Sélectionner les membres** , double-cliquez sur le nom de votre compte administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="70aa5-165">Dans la fenêtre de **Groupe de rôles** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="70aa5-166">Dans la navigation de gauche, cliquez sur **recherche &amp; enquête > recherche de contenu de**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="70aa5-167">Cliquez sur l’icône plus pour ajouter une recherche.</span><span class="sxs-lookup"><span data-stu-id="70aa5-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="70aa5-168">Dans la fenêtre **nouvelle recherche** , tapez **recherche de contrat Tailspin** dans la zone **nom**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="70aa5-169">Dans **où voulez-vous rechercher ?**et cliquez sur **Rechercher partout,** sélectionnez **Exchange**, **SharePoint**et **Les dossiers publics**, puis cliquez sur **Suivant.**</span><span class="sxs-lookup"><span data-stu-id="70aa5-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="70aa5-170">Dans **que voulez-vous rechercher les ?**, type **contrat de Tailspin**et puis cliquez sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="70aa5-171">Dans la liste des recherches, cliquez sur le nom de **recherche du contrat Tailspin** .</span><span class="sxs-lookup"><span data-stu-id="70aa5-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="70aa5-p105">Dans le volet de **recherche de contrat Tailspin** , cliquez sur **Aperçu des résultats de recherche** dans les **résultats**. Vous devez voir une fenêtre répertoriant les deux documents sur le site SharePoint de Production ( **Document** et **Document1**) et les e-mails de **e-mail de Test 1** et **e-mail de Test 3** à User6. Fermez la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="70aa5-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="70aa5-175">Dans le volet de **recherche de contenu** , sous **résultats d’Analyze avec l’e-Discovery avancée**, cliquez sur **Aperçu des résultats d’analyse**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="70aa5-176">Dans la fenêtre **des résultats pour la recherche de contrat Tailspin préparer la recherche** , cliquez sur **préparer** et attendre qu’elle se termine.</span><span class="sxs-lookup"><span data-stu-id="70aa5-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="70aa5-177">Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.</span><span class="sxs-lookup"><span data-stu-id="70aa5-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="70aa5-178">Dans la navigation de gauche, cliquez sur l' **e-Discovery** sous **recherche &amp; enquête**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="70aa5-179">Dans le volet de **l’e-Discovery** , cliquez sur **Avancé eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="70aa5-180">Dans l’onglet **Paramètres avancés d’e-Discovery** , cliquez sur l’icône de signe plu pour ajouter un nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="70aa5-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="70aa5-p106">Dans le volet **Ajouter cas** , tapez **litige contractuel de Tailspin** dans **nom**et puis cliquez sur **OK**. Attendez que le cas doit être créé.</span><span class="sxs-lookup"><span data-stu-id="70aa5-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="70aa5-183">Double-cliquez sur le cas de **litige contractuel de Tailspin** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="70aa5-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="70aa5-p107">Dans la liste de **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis cliquez sur **processus**. Attendez la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="70aa5-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="70aa5-186">Lors de la **processus : terminé** s’affiche au bas de la fenêtre, cliquez sur **processus de synthèse** dans la navigation de gauche pour voir un résumé.</span><span class="sxs-lookup"><span data-stu-id="70aa5-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="70aa5-187">Dans la navigation supérieure, cliquez sur **analyser**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="70aa5-188">Dans la page **paramètres** , sous **thèmes**, tapez **3** dans **le nombre maximal de thèmes**.</span><span class="sxs-lookup"><span data-stu-id="70aa5-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="70aa5-p108">Cliquez sur **analyser** et attendez que l’analyse à effectuer. Vous devriez voir une série de graphiques en secteurs avec l’analyse de la population cible, les documents, les e-mails et les pièces jointes. Pour plus d’informations, consultez [affichage d’analyser les résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="70aa5-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="70aa5-192">Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="70aa5-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70aa5-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70aa5-193">See Also</span></span>

[<span data-ttu-id="70aa5-194">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="70aa5-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="70aa5-195">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="70aa5-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="70aa5-196">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="70aa5-197">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="70aa5-198">Application du nuage sécurité pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="70aa5-199">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="70aa5-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="70aa5-200">EDiscovery avancées d’Office 365</span><span class="sxs-lookup"><span data-stu-id="70aa5-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


