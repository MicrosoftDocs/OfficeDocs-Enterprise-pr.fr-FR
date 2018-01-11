---
title: "Intégration d’Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "Résumé : Utilisez ce Guide de laboratoire de test pour activer l'intégration de Dynamics 365 pour Exchange Online dans votre abonnement à la version d'évaluation d'Office 365."
ms.openlocfilehash: b297c3e461b5695b323c619145df64524989d58a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="a94ef-103">Intégration d’Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a94ef-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="a94ef-104">**Résumé :** Utilisez ce Guide de laboratoire de test pour activer l'intégration de Dynamics 365 pour Exchange Online dans votre abonnement à la version d'évaluation d'Office 365.</span><span class="sxs-lookup"><span data-stu-id="a94ef-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="a94ef-p101">Un aspect utile de Microsoft Dynamics 365 est le stockage de toutes les communications client en un seul endroit, afin que toute personne disposant des autorisations appropriées puisse voir l'ensemble des enregistrements client pertinents. Par exemple, afficher tous les e-mails associés à un contact, un compte, une opportunité ou une demande de devis en particulier.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="a94ef-p102">Pour stocker les e-mails et autres enregistrements de messagerie dans Dynamics 365, vous devez synchroniser votre système de messagerie avec Dynamics 365. La synchronisation côté serveur est la méthode de prédilection pour la synchronisation de la messagerie.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="a94ef-109">Utilisez ce Guide de laboratoire de test pour configurer et montrer la façon dont Exchange Online et le client Outlook Online peuvent exploiter les informations stockées dans Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a94ef-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="a94ef-110">Phase 1 : créer l’environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a94ef-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="a94ef-111">Suivez les instructions figurant dans la rubrique [Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) pour créer une version en mode léger ou pour entreprise simulée d'un environnement de développement/test Office 365 et Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a94ef-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a94ef-p103">La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory (AD). Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="a94ef-114">Phase 2 : configurer et montrer l'intégration Dynamics 365 dans Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a94ef-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="a94ef-115">Suivez ces étapes pour configurer la boîte aux lettres de l'administrateur général pour l'intégration de Dynamics 365 et Exchange Online :</span><span class="sxs-lookup"><span data-stu-id="a94ef-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="a94ef-116">À l’aide d’une session privée de votre navigateur, accédez à [(http://portal.office.com)]((http://portal.office.com)) et connectez-vous à l’aide de votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="a94ef-116">Using a private session of your browser, go to [((http://portal.office.com))]((http://portal.office.com)) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="a94ef-117">Sur la page **Accueil Microsoft Office**, cliquez sur la mosaïque **Messagerie**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="a94ef-118">Dans le nouvel onglet **Messagerie** de votre navigateur, cliquez sur **Nouveau** et notez que la partie inférieure du volet en dessous de la zone de saisie d'un message contient une icône pour Mes modèles.</span><span class="sxs-lookup"><span data-stu-id="a94ef-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Nouveau message électronique vide sans l’intégration à Dynamics 365.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="a94ef-120">Cliquez sur **Abandonner** et laissez l'onglet **Messagerie** ouvert.</span><span class="sxs-lookup"><span data-stu-id="a94ef-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="a94ef-121">Cliquez sur l'onglet **Accueil Microsoft Office** de votre navigateur, puis cliquez sur la mosaïque **Administration**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="a94ef-122">Dans le volet de navigation gauche de l'onglet **Centre d'administration Office**, cliquez sur **Centres d'administration > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="a94ef-123">Dans le nouvel onglet **Dynamics 365** de votre navigateur, dans la liste des instances de Dynamics 365, cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="a94ef-124">Dans le nouvel onglet **Administration** de votre navigateur, dans la barre de navigation, cliquez sur la flèche vers le bas en regard de **Paramètres**, puis cliquez sur **Configuration de la messagerie** sous **Système**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="a94ef-125">Sur la page **Configuration de la messagerie**, cliquez sur **Paramètres de configuration de la messagerie**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="a94ef-126">Dans l'onglet **Messagerie** de la boîte de dialogue **Paramètres du système**, remplacez **Rendez-vous, contacts et tâches** par **Synchronisation côté serveur**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="a94ef-127">Sur la page **Configuration de la messagerie**, cliquez sur **Boîtes aux lettres**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="a94ef-128">Sélectionnez le nom de l'administrateur général Office 365 dans la colonne de gauche, cliquez sur **Appliquer les paramètres de courrier électronique par défaut** dans la barre d'outils, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="a94ef-129">Cliquez sur **Approuver l'adresse de messagerie** dans la barre d'outils, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="a94ef-130">Sélectionnez le nom de l’administrateur général Office 365 dans la colonne de gauche, cliquez sur **Tester&amp; Activer les boîtes aux lettres** dans la barre d’outils, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="a94ef-131">Cliquez sur l'onglet **Messagerie** ouvert et vérifiez que l'administrateur général a reçu un message de test.</span><span class="sxs-lookup"><span data-stu-id="a94ef-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="a94ef-p104">Revenez à l'onglet **Boîtes aux lettres - Boîtes aux lettres actives** de votre navigateur, puis actualisez la page. Les colonnes **Statut des courriers électroniques entrants** et **Statut des courriers électroniques sortants** doivent être définies sur **Succès** pour le nom de compte d'administrateur général. Notez qu'il faut compter jusqu'à 15 minutes pour exécuter les deux tests.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="a94ef-135">Suivez ces étapes pour installer l'application Dynamics 365 pour Outlook et montrer les fonctionnalités de Dynamics 365 au sein de la boîte aux lettres de l'administrateur général :</span><span class="sxs-lookup"><span data-stu-id="a94ef-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="a94ef-136">Dans l'onglet **Boîtes aux lettres - Boîtes aux lettres actives** de votre navigateur, cliquez sur la flèche vers le bas en regard de **Paramètres**, puis cliquez sur **Application Dynamics 365 pour Outlook** sous **Système**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="a94ef-p105">Sur la page **Prise en main de l'application Microsoft Dynamics 365 pour Outlook**, cliquez sur le nom de l'administrateur général, puis cliquez sur **Ajouter l'application à Outlook**. La colonne **Statut** indique **En attente**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="a94ef-p106">Actualisez la page jusqu'à ce que le statut devienne **Ajouté à Outlook**. Notez qu'il faut compter jusqu'à 15 minutes pour exécuter cette configuration.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="a94ef-141">Cliquez sur l'onglet **Messagerie** de votre navigateur et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="a94ef-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="a94ef-142">Cliquez sur l'onglet **Accueil Microsoft Office** de votre navigateur, puis cliquez sur la mosaïque **Messagerie**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="a94ef-p107">Dans le nouvel **Messagerie** de votre navigateur, cliquez sur **Nouveau**. Vous pouvez remarquer que la partie inférieure du volet en dessous de la zone de saisie d'un message contient maintenant une icône pour Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![Nouveau message électronique vide avec l’intégration à Dynamics 365, affichant la nouvelle icône.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="a94ef-p108">Cliquez sur l'icône Dynamics 365. Vous devriez voir un volet **Dynamics 365**, à partir duquel vous pouvez suivre ces modèles de messagerie ou d'accès, de la documentation commerciale ou des articles.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="a94ef-p109">Dans le champ **À** de l'e-mail, tapez **alex.y.wu@outlook.com**, puis cliquez sur **Réessayer**dans le volet **Dynamics 365**. Vous devriez voir une section **Destinataires** dans le volet **Dynamics 365** avec des informations sur Alex Wu, un contact de l'application de vente qui a été fournie avec les exemples de données pour votre abonnement à la version d'évaluation.</span><span class="sxs-lookup"><span data-stu-id="a94ef-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Volet d’informations Dynamics 365 pour un contact commercial stocké dans Dynamics 365.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="a94ef-151">Cliquez sur **Abandonner**.</span><span class="sxs-lookup"><span data-stu-id="a94ef-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="a94ef-152">Cliquez [ici]((http://aka.ms/catlgstack)) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="a94ef-152">Click [here]((http://aka.ms/catlgstack)) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a94ef-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a94ef-153">See Also</span></span>

[<span data-ttu-id="a94ef-154">Environnement de développement/test Office 365 et Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a94ef-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="a94ef-155">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="a94ef-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a94ef-156">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="a94ef-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a94ef-157">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a94ef-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a94ef-158">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="a94ef-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

<span data-ttu-id="a94ef-159">[Gestion des abonnements pour Dynamics 365 (en ligne)]((https://technet.microsoft.com/library/jj679903.aspx))</span><span class="sxs-lookup"><span data-stu-id="a94ef-159">[Subscription Management for Dynamics 365 (online)]((https://technet.microsoft.com/library/jj679903.aspx))</span></span>
  
<span data-ttu-id="a94ef-160">[Administration de Dynamics 365]((https://technet.microsoft.com/library/dn531101.aspx))</span><span class="sxs-lookup"><span data-stu-id="a94ef-160">[Administering Dynamics 365]((https://technet.microsoft.com/library/dn531101.aspx))</span></span>


