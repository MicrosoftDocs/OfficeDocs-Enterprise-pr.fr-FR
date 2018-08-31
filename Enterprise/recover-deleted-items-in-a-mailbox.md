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
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>Récupérer des éléments supprimés dans une boîte aux lettres utilisateur - Aide aux administrateurs

**Cet article est destiné aux administrateurs. Vous essayez de récupérer des éléments supprimés dans votre propre boîte aux lettres ?** Essayez l’une des options suivantes :
- [Récupérer des éléments supprimés dans Outlook pour Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [Récupérer des éléments ou des messages supprimés dans Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [Restaurer des messages électroniques supprimés dans Outlook sur le web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
Un utilisateur a supprimer définitivement les éléments à partir de leur boîte aux lettres Outlook ? L’utilisateur souhaite les retour, mais ne peut pas récupérer les. Vous serez en mesure de récupérer les éléments supprimés s’ils n’ont pas été définitivement supprimés de boîte aux lettres de l’utilisateur. Pour ce faire, à l’aide de l’outil de découverte électronique In-Place dans Exchange Online pour rechercher des messages supprimés et d’autres éléments — et tels que les rendez-vous du calendrier, contacts et des tâches, dans la boîte aux lettres d’un utilisateur. Si vous trouvez les éléments supprimés, vous pouvez les exporter vers un fichier PST (également appelé un fichier de données Outlook), que l’utilisateur peut ensuite utiliser pour restaurer les éléments à leur boîte aux lettres.
  
Voici les étapes de récupération des éléments supprimés dans la boîte aux lettres d’un utilisateur. Combien de temps cela prendra ? La première fois peut prendre 20 ou 30 minutes d’effectuer toutes les étapes, selon le nombre d’éléments vous essayez de récupérer.
  
> [!NOTE]
> Vous devez être un **administrateur Exchange** ou un **administrateur Global** dans Office 365 ou être membre du groupe de rôles de gestion de l’organisation dans Exchange Online pour effectuer les étapes décrites dans cet article. Pour plus d’informations, voir [rôles d’administrateur sur Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d). 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>Étape 1 : Vous-même attribuer des autorisations de découverte électronique
<a name="step1"> </a>

La première étape consiste à attribuer vous-même les autorisations nécessaires dans Exchange Online afin que vous pouvez utiliser l’outil de découverte électronique sur Place pour rechercher les boîtes aux lettres d’un utilisateur. Vous ne devez cela qu’une seule fois. Si vous disposez d’une autre boîte aux lettres de recherche à l’avenir, vous pouvez ignorer cette étape.
  
1. [Où se connecter à Office 365 pour professionnels](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) avec votre compte professionnel ou de l’école. 
    
2. Sélectionnez l’icône d’application Lanceur ![l’icône de lancement d’application dans Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) dans l’angle supérieur gauche, cliquez sur **Admin**.
    
3. Dans la centre d’administration Office 365 de navigation gauche, développez le **Centre d’administration**, puis cliquez sur **Exchange**.
    
    ![Liste du centre d’administration](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. Dans le centre d’administration Exchange, cliquez sur **autorisations**, puis cliquez sur **rôles d’administrateur**.
    
5. Dans la liste affichée, sélectionnez **Gestion de la recherche**, puis cliquez sur **Modifier**![icône Modifier](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).
    
    ![Ajoutez-vous au groupe de rôles de gestion de la découverte dans le CAE](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. Dans le **Groupe de rôles**, sous **membres**, cliquez sur **Ajouter**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
7. Dans la zone **Sélectionner les membres**, vous sélectionnez dans la liste des noms, cliquez sur **Ajouter**, puis cliquez sur **OK**.
    
    > [!NOTE]
    > Vous pouvez également ajouter un groupe que vous êtes membre de, telles que la gestion de l’organisation ou TenantAdmins. Si vous ajoutez un groupe, les autres membres du groupe seront assignées les autorisations nécessaires pour exécuter l’outil de découverte électronique locale. 
  
8. Dans **Groupe de rôles**, cliquez sur **Enregistrer**.
    
9. Vous déconnecter de Office 365.
    
    Vous devez vous déconnecter avant de commencer l’étape suivante afin que les nouvelles autorisations prendra effet.
    
> [!CAUTION]
> Membres du groupe de rôles de gestion de la découverte peuvent accéder contenu des messages critiques. Cela inclut la recherche de toutes les boîtes aux lettres dans votre organisation, afficher un aperçu des résultats de la recherche (et autres éléments de boîte aux lettres), copier les résultats dans une boîte aux lettres de découverte et exporter les résultats de recherche vers un fichier PST. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>Étape 2 : Recherche de boîte aux lettres de l’utilisateur des éléments supprimés
<a name="step2"> </a>

Lorsque vous exécutez une recherche de découverte électronique locale, le dossier éléments récupérables dans la boîte aux lettres que vous recherchez est automatiquement inclus dans la recherche. Le dossier éléments récupérables est où définitivement supprimés sont stockés les éléments jusqu'à ce qu’ils sont purgés (définitivement supprimé) à partir de la boîte aux lettres. Par conséquent, si un élément n’a pas été purgé, vous devez être en mesure de trouver à l’aide de l’outil de découverte électronique sur Place.
  
1. [Où se connecter à Office 365 pour professionnels](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) avec votre compte professionnel ou de l’école. 
    
2. Sélectionnez l’icône d’application Lanceur ![l’icône de lancement d’application dans Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) dans l’angle supérieur gauche, cliquez sur **Admin**.
    
3. Dans la navigation de gauche dans le centre d’administration d’Office 365, développez **administration**, puis cliquez sur **Exchange**.
    
4. Dans le centre d’administration Exchange, cliquez sur **gestion de la conformité**, cliquez sur **In-Place eDiscovery &amp; attente**, puis cliquez sur **Nouveau**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
    ![Dans le centre d’administration Exchange, dans la page Gestion de la conformité, cliquez sur la découverte électronique locale et maintenez la touche](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. Dans la page **nom et description** , tapez un nom pour la recherche (telles que le nom de l’utilisateur que vous êtes la récupération de message électronique), une description facultative, puis cliquez sur **suivant**.
    
6. Dans la page **boîtes aux lettres** , cliquez sur **spécifier les boîtes aux lettres à rechercher**, puis cliquez sur **Ajouter**![icône Ajouter](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).
    
    ![Cliquez sur spécifier les boîtes aux lettres à rechercher pour rechercher une boîte aux lettres spécifique](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. Recherchez et sélectionnez le nom de l’utilisateur que vous êtes le courrier électronique supprimé de la récupération, cliquez sur **Ajouter**, puis cliquez sur **OK**.
    
8. Cliquez sur **Suivant**.
    
    La page de **requête de recherche** s’affiche. Il s’agit d’où vous définissez les critères de recherche qui vous aidera à trouver les éléments manquants dans la boîte aux lettres de l’utilisateur. 
    
9. Dans la page **Requête de recherche**, complétez les champs suivants : 
    
  - **Inclure tous les contenus** Sélectionnez cette option pour inclure tous les contenus dans la boîte aux lettres de l’utilisateur dans les résultats de recherche. Si vous sélectionnez cette option, vous ne pouvez pas spécifier des critères de recherche supplémentaires. 
    
  - **Filtre en fonction des critères** Sélectionnez cette option pour spécifier les critères de recherche, y compris les mots clés, de début et de fin des dates, l’expéditeur et adresses des destinataires et les types de messages. 
    
    ![Créer une recherche en fonction des critères tels que les mots clés, plage de dates, les destinataires et les types de messages](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**Champ**|**Utilisez cette option pour...**|
|:-----|:-----|
|![Un numéro dans un cercle rose](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |Spécifier des mots clés, plage de dates, les destinataires et les types de messages.  <br/> |
|![Numéro deux dans un cercle rose.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |Rechercher des messages avec des mots clés ou expressions et utiliser des opérateurs logiques, tels que **AND** ou **OR**.  <br/> |
|![Nombre trois dans un cercle rose.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |Rechercher des messages envoyés ou reçus au sein d’une plage de dates.  <br/> |
|![N ° 4 d’un cercle rose.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |Rechercher des messages reçus d’ou envoyés à des personnes spécifiques.  <br/> |
|![Numéro 5 dans un cercle rose.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |Rechercher tous les types de message ou sélectionnez spécifiques.  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. Dans la page **paramètres de blocage sur Place** , cliquez sur **Terminer** pour lancer la recherche. Pour récupérer des messages électroniques supprimés, il n’existe aucune raison de placer des boîtes aux lettres de l’utilisateur en attente. 
    
    Après le démarrage de la recherche, Exchange affiche une estimation de la taille totale et le nombre d’éléments qui seront renvoyés par la recherche en fonction des critères que vous avez spécifié.
    
11. Sélectionnez la recherche que vous venez de créer, cliquez sur **Actualiser**![Actualiser](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour les informations affichées dans le volet de détails. L’état de la **Réussite de l’estimation** indique que la recherche est terminée. Exchange affiche également une estimation du nombre total d’éléments (et leur taille) trouvés par la recherche basée sur les critères de recherche que vous avez spécifié à l’étape 9. 
    
12. Dans le volet détails, cliquez sur **Aperçu des résultats de recherche** pour afficher les éléments qui ont été détectés. Cela peut vous aider à identifier les éléments que vous recherchez. Si vous trouvez l’ou les éléments que vous souhaitez récupérer, passez à l’étape 4 pour exporter les résultats de recherche vers un fichier PST. 
    
    ![Cliquez sur Aperçu des résultats de recherche pour afficher l’élément que vous tentez de récupérer](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. Si vous ne trouvez pas ce que vous recherchez, vous pouvez modifier vos critères de recherche en sélectionnant la recherche, cliquez sur **Modifier**![icône Modifier](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), puis en cliquant sur **requête de recherche**. Modifier les critères de recherche, puis relancez la recherche.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>(Facultatif) Étape 3 : Copier les résultats de recherche dans une boîte aux lettres de découverte
<a name="step3"> </a>

Si vous ne trouvez pas un élément en affichant un aperçu des résultats de la recherche, ou si vous souhaitez voir les éléments qui se trouvent dans le dossier éléments récupérables de l’utilisateur, puis vous pouvez copier les résultats de recherche dans une boîte aux lettres spéciale (appelée une boîte aux lettres de découverte), puis ouvrez cette boîte aux lettres dans Outlook sur le web t o permet d’afficher les éléments réels. La meilleure raison pour copier les résultats de recherche est afin d’afficher les éléments dans le dossier éléments récupérables de l’utilisateur. Plus probablement, l’élément que vous tentez de récupérer se trouve dans le sous-dossier purge. 
  
1. Dans le centre d’administration Exchange, accédez à **gestion de la conformité** \> **In-Place eDiscovery &amp; contenir**.
    
2. Dans la liste de recherche, sélectionnez la recherche que vous avez créé à l’étape 2.
    
3. Cliquez sur **recherche**![recherche](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), puis cliquez sur **Copier les résultats de recherche** dans la liste déroulante. 
    
    ![Cliquez sur Rechercher, puis cliquez sur Copier les résultats de recherche](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. Dans la page **Copier les résultats de recherche** , cliquez sur **Parcourir**.
    
    ![Laissez les cases à cocher non sélectionné lors de la récupération des éléments supprimés](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. Sous **Nom d’affichage**, cliquez sur **Boîte aux lettres de découverte**, puis cliquez sur **OK**.
    
    ![Copier les résultats de recherche dans la boîte aux lettres de découverte par défaut](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > La boîte aux lettres de découverte est une boîte aux lettres de découverte par défaut qui est automatiquement créée dans votre organisation Office 365. 
  
6. Sur la page **Copier les résultats de recherche** , cliquez sur **Copier** pour démarrer le processus pour copier les résultats de recherche dans la boîte aux lettres de découverte. 
    
    ![Cliquez sur Copier pour copier les résultats de recherche dans la boîte aux lettres de découverte](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. Cliquez sur **Actualiser**![Actualiser](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour les informations sur l’état de copie est affiché dans le volet détails. 
    
8. Lorsque la copie est terminée, cliquez sur **Ouvrir** pour ouvrir la boîte aux lettres de découverte pour afficher les résultats de recherche. 
    
    ![Cliquez sur Ouvrir pour accéder à la boîte aux lettres de découverte pour afficher les résultats de recherche](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    Les résultats de recherche copiés dans la boîte aux lettres de découverte sont placés dans un dossier qui a le même nom que la recherche de découverte électronique locale. Vous pouvez cliquer sur un dossier pour afficher les éléments dans ce dossier.
    
    ![Résultats de recherche dans la boîte aux lettres de la recherche de découverte ; dans le dossier de purge peuvent uniquement être récupérés par un administrateur](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    Lorsque vous exécutez une recherche, dossier éléments récupérables de l’utilisateur est inclus dans la recherche. Cela signifie que si les éléments du dossier éléments récupérables aux critères de recherche, ils sont inclus dans les résultats de recherche. Éléments dans le dossier suppressions sont les éléments que l’utilisateur est définitivement supprimé (en supprimant un élément à partir du dossier éléments supprimés ou en la sélectionnant et en appuyant sur **MAJ + SUPPR**. Un utilisateur peut utiliser l’outil de récupérer les éléments supprimés dans Outlook ou Outlook sur le web pour récupérer des éléments dans le dossier de suppressions. Éléments dans le dossier de purge sont les éléments supprimé de l’utilisateur à l’aide de l’outil de récupérer les éléments supprimés ou les éléments qu’ils ont été supprimés automatiquement par une stratégie de boîte aux lettres. Dans les deux cas, seulement un administrateur peut récupérer des éléments dans le dossier de purge. 
    
    > [!TIP]
    > Si un utilisateur ne peut pas trouver un élément supprimé à l’aide de l’outil d’éléments récupérables, mais que cet élément est toujours récupérable (ce qui signifie qu’il n’a pas été définitivement supprimé de la boîte aux lettres), il est probablement situé dans le dossier de purge. Par conséquent, veillez à rechercher dans le dossier de la purge de l’élément supprimé que vous tentez de récupération pour un utilisateur. 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>Étape 4 : Exporter les résultats de recherche vers un fichier PST
<a name="step4"> </a>

Une fois que vous avez trouvé l’élément que vous tentez de récupération pour un utilisateur, l’étape suivante consiste à exporter les résultats de la recherche que s’est exécutée à l’étape 2 vers un fichier PST. L’utilisateur utilisera ce fichier PST à l’étape suivante pour restaurer les éléments supprimés dans leur boîte aux lettres.
  
1. Dans le centre d’administration Exchange, accédez à **gestion de la conformité** \> **In-Place eDiscovery &amp; contenir**.
    
2. Dans la liste de recherche, sélectionnez la recherche que vous avez créé à l’étape 2.
    
3. Cliquez sur **Exporter vers un fichier PST**.
    
    ![Cliquez sur Exporter vers un fichier PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. Si vous êtes invité à installer l’outil d’exportation de découverte électronique, cliquez sur **exécuter**.
    
5. Dans l’outil d’exportation PST eDiscovery, cliquez sur **Parcourir** pour spécifier l’emplacement où vous souhaitez télécharger le fichier PST. 
    
    ![L’outil d’exportation PST d’eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    Vous pouvez ignorer les options pour activer la déduplication et inclure les éléments impossibles à rechercher.
    
6. Cliquez sur **Démarrer** pour télécharger le fichier sur votre ordinateur. 
    
    L' **outil d’exportation PST d’eDiscovery** affiche les informations sur le processus d’exportation. Une fois l’exportation terminée, vous pouvez accéder au fichier dans l’emplacement où il a été téléchargé. 
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>Étape 5 : Restaurer les éléments récupérés dans la boîte aux lettres
<a name="step5"> </a>

L’étape finale consiste à utiliser le fichier .pst qui a été exporté à l’étape 4 pour restaurer les éléments récupérés à la boîte aux lettres de l’utilisateur. Une fois que vous envoyez le fichier .pst à l’utilisateur, le reste de cette étape est effectué par l’utilisateur pour ouvrir le fichier PST, puis déplacez les éléments récupérés vers un autre dossier dans leur boîte aux lettres. Pour obtenir des instructions pas à pas, vous pouvez également envoyer l’utilisateur un lien à cette rubrique : [Ouvrir et fermer des fichiers de données Outlook (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Ou vous pouvez envoyer à l’utilisateur un lien vers la section [restaurer les éléments supprimés dans une boîte aux lettres à l’aide d’un fichier PST](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) ci-dessous et lui demander d’effectuer ces étapes. 
  
 **Envoyer le fichier .pst à l’utilisateur**
  
La dernière étape que vous devrez effectuer envoie le fichier qui a été exporté à l’étape 4 à l’utilisateur. Il existe plusieurs façons de procéder :
  
- Attachez le fichier à un message électronique. Si Outlook est configurée pour bloquer PST les fichiers, puis vous devez compresser le fichier et puis de le joindre au message. Voici comment :
    
1. Dans l’Explorateur Windows ou l’Explorateur de fichiers, recherchez le fichier PST.
    
2. Cliquez sur le fichier, puis sélectionnez **Envoyer à** \> **compressés dossier compressé**. Windows crée un nouveau fichier zip et lui attribue le même nom que le fichier PST.
    
3. Attacher le fichier compressé à un message électronique et l’envoyer à l’utilisateur, qui peut ensuite décompresser le fichier en cliquant dessus.
    
- Copiez le fichier dans un dossier partagé que l’utilisateur peut accéder et les récupérer.
    
Les étapes décrites dans la section suivante sont effectuées par l’utilisateur pour restaurer les éléments supprimés dans leur boîte aux lettres.
  
 **Restaurer des éléments supprimés dans une boîte aux lettres à l’aide d’un fichier PST**
  
Vous devez utiliser l’application de bureau Outlook pour restaurer un élément supprimé à l’aide d’un fichier PST. Vous ne pouvez pas utiliser Outlook Web App ou Outlook sur le web pour ouvrir un fichier PST.
  
1. Dans Outlook 2013 ou 2016 Outlook, cliquez sur l’onglet **fichier** . 
    
2. Cliquez sur **Open &amp; exporter**, puis cliquez sur **Ouvrir le fichier données Outlook**.
    
3. Accédez à l’emplacement où vous avez enregistré le fichier PST qui a envoyé votre administrateur.
    
4. Sélectionnez le fichier PST, puis cliquez sur **Ouvrir**.
    
    Le fichier s’affiche dans la barre de gauche-navigation dans Outlook.
    
    ![Le fichier s’affiche dans la barre de gauche-navigation dans Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. Cliquez sur les flèches pour développer le fichier PST et les dossiers sous pour localiser l’élément que vous souhaitez récupérer.
    
    ![Recherchez dans le dossier vide pour l’élément que vous souhaitez récupérer](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > Recherchez dans le dossier vide pour l’élément que vous souhaitez récupérer. Il s’agit d’un dossier masqué purgés pour les éléments sont déplacés. Il est probable que l’élément de votre administrateur récupéré est dans ce dossier. 
  
6. Avec le bouton droit de l’élément que vous souhaitez récupérer, puis cliquez sur **déplacer** \> **Autre dossier**.
    
    ![Cliquez sur Déplacer, puis sélectionnez autre dossier](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. Pour déplacer l’élément vers votre boîte de réception, cliquez sur **boîte de réception**, puis cliquez sur **OK**.
    
    **Conseil :** Pour récupérer d’autres types d’éléments, effectuez l’une des options suivantes : 
    
  - Pour récupérer un élément de calendrier, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **calendrier**.
    
  - Pour récupérer un contact, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **Contacts**.
    
  - Pour récupérer une tâche, droit dessus, puis cliquez sur **déplacer** \> **Autre dossier** \> **tâches**.
    
![Sélectionnez un dossier pour déplacer les autres types d’éléments](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. Lorsque vous avez terminé de récupération des éléments supprimés, cliquez sur le fichier PST dans la barre de navigation à gauche et sélectionnez **Fermer « nom du fichier PST »**.
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>Plus d'informations
<a name="moreinfo"> </a>

- Il est possible pour un utilisateur de récupérer un élément définitivement supprimé si la période de rétention des éléments supprimés de l’élément n’a pas expiré. En tant qu’administrateur que peut avoir des éléments de la durée spécifiées dans le dossier éléments récupérables sont disponibles pour la récupération. Par exemple, il peut-être une stratégie qui supprime tout ce qui a été dans le dossier éléments supprimés de l’utilisateur pendant 30 jours et une autre stratégie qui permet aux utilisateurs de récupérer des éléments dans le dossier éléments récupérables pour jusqu'à un autre 14 jours. Toutefois, après cette 14 jours, vous pouvez toujours être en mesure de récupérer un élément dans la boîte aux lettres d’un utilisateur en utilisant les procédures dans cette rubrique.
    
- Les utilisateurs peuvent récupérer un élément supprimé si elle n’a pas été supprimé et si la période de rétention des éléments supprimés pour que cet élément n’a pas expiré. Pour aider les utilisateurs à récupérer les éléments supprimés dans leur boîte aux lettres, qu’ils pointent vers une des rubriques suivantes :
    
  - [Récupérer des éléments supprimés dans Outlook pour Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Récupérer les éléments supprimés dans Outlook 2010](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [Récupérer des éléments ou des messages supprimés dans Outlook Web App](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [Restaurer des messages électroniques supprimés dans Outlook sur le web](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [Récupérer un contact supprimé dans Outlook](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [Restaurer des messages électroniques supprimés dans Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  

