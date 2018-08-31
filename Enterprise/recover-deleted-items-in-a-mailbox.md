---
title: Récupérer des éléments supprimés dans une boîte aux lettres utilisateur - Aide aux administrateurs
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'Cet article est destiné aux administrateurs. Un utilisateur a supprimer définitivement les éléments à partir de leur boîte aux lettres Outlook ? L’utilisateur souhaite les retour, mais ne peut pas récupérer les. Vous serez en mesure de récupérer les éléments supprimés s’ils n’ont pas été définitivement supprimés de boîte aux lettres de l’utilisateur. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540388"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="9faa7-106">Récupérer des éléments supprimés dans une boîte aux lettres utilisateur - Aide aux administrateurs</span><span class="sxs-lookup"><span data-stu-id="9faa7-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="9faa7-p102">**Cet article est destiné aux administrateurs. Vous essayez de récupérer des éléments supprimés dans votre propre boîte aux lettres ?** Essayez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="9faa7-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="9faa7-109">Récupérer des éléments supprimés dans Outlook pour Windows</span><span class="sxs-lookup"><span data-stu-id="9faa7-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="9faa7-110">Récupérer des éléments ou des messages supprimés dans Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="9faa7-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="9faa7-111">Restaurer des messages électroniques supprimés dans Outlook sur le web</span><span class="sxs-lookup"><span data-stu-id="9faa7-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="9faa7-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="9faa7-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="9faa7-p103">Un utilisateur a supprimer définitivement les éléments à partir de leur boîte aux lettres Outlook ? L’utilisateur souhaite les retour, mais ne peut pas récupérer les. Vous serez en mesure de récupérer les éléments supprimés s’ils n’ont pas été définitivement supprimés de boîte aux lettres de l’utilisateur. Pour ce faire, à l’aide de l’outil de découverte électronique In-Place dans Exchange Online pour rechercher des messages supprimés et d’autres éléments — et tels que les rendez-vous du calendrier, contacts et des tâches, dans la boîte aux lettres d’un utilisateur. Si vous trouvez les éléments supprimés, vous pouvez les exporter vers un fichier PST (également appelé un fichier de données Outlook), que l’utilisateur peut ensuite utiliser pour restaurer les éléments à leur boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="9faa7-p104">Voici les étapes de récupération des éléments supprimés dans la boîte aux lettres d’un utilisateur. Combien de temps cela prendra ? La première fois peut prendre 20 ou 30 minutes d’effectuer toutes les étapes, selon le nombre d’éléments vous essayez de récupérer.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9faa7-p105">Vous devez être un **administrateur Exchange** ou un **administrateur Global** dans Office 365 ou être membre du groupe de rôles de gestion de l’organisation dans Exchange Online pour effectuer les étapes décrites dans cet article. Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="9faa7-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="9faa7-123">Étape 1 : Vous-même attribuer des autorisations de découverte électronique</span><span class="sxs-lookup"><span data-stu-id="9faa7-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="9faa7-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-124"></span></span>

