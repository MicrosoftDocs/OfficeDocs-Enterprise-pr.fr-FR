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
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741451"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="d71be-103">Advanced eDiscovery pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="d71be-104">**Résumé :** Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="d71be-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="d71be-105">Office 365 Advanced eDiscovery vous permet de trouver et d'analyser rapidement les informations pertinentes dans les données stockées dans Office 365, y compris le courrier électronique et les documents.</span><span class="sxs-lookup"><span data-stu-id="d71be-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="d71be-106">Cela permet de réaliser des économies importantes en matière de temps et d’argent, notamment en cas de litige.</span><span class="sxs-lookup"><span data-stu-id="d71be-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="d71be-107">Pour plus d'informations, voir [Découverte électronique avancée Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="d71be-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="d71be-108">Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="d71be-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="d71be-109">Cliquez [ici](http://aka.ms/catlgstack) pour afficher un plan de tous les Articles de la pile de guides de laboratoire de Test Office 365.</span><span class="sxs-lookup"><span data-stu-id="d71be-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="d71be-110">Phase 1 : Création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="d71be-111">Si vous souhaitez simplement tester Advanced eDiscovery de manière légère avec la configuration minimale requise, suivez les instructions de la phase 2 et de la phase 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d71be-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d71be-112">Si vous souhaitez tester la découverte électronique avancée dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d71be-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d71be-113">Le test de eDiscovery avancé ne nécessite pas l'environnement d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="d71be-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="d71be-114">Elle est fournie ici comme option afin que vous puissiez effectuer des tests et des expérimentations dans un environnement qui représente une organisation typique.</span><span class="sxs-lookup"><span data-stu-id="d71be-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="d71be-115">Phase 2 : Création des données d’exemple pour Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="d71be-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="d71be-116">Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="d71be-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="d71be-117">Ouvrez Internet Explorer et connectez [https://outlook.com](https://outlook.com) -vous au compte Outlook que vous avez créé au cours de la phase 2 de l'environnement de[développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d71be-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="d71be-118">Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d71be-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="d71be-119">Si vous utilisez l'environnement de développement/test d'entreprise simulé, utilisez le portail Azure ([https://portal.azure.com](https://portal.azure.com)) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de client1.</span><span class="sxs-lookup"><span data-stu-id="d71be-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="d71be-120">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="d71be-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="d71be-121">Dans **à**, tapez l'adresse de messagerie du compte User6 de votre abonnement d'évaluation ( \*\* user6@.\*\*</span><span class="sxs-lookup"><span data-stu-id="d71be-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**</span></span><organization name> <span data-ttu-id="d71be-122">**. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="d71be-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="d71be-123">Pour l’objet, saisissez **Message électronique de test 1**.</span><span class="sxs-lookup"><span data-stu-id="d71be-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="d71be-124">Dans le corps, saisissez **Brouillon de contrat Tailspin**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="d71be-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="d71be-125">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="d71be-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="d71be-126">Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="d71be-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="d71be-127">Pour l’objet, saisissez **Message électronique de test 2**.</span><span class="sxs-lookup"><span data-stu-id="d71be-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="d71be-128">Dans le corps, saisissez **Réunion Tailspin à l’heure du déjeuner**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="d71be-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="d71be-129">Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="d71be-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="d71be-130">Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="d71be-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="d71be-131">Pour l’objet, saisissez **Message électronique de test 3**.</span><span class="sxs-lookup"><span data-stu-id="d71be-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="d71be-132">Dans le corps, saisissez **Désaccord sur le contrat Tailspin**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="d71be-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="d71be-133">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="d71be-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="d71be-134">Ouvrez un nouvel onglet et connectez-vous au portail Office 365 ([https://www.office.com](https://www.office.com)) avec le nom de compte et le mot de passe du compte User6 de votre abonnement à la version d'évaluation.</span><span class="sxs-lookup"><span data-stu-id="d71be-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="d71be-135">Dans l’onglet **Portail Office 365**, cliquez sur **Courrier**.</span><span class="sxs-lookup"><span data-stu-id="d71be-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="d71be-136">Sous l'onglet **mail-User6-Outlook** , vérifiez que User6 a reçu les trois messages électroniques du compte de messagerie Outlook.</span><span class="sxs-lookup"><span data-stu-id="d71be-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="d71be-137">Revenez à l’**onglet Portail Office 365** pour User6.</span><span class="sxs-lookup"><span data-stu-id="d71be-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="d71be-138">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="d71be-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="d71be-139">Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="d71be-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="d71be-140">Dans la page **Office**, cliquez sur **Se connecter,** puis connectez-vous avec les informations d’identification de votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="d71be-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="d71be-141">dans un nouvel onglet, accédez à l'URL de votre site SharePoint de Production: **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="d71be-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="d71be-142">Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="d71be-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="d71be-143">Sur la page **Word Online**, saisissez **Brouillon de contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet de la page **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="d71be-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="d71be-144">Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.</span><span class="sxs-lookup"><span data-stu-id="d71be-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="d71be-145">	Dans l’onglet *\*Word Online*\*, saisissez *\*Notes sur le litige lié au contrat Tailspin*\*, patientez jusqu’à ce que le titre affiche *\*Enregistré*\*, puis fermez l’onglet *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="d71be-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="d71be-146">Dans l’onglet **Collection de sites de production**, Vous devriez voir **Document** et **Document1** dans la liste de documents.</span><span class="sxs-lookup"><span data-stu-id="d71be-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="d71be-147">Fermez l’onglet **Collection de sites de production**.</span><span class="sxs-lookup"><span data-stu-id="d71be-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="d71be-148">Phase 3: utiliser Advanced eDiscovery pour un litige légal</span><span class="sxs-lookup"><span data-stu-id="d71be-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="d71be-149">Malheureusement, un litige contractuel entre votre organisation et Tailspin Toys a atteint le point d’action en justice.</span><span class="sxs-lookup"><span data-stu-id="d71be-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="d71be-150">Dans cette procédure, vous créez et configurez un cas avancé de découverte électronique pour rechercher et analyser le courrier électronique et les documents qui contiennent le texte «Tailspin Contract».</span><span class="sxs-lookup"><span data-stu-id="d71be-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="d71be-151">La procédure d’utilisation d’Advanced eDiscovery est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d71be-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="d71be-152">Créez une recherche dans le centre &amp; de sécurité conformité, analysez ses résultats, puis préparez les résultats pour Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="d71be-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="d71be-153">Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="d71be-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="d71be-154">Dans cette procédure, vous créez une recherche dans le centre &amp; de sécurité conformité pour «Tailspin Contract», examinez les résultats, puis préparez les résultats pour Advanced eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="d71be-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="d71be-155">Dans l’onglet **Portail Office 365**, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="d71be-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="d71be-156">Dans le volet de navigation gauche de l’onglet Centre d’administration, cliquez sur **Centres d’administration > Conformité**.</span><span class="sxs-lookup"><span data-stu-id="d71be-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="d71be-157">Sous l' **onglet &amp; conformité de sécurité** , cliquez sur **autorisations**.</span><span class="sxs-lookup"><span data-stu-id="d71be-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="d71be-158">Dans la liste **Autorisations**, double-cliquez sur **Gestion de l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="d71be-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="d71be-159">Dans la fenêtre **Groupe de rôles**, sous **Membres**, cliquez sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="d71be-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="d71be-160">Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d71be-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="d71be-161">Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d71be-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="d71be-162">Dans la liste **Autorisations**, double-cliquez sur **Gestionnaire eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="d71be-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="d71be-163">Dans la fenêtre **Groupe de rôles**, sous **Administrateur eDiscovery**, cliquez sur l’icône plus.</span><span class="sxs-lookup"><span data-stu-id="d71be-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="d71be-164">Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d71be-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="d71be-165">Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d71be-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="d71be-166">Dans le volet de navigation de gauche, cliquez sur Search **Search &amp; > content Search**.</span><span class="sxs-lookup"><span data-stu-id="d71be-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="d71be-167">Cliquez sur l’icône plus pour ajouter une recherche.</span><span class="sxs-lookup"><span data-stu-id="d71be-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="d71be-168">Dans la fenêtre **Nouvelle recherche**, saisissez **Recherche de contrat Tailspin** dans **Nom**.</span><span class="sxs-lookup"><span data-stu-id="d71be-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="d71be-169">Dans **Dans quels emplacements voulez-vous effectuer la recherche ?**, cliquez sur **Rechercher partout**, sélectionnez **Exchange**, **SharePoint** et **Dossiers publics**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="d71be-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="d71be-170">Dans **Que voulez-vous chercher ?**, saisissez **Contrat Tailspin**, puis cliquez sur **Recherche**.</span><span class="sxs-lookup"><span data-stu-id="d71be-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="d71be-171">Dans la liste des recherches, cliquez sur le nom **Recherche de contrat Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="d71be-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="d71be-172">Dans le volet **Recherche de contrat Tailspin**, cliquez sur **Aperçu des résultats de recherche** sous **Résultats**.</span><span class="sxs-lookup"><span data-stu-id="d71be-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="d71be-173">Vous devriez voir une fenêtre répertoriant les deux documents sur le site SharePoint de production ( **document** et **Document1**) et les e-mails de **test 1** et de **courrier électronique de test 3** vers User6.</span><span class="sxs-lookup"><span data-stu-id="d71be-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="d71be-174">Fermez la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d71be-174">Close the window.</span></span>
    
19. <span data-ttu-id="d71be-175">Dans le volet **Recherche de contenu**, sous **Analyser les résultats avec Advanced eDiscovery**, cliquez sur **Aperçu des résultats pour l’analyse**.</span><span class="sxs-lookup"><span data-stu-id="d71be-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="d71be-176">Dans la fenêtre **Préparer les résultats de recherche pour la recherche de contrat Tailspin**, cliquez sur **Préparer** et attendez qu’elle se termine.</span><span class="sxs-lookup"><span data-stu-id="d71be-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="d71be-177">Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.</span><span class="sxs-lookup"><span data-stu-id="d71be-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="d71be-178">Dans le volet de navigation de gauche, cliquez sur **eDiscovery** sous \*\*enquête de recherche &amp; \*\*.</span><span class="sxs-lookup"><span data-stu-id="d71be-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="d71be-179">Dans le volet **eDiscovery**, cliquez sur **Atteindre Advanced eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="d71be-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="d71be-180">Dans l’onglet **Advanced eDiscovery**, cliquez sur l’icône plus pour ajouter un nouvel incident.</span><span class="sxs-lookup"><span data-stu-id="d71be-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="d71be-p106">	Dans le volet *\*Ajouter un incident*\*, saisissez *\*Litige de contrat Tailspin** dans *\*Nom*\*, puis cliquez sur *\*OK*\*. Attendez que l’incident soit créé.</span><span class="sxs-lookup"><span data-stu-id="d71be-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="d71be-183">Double-cliquez sur l’incident **Litige de contrat Tailspin** dans la liste. </span><span class="sxs-lookup"><span data-stu-id="d71be-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="d71be-184">Dans la liste **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis sur **traiter**.</span><span class="sxs-lookup"><span data-stu-id="d71be-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="d71be-185">Attendez la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="d71be-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="d71be-186">Lorsque le message **Processus : terminé** apparaît en bas de la fenêtre, cliquez sur **Résumé du processus** dans le volet de navigation de gauche pour afficher un résumé.</span><span class="sxs-lookup"><span data-stu-id="d71be-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="d71be-187">Dans la partie supérieure de la navigation, cliquez sur **Analyser**.</span><span class="sxs-lookup"><span data-stu-id="d71be-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="d71be-188">Dans la page **Installation**, sous **Thèmes**, saisissez **3** dans **Nombre maximal de thèmes**.</span><span class="sxs-lookup"><span data-stu-id="d71be-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="d71be-189">Cliquez sur **Analyser** et attendez que l’analyse se termine.</span><span class="sxs-lookup"><span data-stu-id="d71be-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="d71be-190">Vous devriez voir une série de graphiques en secteurs avec l’analyse de la population cible, des documents, des messages électroniques et des pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="d71be-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="d71be-191">Pour plus d'informations, consultez la rubrique [affichage des résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="d71be-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="d71be-192">Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="d71be-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d71be-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d71be-193">See Also</span></span>

[<span data-ttu-id="d71be-194">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="d71be-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d71be-195">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="d71be-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="d71be-196">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="d71be-197">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d71be-198">Sécurité des applications cloud pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d71be-199">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="d71be-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="d71be-200">eDiscovery (découverte électronique) avancée Office 365</span><span class="sxs-lookup"><span data-stu-id="d71be-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


