---
title: Ajouter plusieurs utilisateurs simultanément à Office 365 - Aide de l'administrateur
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: "Découvrez comment ajouter plusieurs utilisateurs à Office 365 pour les entreprises à partir d'une liste dans une feuille de calcul ou dans un autre fichier au format CSV. Regardez une vidéo sur YouTube qui explique comment ajouter des comptes à Office 365. À la fin de ce processus, chaque utilisateur disposant d'un compte dispose d'une boîte aux lettres Office 365. "
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491500"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="080a4-105">Ajouter plusieurs utilisateurs simultanément à Office 365 - Aide de l’administrateur</span><span class="sxs-lookup"><span data-stu-id="080a4-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="080a4-p102">[] Les membres de votre équipe ont besoin d'un compte d'utilisateur pour pouvoir se connecter et accéder aux services Office 365, tels que le courrier et Office. Si votre équipe compte de nombreux membres, vous pouvez ajouter tous leurs comptes simultanément à partir d'une feuille de calcul Excel ou d'un autre fichier enregistré au format CSV. [Qu'est-ce que le format CSV ?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="080a4-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="080a4-109">Ajouter plusieurs utilisateurs à Office 365 dans le Centre d'administration Office 365</span><span class="sxs-lookup"><span data-stu-id="080a4-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="080a4-110">Connectez-vous à Office 365 avec votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="080a4-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="080a4-111">Dans le Centre d'administration Office 365, sélectionnez **Utilisateurs** \> **Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="080a4-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![In the Admin center choose Users and then Active users](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="080a4-113">Dans le menu déroulant **Autres**, choisissez **Importer plusieurs utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="080a4-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="080a4-114">Dans le panneau **Importer plusieurs utilisateurs**, vous pouvez éventuellement télécharger un exemple de fichier CSV avec ou sans exemple de données inclus.</span><span class="sxs-lookup"><span data-stu-id="080a4-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="080a4-116">Votre feuille de calcul doit inclure les **mêmes en-têtes de colonne** que ceux de l'exemple (Nom d'utilisateur, Prénom, etc.). Si vous utilisez le modèle, ouvrez-le dans un outil d'édition de texte tel que Notepad, laissez les données de la ligne 1 inchangées et entrez uniquement des données dans la ligne 2 et les lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="080a4-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="080a4-117">Votre feuille de calcul doit également inclure des valeurs pour le nom d'utilisateur (tel que alexandre@contoso.com) et un nom complet (tel que Alexandre Chauvin) pour chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="080a4-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="080a4-118">Entrez un chemin d'accès dans la zone, ou choisissez **Parcourir** pour accéder à l'emplacement du fichier CSV, puis sélectionnez **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="080a4-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="080a4-p103">S'il existe des problèmes avec le fichier, ceux-ci s'affichent dans le panneau. Vous pouvez également télécharger un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="080a4-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="080a4-122">Dans la boîte de dialogue **Définir les options utilisateur**, vous pouvez définir le statut de connexion et choisir la licence produit à affecter à tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="080a4-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="080a4-123">Dans la boîte de dialogue **Affichez vos résultats**, vous pouvez choisir d'envoyer les résultats à vous-même ou à d'autres utilisateurs (les mots de passe seront au format texte brut). En outre, vous pouvez voir combien d'utilisateurs ont été créés et si vous avez besoin d'acheter des licences supplémentaires pour les attribuer à certains des nouveaux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="080a4-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="080a4-124">Voir la vidéo</span><span class="sxs-lookup"><span data-stu-id="080a4-124">Watch the video</span></span>
<span data-ttu-id="080a4-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="080a4-125"></span></span>

 <span data-ttu-id="080a4-126">Regardez une courte vidéo qui vous montre comment ajouter des utilisateurs en bloc.</span><span class="sxs-lookup"><span data-stu-id="080a4-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="080a4-127">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="080a4-127">Next steps</span></span>
<span data-ttu-id="080a4-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="080a4-128"></span></span>

- <span data-ttu-id="080a4-129">À présent que ces personnes ont des comptes, elles doivent [Télécharger et installer ou réinstaller office 365 ou office 2016 sur un PC ou un Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="080a4-129">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="080a4-130">Chaque membre de votre équipe peut installer Office 365 sur un maximum de 5 PC ou Mac.</span><span class="sxs-lookup"><span data-stu-id="080a4-130">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="080a4-131">Chaque personne peut également [configurer les applications Office et le courrier électronique sur un appareil mobile sur un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) maximum de 5 tablettes et 5 téléphones, comme des iPhone, des iPad et des tablettes et tablettes Android.</span><span class="sxs-lookup"><span data-stu-id="080a4-131">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="080a4-132">Ainsi, ils peuvent modifier les fichiers Office à partir de n'importe quel endroit.</span><span class="sxs-lookup"><span data-stu-id="080a4-132">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="080a4-133">Voir [Configurer Office 365 pour les entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) pour obtenir une liste de bout en bout des étapes de configuration.</span><span class="sxs-lookup"><span data-stu-id="080a4-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="080a4-134">Informations complémentaires sur l'ajout d'utilisateurs à Office 365</span><span class="sxs-lookup"><span data-stu-id="080a4-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="080a4-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="080a4-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="080a4-136">Qu'est-ce que le format CSV ?</span><span class="sxs-lookup"><span data-stu-id="080a4-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="080a4-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="080a4-137"></span></span>

<span data-ttu-id="080a4-p106">Un fichier CSV inclut des valeurs séparées par des virgules. Vous pouvez créer ou modifier un fichier comme celui-ci avec un éditeur de texte ou un tableur comme Excel.</span><span class="sxs-lookup"><span data-stu-id="080a4-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="080a4-p107">Vous pouvez télécharger [cet exemple de feuille de calcul](https://www.microsoft.com/en-us/download/details.aspx?id=45485) pour commencer. Rappelez-vous qu'Office 365 nécessite des en-têtes de colonne dans la première ligne, aussi ne les remplacez pas par d'autres informations.</span><span class="sxs-lookup"><span data-stu-id="080a4-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="080a4-142">Enregistrez le fichier avec un nouveau nom et spécifiez le format CSV.</span><span class="sxs-lookup"><span data-stu-id="080a4-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Image expliquant comment enregistrer un fichier au format CSV dans Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="080a4-p108">Une fois le fichier enregistré, il est probable qu'un message indiquant que certaines fonctionnalités de votre classeur seront perdues si vous enregistrez le fichier au format CSV s'affiche. Ceci est normal. Cliquez sur **Oui** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="080a4-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Image de l'invite rencontrée dans Excel vous demandant si vous voulez vraiment enregistrer le fichier au format CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="080a4-148">Conseils pour la mise en forme de votre feuille de calcul</span><span class="sxs-lookup"><span data-stu-id="080a4-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="080a4-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="080a4-149"></span></span>

- <span data-ttu-id="080a4-p109">**Ai-je besoin des mêmes en-têtes de colonne que dans l'exemple de feuille de calcul ?** Oui. La première ligne de l'exemple de feuille de calcul inclut les en-têtes de colonne. Ces en-têtes sont obligatoires. Pour chaque utilisateur que vous voulez ajouter à Office 365, créez une ligne sous l'en-tête. Si vous ajoutez, modifiez ou supprimez l'un des en-têtes de colonne, il est possible qu'Office 365 ne puisse pas créer des utilisateurs à partir des informations du fichier.</span><span class="sxs-lookup"><span data-stu-id="080a4-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="080a4-p110">**Que faire si je n'ai pas toutes les informations requises pour chaque utilisateur ?** Le nom de l'utilisateur et le nom d'affichage sont obligatoires. Vous ne pouvez pas ajouter un nouvel utilisateur sans ces informations. S'il vous manque d'autres informations, par exemple le numéro de télécopie, vous pouvez insérer un espace suivi d'une virgule pour indiquer que le champ est vide.</span><span class="sxs-lookup"><span data-stu-id="080a4-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="080a4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="080a4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="080a4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="080a4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="080a4-p113">**Que dois-je faire si j'ajoute des utilisateurs de régions ou de pays différents ?** Créez une feuille de calcul distincte pour chaque zone. Vous devez exécuter l'Assistant Ajouter des utilisateurs en bloc avec chaque feuille de calcul, et donner ainsi un seul emplacement à tous les utilisateurs inclus dans le fichier que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="080a4-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="080a4-p114">**Le nombre de caractères que je peux utiliser est-il limité ?** Le tableau suivant indique les étiquettes de colonne des données utilisateur et le nombre maximal de caractères autorisés pour chacune d'elles dans l'exemple de feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="080a4-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="080a4-172">**Étiquette de colonne des données utilisateur**</span><span class="sxs-lookup"><span data-stu-id="080a4-172">**User data column label**</span></span>|<span data-ttu-id="080a4-173">**Longueur de caractères maximale**</span><span class="sxs-lookup"><span data-stu-id="080a4-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="080a4-174">Nom d'utilisateur (requis)</span><span class="sxs-lookup"><span data-stu-id="080a4-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="080a4-p115">79 avec le symbole arobase (@), au format nom@domaine.\<extension\>. L'alias de l'utilisateur ne peut pas dépasser 30 caractères, et le nom de domaine 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="080a4-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="080a4-177">Prénom</span><span class="sxs-lookup"><span data-stu-id="080a4-177">First Name</span></span>  <br/> |<span data-ttu-id="080a4-178">64</span><span class="sxs-lookup"><span data-stu-id="080a4-178">64</span></span>  <br/> |
|<span data-ttu-id="080a4-179">Nom</span><span class="sxs-lookup"><span data-stu-id="080a4-179">Last Name</span></span>  <br/> |<span data-ttu-id="080a4-180">64</span><span class="sxs-lookup"><span data-stu-id="080a4-180">64</span></span>  <br/> |
|<span data-ttu-id="080a4-181">Nom d'affichage (requis)</span><span class="sxs-lookup"><span data-stu-id="080a4-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="080a4-182">256</span><span class="sxs-lookup"><span data-stu-id="080a4-182">256</span></span>  <br/> |
|<span data-ttu-id="080a4-183">Poste</span><span class="sxs-lookup"><span data-stu-id="080a4-183">Job Title</span></span>  <br/> |<span data-ttu-id="080a4-184">64</span><span class="sxs-lookup"><span data-stu-id="080a4-184">64</span></span>  <br/> |
|<span data-ttu-id="080a4-185">Service</span><span class="sxs-lookup"><span data-stu-id="080a4-185">Department</span></span>  <br/> |<span data-ttu-id="080a4-186">64</span><span class="sxs-lookup"><span data-stu-id="080a4-186">64</span></span>  <br/> |
|<span data-ttu-id="080a4-187">Numéro du bureau</span><span class="sxs-lookup"><span data-stu-id="080a4-187">Office Number</span></span>  <br/> |<span data-ttu-id="080a4-188">128</span><span class="sxs-lookup"><span data-stu-id="080a4-188">128</span></span>  <br/> |
|<span data-ttu-id="080a4-189">Téléphone (bureau)</span><span class="sxs-lookup"><span data-stu-id="080a4-189">Office Phone</span></span>  <br/> |<span data-ttu-id="080a4-190">64</span><span class="sxs-lookup"><span data-stu-id="080a4-190">64</span></span>  <br/> |
|<span data-ttu-id="080a4-191">Téléphone mobile</span><span class="sxs-lookup"><span data-stu-id="080a4-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="080a4-192">64</span><span class="sxs-lookup"><span data-stu-id="080a4-192">64</span></span>  <br/> |
|<span data-ttu-id="080a4-193">Télécopie</span><span class="sxs-lookup"><span data-stu-id="080a4-193">Fax</span></span>  <br/> |<span data-ttu-id="080a4-194">64</span><span class="sxs-lookup"><span data-stu-id="080a4-194">64</span></span>  <br/> |
|<span data-ttu-id="080a4-195">Adresse</span><span class="sxs-lookup"><span data-stu-id="080a4-195">Address</span></span>  <br/> |<span data-ttu-id="080a4-196">1023</span><span class="sxs-lookup"><span data-stu-id="080a4-196">1023</span></span>  <br/> |
|<span data-ttu-id="080a4-197">Ville</span><span class="sxs-lookup"><span data-stu-id="080a4-197">City</span></span>  <br/> |<span data-ttu-id="080a4-198">128</span><span class="sxs-lookup"><span data-stu-id="080a4-198">128</span></span>  <br/> |
|<span data-ttu-id="080a4-199">Département ou région</span><span class="sxs-lookup"><span data-stu-id="080a4-199">State or Province</span></span>  <br/> |<span data-ttu-id="080a4-200">128</span><span class="sxs-lookup"><span data-stu-id="080a4-200">128</span></span>  <br/> |
|<span data-ttu-id="080a4-201">Code postal</span><span class="sxs-lookup"><span data-stu-id="080a4-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="080a4-202">40</span><span class="sxs-lookup"><span data-stu-id="080a4-202">40</span></span>  <br/> |
|<span data-ttu-id="080a4-203">Pays ou région</span><span class="sxs-lookup"><span data-stu-id="080a4-203">Country or Region</span></span>  <br/> |<span data-ttu-id="080a4-204">128</span><span class="sxs-lookup"><span data-stu-id="080a4-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="080a4-205">Vous rencontrez encore des problèmes lorsque vous ajoutez des utilisateurs à Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="080a4-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="080a4-p116">**Vérifiez que la feuille de calcul est correctement mise en forme.** Examinez les en-têtes des colonnes pour vous assurer qu'ils correspondent à ceux de l'exemple de fichier. Veillez à respecter le nombre de caractères autorisés et assurez-vous que chaque champ est séparé par une virgule.</span><span class="sxs-lookup"><span data-stu-id="080a4-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="080a4-p117">\*\* Si les nouveaux utilisateurs n'apparaissent pas tout de suite dans Office 365, patientez quelques minutes. \*\* La répercussion des modifications dans tous les services d'Office 365 peut prendre du temps.</span><span class="sxs-lookup"><span data-stu-id="080a4-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="080a4-211">Ajouter plusieurs utilisateurs à Office 365 dans l'ancien Centre d'administration Office 365</span><span class="sxs-lookup"><span data-stu-id="080a4-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="080a4-212">Téléchargez [cet exemple de feuille de calcul](https://www.microsoft.com/en-us/download/details.aspx?id=45485) et ouvrez-la dans Excel.</span><span class="sxs-lookup"><span data-stu-id="080a4-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="080a4-213">Votre feuille de calcul doit inclure les **mêmes en-têtes de colonne** que ceux de l'exemple (Nom d'utilisateur, Prénom, etc.). Si vous utilisez le modèle, laissez les données de la ligne 1 inchangées et entrez uniquement des données dans la ligne 2 et les lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="080a4-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="080a4-p118">Votre feuille de calcul doit également inclure des valeurs pour le nom d'utilisateur (tel que alexandre@contoso.com) et un nom complet (tel que Alexandre Chauvin) pour chaque utilisateur. Pour laisser les autres champs vides, entrez un espace plus une virgule dans le champ, comme illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="080a4-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Exemple de fichier CSV comportant des lignes vides](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="080a4-p119">Si des membres de votre organisation travaillent dans différents pays ou régions, vous devez créer une feuille de calcul pour les utilisateurs de chaque pays ou région. Par exemple, une feuille de calcul peut répertorier toutes les personnes travaillant aux États-Unis, tandis que l'autre répertorie celles travaillant au Japon. En effet, la disponibilité des services Office 365 varie selon la région.</span><span class="sxs-lookup"><span data-stu-id="080a4-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="080a4-p120">**Conseil :** avant d'ajouter un grand nombre d'utilisateurs à Office 365, vous voudrez peut-être vous exercer avec l'exemple de feuille de calcul. Par exemple, modifiez l'exemple de feuille de calcul avec les données de quelques utilisateurs (5 ou 10 utilisateurs) et enregistrez le fichier avec un nouveau nom. Parcourez les étapes décrites dans cette procédure, consultez les résultats, supprimez les nouveaux comptes et recommencez. Vous pouvez ainsi vous entraîner à recevoir l'ensemble des données adaptées à votre situation. Consultez également la section [Conseils pour la mise en forme de votre feuille de calcul](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="080a4-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="080a4-225">Connectez-vous à Office 365 avec votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="080a4-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="080a4-226">Accédez au Centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="080a4-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="080a4-p121">Pour que les personnes puissent utiliser les services Office 365, une licence doit leur être attribuée. Avant de continuer, vous voudrez peut-être vérifier que vous avez suffisamment de licences pour les personnes mentionnées dans votre feuille de calcul. Sélectionnez **Facturation** \> **Abonnements** pour déterminer si vous en avez assez. Si vous avez besoin d'acheter d'autres licences, sélectionnez \*\* Modifier le nombre de licences \*\*. Vous pouvez également exécuter l'Assistant et attribuer les licences que vous avez, puis acheter d'autres licences plus tard et réexécuter l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="080a4-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="080a4-p122">Accédez ensuite à l'Assistant Ajouter des utilisateurs en bloc : sélectionnez **Utilisateurs** \> **Utilisateurs actifs**. Sélectionnez ![Icône pour l'ajout de plusieurs utilisateurs à Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) comme illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="080a4-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Image de la section Utilisateurs du Centre d'administration Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="080a4-235">L'Assistant Ajouter des utilisateurs en bloc apparaît et vous guide dans l'ajout d'un groupe d'utilisateurs à Office 365.</span><span class="sxs-lookup"><span data-stu-id="080a4-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="080a4-236">Dans l'étape 1 (Sélectionner un fichier CSV), spécifiez votre propre feuille de calcul comme illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="080a4-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Étape 1 de l'Assistant Ajouter des utilisateurs en bloc - Sélectionner un fichier CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="080a4-238">Dans l'étape 2 (Vérification), l'Assistant vous indique si le contenu de la feuille de calcul est correctement mis en forme.</span><span class="sxs-lookup"><span data-stu-id="080a4-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Étape 2 de l'Assistant Ajouter des utilisateurs en bloc - Vérification](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="080a4-p123">Dans l'étape 3 (Paramètres), sélectionnez **Autorisé** de telle sorte que les personnes qui apparaissent dans votre feuille de calcul puissent utiliser Office 365. Sélectionnez également le pays ou la région dans lequel ces personnes utiliseront Office 365. Rappelez-vous que si certains membres de votre organisation utiliseront Office 365 dans un autre pays ou dans une autre région, créez une feuille de calcul distincte avec leurs noms et exécutez l'Assistant Ajouter des utilisateurs en bloc pour les ajouter.</span><span class="sxs-lookup"><span data-stu-id="080a4-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Étape 3 de l'Assistant Ajouter des utilisateurs en bloc - Paramètres](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="080a4-244">La page Attribuer des licences indique le nombre de licences disponibles.</span><span class="sxs-lookup"><span data-stu-id="080a4-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Étape 4 de l'Assistant Ajouter des utilisateurs en bloc - Licences](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="080a4-p124">Vous pouvez sélectionner **Acheter de nouvelles licences**, mais vous quitterez alors l'Assistant Ajouter des utilisateurs en bloc et accéderez à la **facturation** dans le portail Centre d'administration Office 365. Après avoir acheté d'autres licences, vous devez patienter quelques minutes que la commande soit traitée, puis réexécuter l'Assistant Ajouter des utilisateurs en bloc depuis le début.</span><span class="sxs-lookup"><span data-stu-id="080a4-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="080a4-248">Si vous n'achetez pas d'autres licences, les comptes ne seront pas créés pour toutes les personnes figurant dans votre feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="080a4-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="080a4-249">Dans cet exemple, nous n'achetons pas d'autres licences et continuons avec l'Assistant Ajouter des utilisateurs en bloc.</span><span class="sxs-lookup"><span data-stu-id="080a4-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="080a4-250">Dans l'étape 5 (Envoyer les résultats), tapez les adresses de courrier dont vous voulez recevoir un message répertoriant  *tous*  les noms d'utilisateur Office 365 et mots de passe temporaires pour les personnes figurant dans la feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="080a4-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Étape 5 de l'Assistant Ajouter des utilisateurs en bloc - Envoyer les résultats](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="080a4-p125">Le message suivant est envoyé à toutes les adresses de courrier que vous avez spécifiées à l'étape 5 (Envoyer les résultats). Ce message indique les comptes qui ont été créés. Notez qu'aucun compte n'a été créé pour certaines personnes, car les licences n'étaient pas suffisantes.</span><span class="sxs-lookup"><span data-stu-id="080a4-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Courrier d'exemple avec les informations d'identification d'un utilisateur](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="080a4-p126">Vous pouvez acheter d'autres licences ultérieurement et réexécuter l'Assistant Ajouter des utilisateurs en bloc avec la même feuille de calcul. L'Assistant ignore les utilisateurs qui ont déjà des comptes. Le rapport de résultats inclura la mention « Nom d'utilisateur dupliqué ». Celle-ci indique qu'une personne dotée de ces informations possède déjà un compte.</span><span class="sxs-lookup"><span data-stu-id="080a4-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="080a4-258">La page finale de l'Assistant Ajouter des utilisateurs en bloc répertorie les noms d'utilisateur et mots de passe temporaires, comme illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="080a4-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Étape 6 de l'Assistant Ajouter des utilisateurs en bloc - Envoyer les résultats](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="080a4-p127">Une fois que vous avez ajouté des utilisateurs à Office 365, vous devez leur communiquer leurs informations de compte Office 365. Nous vous conseillons d'utiliser le processus normal pour communiquer les nouveaux mots de passe.</span><span class="sxs-lookup"><span data-stu-id="080a4-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