<span data-ttu-id="9faa7-p106">La première étape consiste à attribuer vous-même les autorisations nécessaires dans Exchange Online afin que vous pouvez utiliser l’outil de découverte électronique sur Place pour rechercher les boîtes aux lettres d’un utilisateur. Vous ne devez cela qu’une seule fois. Si vous disposez d’une autre boîte aux lettres de recherche à l’avenir, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="9faa7-128">[Où se connecter à Office 365 pour professionnels](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) avec votre compte professionnel ou de l’école.</span><span class="sxs-lookup"><span data-stu-id="9faa7-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="9faa7-129">Sélectionnez l’icône d’application Lanceur ![l’icône de lancement d’application dans Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) dans l’angle supérieur gauche, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="9faa7-130">Dans la centre d’administration Office 365 de navigation gauche, développez le **Centre d’administration**, puis cliquez sur **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Liste du centre d’administration](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="9faa7-132">Dans le centre d’administration Exchange, cliquez sur **autorisations**, puis cliquez sur **rôles d’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="9faa7-133">Dans la liste affichée, sélectionnez **Gestion de la recherche**, puis cliquez sur **Modifier**![icône Modifier](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span><span class="sxs-lookup"><span data-stu-id="9faa7-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Ajoutez-vous au groupe de rôles de gestion de la découverte dans le CAE](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="9faa7-135">Dans le **Groupe de rôles**, sous **membres**, cliquez sur **Ajouter**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="9faa7-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="9faa7-136">Dans la zone **Sélectionner les membres**, vous sélectionnez dans la liste des noms, cliquez sur **Ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="9faa7-p107">Vous pouvez également ajouter un groupe que vous êtes membre de, telles que la gestion de l’organisation ou TenantAdmins. Si vous ajoutez un groupe, les autres membres du groupe seront assignées les autorisations nécessaires pour exécuter l’outil de découverte électronique locale.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="9faa7-139">Dans **Groupe de rôles**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="9faa7-140">Vous déconnecter de Office 365.</span><span class="sxs-lookup"><span data-stu-id="9faa7-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="9faa7-141">Vous devez vous déconnecter avant de commencer l’étape suivante afin que les nouvelles autorisations prendra effet.</span><span class="sxs-lookup"><span data-stu-id="9faa7-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="9faa7-p108">Membres du groupe de rôles de gestion de la découverte peuvent accéder contenu des messages critiques. Cela inclut la recherche de toutes les boîtes aux lettres dans votre organisation, afficher un aperçu des résultats de la recherche (et autres éléments de boîte aux lettres), copier les résultats dans une boîte aux lettres de découverte et exporter les résultats de recherche vers un fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="9faa7-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="9faa7-145">Étape 2 : Recherche de boîte aux lettres de l’utilisateur des éléments supprimés</span><span class="sxs-lookup"><span data-stu-id="9faa7-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="9faa7-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-146"></span></span>

<span data-ttu-id="9faa7-p109">Lorsque vous exécutez une recherche de découverte électronique locale, le dossier éléments récupérables dans la boîte aux lettres que vous recherchez est automatiquement inclus dans la recherche. Le dossier éléments récupérables est où définitivement supprimés sont stockés les éléments jusqu'à ce qu’ils sont purgés (définitivement supprimé) à partir de la boîte aux lettres. Par conséquent, si un élément n’a pas été purgé, vous devez être en mesure de trouver à l’aide de l’outil de découverte électronique sur Place.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="9faa7-150">[Où se connecter à Office 365 pour professionnels](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) avec votre compte professionnel ou de l’école.</span><span class="sxs-lookup"><span data-stu-id="9faa7-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="9faa7-151">Sélectionnez l’icône d’application Lanceur ![l’icône de lancement d’application dans Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) dans l’angle supérieur gauche, cliquez sur **Admin**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="9faa7-152">Dans la navigation de gauche dans le centre d’administration d’Office 365, développez **administration**, puis cliquez sur **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="9faa7-153">Dans le centre d’administration Exchange, cliquez sur **gestion de la conformité**, cliquez sur **In-Place eDiscovery &amp; attente**, puis cliquez sur **Nouveau**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="9faa7-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Dans le centre d’administration Exchange, dans la page Gestion de la conformité, cliquez sur la découverte électronique locale et maintenez la touche](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="9faa7-155">Dans la page **nom et description** , tapez un nom pour la recherche (telles que le nom de l’utilisateur que vous êtes la récupération de message électronique), une description facultative, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="9faa7-156">Dans la page **boîtes aux lettres** , cliquez sur **spécifier les boîtes aux lettres à rechercher**, puis cliquez sur **Ajouter**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="9faa7-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Cliquez sur spécifier les boîtes aux lettres à rechercher pour rechercher une boîte aux lettres spécifique](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="9faa7-158">Recherchez et sélectionnez le nom de l’utilisateur que vous êtes le courrier électronique supprimé de la récupération, cliquez sur **Ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="9faa7-159">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-159">Click **Next**.</span></span>
    
    <span data-ttu-id="9faa7-p110">La page de **requête de recherche** s’affiche. Il s’agit d’où vous définissez les critères de recherche qui vous aidera à trouver les éléments manquants dans la boîte aux lettres de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="9faa7-162">Dans la page **Requête de recherche**, complétez les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="9faa7-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="9faa7-p111">**Inclure tous les contenus** Sélectionnez cette option pour inclure tous les contenus dans la boîte aux lettres de l’utilisateur dans les résultats de recherche. Si vous sélectionnez cette option, vous ne pouvez pas spécifier des critères de recherche supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="9faa7-165">**Filtre en fonction des critères** Sélectionnez cette option pour spécifier les critères de recherche, y compris les mots clés, de début et de fin des dates, l’expéditeur et adresses des destinataires et les types de messages.</span><span class="sxs-lookup"><span data-stu-id="9faa7-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Créer une recherche en fonction des critères tels que les mots clés, plage de dates, les destinataires et les types de messages](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="9faa7-167">**Champ**</span><span class="sxs-lookup"><span data-stu-id="9faa7-167">**Field**</span></span>|<span data-ttu-id="9faa7-168">**Utilisez cette option pour...**</span><span class="sxs-lookup"><span data-stu-id="9faa7-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Un numéro dans un cercle rose](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="9faa7-170">Spécifier des mots clés, plage de dates, les destinataires et les types de messages.</span><span class="sxs-lookup"><span data-stu-id="9faa7-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Numéro deux dans un cercle rose.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="9faa7-172">Rechercher des messages avec des mots clés ou expressions et utiliser des opérateurs logiques, tels que **AND** ou **OR**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Nombre trois dans un cercle rose.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="9faa7-174">Rechercher des messages envoyés ou reçus au sein d’une plage de dates.</span><span class="sxs-lookup"><span data-stu-id="9faa7-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![N ° 4 d’un cercle rose.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="9faa7-176">Rechercher des messages reçus d’ou envoyés à des personnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9faa7-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Numéro 5 dans un cercle rose.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="9faa7-178">Rechercher tous les types de message ou sélectionnez spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9faa7-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="9faa7-p112">Dans la page **paramètres de blocage sur Place** , cliquez sur **Terminer** pour lancer la recherche. Pour récupérer des messages électroniques supprimés, il n’existe aucune raison de placer des boîtes aux lettres de l’utilisateur en attente.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="9faa7-181">Après le démarrage de la recherche, Exchange affiche une estimation de la taille totale et le nombre d’éléments qui seront renvoyés par la recherche en fonction des critères que vous avez spécifié.</span><span class="sxs-lookup"><span data-stu-id="9faa7-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="9faa7-p113">Sélectionnez la recherche que vous venez de créer, cliquez sur **Actualiser**![Actualiser](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour les informations affichées dans le volet de détails. L’état de la **Réussite de l’estimation** indique que la recherche est terminée. Exchange affiche également une estimation du nombre total d’éléments (et leur taille) trouvés par la recherche basée sur les critères de recherche que vous avez spécifié à l’étape 9.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="9faa7-p114">Dans le volet détails, cliquez sur **Aperçu des résultats de recherche** pour afficher les éléments qui ont été détectés. Cela peut vous aider à identifier les éléments que vous recherchez. Si vous trouvez l’ou les éléments que vous souhaitez récupérer, passez à l’étape 4 pour exporter les résultats de recherche vers un fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Cliquez sur Aperçu des résultats de recherche pour afficher l’élément que vous tentez de récupérer](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="9faa7-p115">Si vous ne trouvez pas ce que vous recherchez, vous pouvez modifier vos critères de recherche en sélectionnant la recherche, cliquez sur **Modifier**![icône Modifier](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), puis en cliquant sur **requête de recherche**. Modifier les critères de recherche, puis relancez la recherche.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="9faa7-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="9faa7-192">(Facultatif) Étape 3 : Copier les résultats de recherche dans une boîte aux lettres de découverte</span><span class="sxs-lookup"><span data-stu-id="9faa7-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="9faa7-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-193"></span></span>

<span data-ttu-id="9faa7-p116">Si vous ne trouvez pas un élément en affichant un aperçu des résultats de la recherche, ou si vous souhaitez voir les éléments qui se trouvent dans le dossier éléments récupérables de l’utilisateur, puis vous pouvez copier les résultats de recherche dans une boîte aux lettres spéciale (appelée une boîte aux lettres de découverte), puis ouvrez cette boîte aux lettres dans Outlook sur le web t o permet d’afficher les éléments réels. La meilleure raison pour copier les résultats de recherche est afin d’afficher les éléments dans le dossier éléments récupérables de l’utilisateur. Plus probablement, l’élément que vous tentez de récupérer se trouve dans le sous-dossier purge.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="9faa7-197">Dans le centre d’administration Exchange, accédez à **gestion de la conformité** \> **In-Place eDiscovery &amp; contenir**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="9faa7-198">Dans la liste de recherche, sélectionnez la recherche que vous avez créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="9faa7-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="9faa7-199">Cliquez sur **recherche**![recherche](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), puis cliquez sur **Copier les résultats de recherche** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="9faa7-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Cliquez sur Rechercher, puis cliquez sur Copier les résultats de recherche](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="9faa7-201">Dans la page **Copier les résultats de recherche** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Laissez les cases à cocher non sélectionné lors de la récupération des éléments supprimés](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="9faa7-203">Sous **Nom d’affichage**, cliquez sur **Boîte aux lettres de découverte**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copier les résultats de recherche dans la boîte aux lettres de découverte par défaut](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="9faa7-205">La boîte aux lettres de découverte est une boîte aux lettres de découverte par défaut qui est automatiquement créée dans votre organisation Office 365.</span><span class="sxs-lookup"><span data-stu-id="9faa7-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="9faa7-206">Sur la page **Copier les résultats de recherche** , cliquez sur **Copier** pour démarrer le processus pour copier les résultats de recherche dans la boîte aux lettres de découverte.</span><span class="sxs-lookup"><span data-stu-id="9faa7-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Cliquez sur Copier pour copier les résultats de recherche dans la boîte aux lettres de découverte](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="9faa7-208">Cliquez sur **Actualiser**![Actualiser](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour les informations sur l’état de copie est affiché dans le volet détails.</span><span class="sxs-lookup"><span data-stu-id="9faa7-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="9faa7-209">Lorsque la copie est terminée, cliquez sur **Ouvrir** pour ouvrir la boîte aux lettres de découverte pour afficher les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="9faa7-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Cliquez sur Ouvrir pour accéder à la boîte aux lettres de découverte pour afficher les résultats de recherche](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="9faa7-p117">Les résultats de recherche copiés dans la boîte aux lettres de découverte sont placés dans un dossier qui a le même nom que la recherche de découverte électronique locale. Vous pouvez cliquer sur un dossier pour afficher les éléments dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![Résultats de recherche dans la boîte aux lettres de la recherche de découverte ; dans le dossier de purge peuvent uniquement être récupérés par un administrateur](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="9faa7-p118">Lorsque vous exécutez une recherche, dossier éléments récupérables de l’utilisateur est inclus dans la recherche. Cela signifie que si les éléments du dossier éléments récupérables aux critères de recherche, ils sont inclus dans les résultats de recherche. Éléments dans le dossier suppressions sont les éléments que l’utilisateur est définitivement supprimé (en supprimant un élément à partir du dossier éléments supprimés ou en la sélectionnant et en appuyant sur **MAJ + SUPPR**. Un utilisateur peut utiliser l’outil de récupérer les éléments supprimés dans Outlook ou Outlook sur le web pour récupérer des éléments dans le dossier de suppressions. Éléments dans le dossier de purge sont les éléments supprimé de l’utilisateur à l’aide de l’outil de récupérer les éléments supprimés ou les éléments qu’ils ont été supprimés automatiquement par une stratégie de boîte aux lettres. Dans les deux cas, seulement un administrateur peut récupérer des éléments dans le dossier de purge.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="9faa7-p119">Si un utilisateur ne peut pas trouver un élément supprimé à l’aide de l’outil d’éléments récupérables, mais que cet élément est toujours récupérable (ce qui signifie qu’il n’a pas été définitivement supprimé de la boîte aux lettres), il est probablement situé dans le dossier de purge. Par conséquent, veillez à rechercher dans le dossier de la purge de l’élément supprimé que vous tentez de récupération pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="9faa7-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="9faa7-223">Étape 4 : Exporter les résultats de recherche vers un fichier PST</span><span class="sxs-lookup"><span data-stu-id="9faa7-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="9faa7-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-224"></span></span>

<span data-ttu-id="9faa7-p120">Une fois que vous avez trouvé l’élément que vous tentez de récupération pour un utilisateur, l’étape suivante consiste à exporter les résultats de la recherche que s’est exécutée à l’étape 2 vers un fichier PST. L’utilisateur utilisera ce fichier PST à l’étape suivante pour restaurer les éléments supprimés dans leur boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="9faa7-227">Dans le centre d’administration Exchange, accédez à **gestion de la conformité** \> **In-Place eDiscovery &amp; contenir**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="9faa7-228">Dans la liste de recherche, sélectionnez la recherche que vous avez créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="9faa7-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="9faa7-229">Cliquez sur **Exporter vers un fichier PST**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-229">Click **Export to a PST file**.</span></span>
    
    ![Cliquez sur Exporter vers un fichier PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="9faa7-231">Si vous êtes invité à installer l’outil d’exportation de découverte électronique, cliquez sur **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="9faa7-232">Dans l’outil d’exportation PST eDiscovery, cliquez sur **Parcourir** pour spécifier l’emplacement où vous souhaitez télécharger le fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![L’outil d’exportation PST d’eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="9faa7-234">Vous pouvez ignorer les options pour activer la déduplication et inclure les éléments impossibles à rechercher.</span><span class="sxs-lookup"><span data-stu-id="9faa7-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="9faa7-235">Cliquez sur **Démarrer** pour télécharger le fichier sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9faa7-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="9faa7-p121">L' **outil d’exportation PST d’eDiscovery** affiche les informations sur le processus d’exportation. Une fois l’exportation terminée, vous pouvez accéder au fichier dans l’emplacement où il a été téléchargé.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="9faa7-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="9faa7-239">Étape 5 : Restaurer les éléments récupérés dans la boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="9faa7-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="9faa7-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-240"></span></span>

<span data-ttu-id="9faa7-p122">L’étape finale consiste à utiliser le fichier .pst qui a été exporté à l’étape 4 pour restaurer les éléments récupérés à la boîte aux lettres de l’utilisateur. Une fois que vous envoyez le fichier .pst à l’utilisateur, le reste de cette étape est effectué par l’utilisateur pour ouvrir le fichier PST, puis déplacez les éléments récupérés vers un autre dossier dans leur boîte aux lettres. Pour obtenir des instructions pas à pas, vous pouvez également envoyer l’utilisateur un lien à cette rubrique : [Ouvrir et fermer des fichiers de données Outlook (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Ou vous pouvez envoyer à l’utilisateur un lien vers la section [restaurer les éléments supprimés dans une boîte aux lettres à l’aide d’un fichier PST](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) ci-dessous et lui demander d’effectuer ces étapes.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="9faa7-245">**Envoyer le fichier .pst à l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="9faa7-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="9faa7-p123">La dernière étape que vous devrez effectuer envoie le fichier qui a été exporté à l’étape 4 à l’utilisateur. Il existe plusieurs façons de procéder :</span><span class="sxs-lookup"><span data-stu-id="9faa7-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="9faa7-p124">Attachez le fichier à un message électronique. Si Outlook est configurée pour bloquer PST les fichiers, puis vous devez compresser le fichier et puis de le joindre au message. Voici comment :</span><span class="sxs-lookup"><span data-stu-id="9faa7-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="9faa7-251">Dans l’Explorateur Windows ou l’Explorateur de fichiers, recherchez le fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="9faa7-p125">Cliquez sur le fichier, puis sélectionnez **Envoyer à** \> **compressés dossier compressé**. Windows crée un nouveau fichier zip et lui attribue le même nom que le fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="9faa7-254">Attacher le fichier compressé à un message électronique et l’envoyer à l’utilisateur, qui peut ensuite décompresser le fichier en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="9faa7-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="9faa7-255">Copiez le fichier dans un dossier partagé que l’utilisateur peut accéder et les récupérer.</span><span class="sxs-lookup"><span data-stu-id="9faa7-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="9faa7-256">Les étapes décrites dans la section suivante sont effectuées par l’utilisateur pour restaurer les éléments supprimés dans leur boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="9faa7-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="9faa7-257">**Restaurer des éléments supprimés dans une boîte aux lettres à l’aide d’un fichier PST**</span><span class="sxs-lookup"><span data-stu-id="9faa7-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="9faa7-p126">Vous devez utiliser l’application de bureau Outlook pour restaurer un élément supprimé à l’aide d’un fichier PST. Vous ne pouvez pas utiliser Outlook Web App ou Outlook sur le web pour ouvrir un fichier PST.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="9faa7-260">Dans Outlook 2013 ou 2016 Outlook, cliquez sur l’onglet **fichier** .</span><span class="sxs-lookup"><span data-stu-id="9faa7-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="9faa7-261">Cliquez sur **Open &amp; exporter**, puis cliquez sur **Ouvrir le fichier données Outlook**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="9faa7-262">Accédez à l’emplacement où vous avez enregistré le fichier PST qui a envoyé votre administrateur.</span><span class="sxs-lookup"><span data-stu-id="9faa7-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="9faa7-263">Sélectionnez le fichier PST, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="9faa7-264">Le fichier s’affiche dans la barre de gauche-navigation dans Outlook.</span><span class="sxs-lookup"><span data-stu-id="9faa7-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![Le fichier s’affiche dans la barre de gauche-navigation dans Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="9faa7-266">Cliquez sur les flèches pour développer le fichier PST et les dossiers sous pour localiser l’élément que vous souhaitez récupérer.</span><span class="sxs-lookup"><span data-stu-id="9faa7-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Recherchez dans le dossier vide pour l’élément que vous souhaitez récupérer](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="9faa7-p127">Recherchez dans le dossier vide pour l’élément que vous souhaitez récupérer. Il s’agit d’un dossier masqué purgés pour les éléments sont déplacés. Il est probable que l’élément de votre administrateur récupéré est dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="9faa7-271">Avec le bouton droit de l’élément que vous souhaitez récupérer, puis cliquez sur **déplacer** \> **Autre dossier**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Cliquez sur Déplacer, puis sélectionnez autre dossier](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="9faa7-273">Pour déplacer l’élément vers votre boîte de réception, cliquez sur **boîte de réception**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="9faa7-274">**Conseil :** Pour récupérer d’autres types d’éléments, effectuez l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="9faa7-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="9faa7-275">Pour récupérer un élément de calendrier, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **calendrier**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="9faa7-276">Pour récupérer un contact, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **Contacts**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="9faa7-277">Pour récupérer une tâche, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **tâches**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Sélectionnez un dossier pour déplacer les autres types d’éléments](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="9faa7-279">Lorsque vous avez terminé de récupération des éléments supprimés, cliquez sur le fichier PST dans la barre de navigation à gauche et sélectionnez **Fermer « nom du fichier PST »**.</span><span class="sxs-lookup"><span data-stu-id="9faa7-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="9faa7-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="9faa7-281">Plus d'informations</span><span class="sxs-lookup"><span data-stu-id="9faa7-281">More information</span></span>
<span data-ttu-id="9faa7-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="9faa7-282"></span></span>

- <span data-ttu-id="9faa7-p128">Il est possible pour un utilisateur de récupérer un élément définitivement supprimé si la période de rétention des éléments supprimés de l’élément n’a pas expiré. En tant qu’administrateur que peut avoir des éléments de la durée spécifiées dans le dossier éléments récupérables sont disponibles pour la récupération. Par exemple, il peut-être une stratégie qui supprime tout ce qui a été dans le dossier éléments supprimés de l’utilisateur pendant 30 jours et une autre stratégie qui permet aux utilisateurs de récupérer des éléments dans le dossier éléments récupérables pour jusqu'à un autre 14 jours. Toutefois, après cette 14 jours, vous pouvez toujours être en mesure de récupérer un élément dans la boîte aux lettres d’un utilisateur en utilisant les procédures dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9faa7-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="9faa7-p129">Les utilisateurs peuvent récupérer un élément supprimé si elle n’a pas été supprimé et si la période de rétention des éléments supprimés pour que cet élément n’a pas expiré. Pour aider les utilisateurs à récupérer les éléments supprimés dans leur boîte aux lettres, qu’ils pointent vers une des rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9faa7-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="9faa7-289">Récupérer des éléments supprimés dans Outlook pour Windows</span><span class="sxs-lookup"><span data-stu-id="9faa7-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="9faa7-290">Récupérer les éléments supprimés dans Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="9faa7-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="9faa7-291">Récupérer des éléments ou des messages supprimés dans Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="9faa7-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="9faa7-292">Restaurer des messages électroniques supprimés dans Outlook sur le web</span><span class="sxs-lookup"><span data-stu-id="9faa7-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="9faa7-293">Récupérer un contact supprimé dans Outlook</span><span class="sxs-lookup"><span data-stu-id="9faa7-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="9faa7-294">Restaurer des messages électroniques supprimés dans Outlook.com</span><span class="sxs-lookup"><span data-stu-id="9faa7-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="9faa7-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="9faa7-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

