---
title: Ajouter plusieurs utilisateurs en même temps à Microsoft 365-aide de l’administrateur
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
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
description: 'Découvrez comment ajouter plusieurs utilisateurs à Microsoft 365 pour les entreprises à partir d’une liste dans une feuille de calcul ou dans un autre fichier au format CSV. Regardez une vidéo sur YouTube qui explique comment ajouter des comptes à Microsoft 365. À la fin de ce processus, chaque utilisateur disposant d’un compte dispose d’une boîte aux lettres Microsoft 365. '
ms.openlocfilehash: 88c83b7163bfa6d389995704595d80458ddc8198
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "44699241"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a><span data-ttu-id="4f736-105">Ajouter plusieurs utilisateurs en même temps à Microsoft 365-aide de l’administrateur</span><span class="sxs-lookup"><span data-stu-id="4f736-105">Add several users at the same time to Microsoft 365 - Admin Help</span></span>

<span data-ttu-id="4f736-106">Chaque membre de votre équipe doit disposer d’un compte d’utilisateur avant de pouvoir se connecter et accéder aux services Microsoft 365, tels que la messagerie électronique et Office.</span><span class="sxs-lookup"><span data-stu-id="4f736-106">Each person on your team needs a user account before they can sign in and access Microsoft 365 services, such as email and Office.</span></span> <span data-ttu-id="4f736-107">Si votre équipe compte de nombreux membres, vous pouvez ajouter tous leurs comptes simultanément à partir d'une feuille de calcul Excel ou d'un autre fichier enregistré au format CSV.</span><span class="sxs-lookup"><span data-stu-id="4f736-107">If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format.</span></span> [<span data-ttu-id="4f736-108">Qu'est-ce que le format CSV ?</span><span class="sxs-lookup"><span data-stu-id="4f736-108">Not sure what CSV format is?</span></span>](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> <span data-ttu-id="4f736-109">Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.</span><span class="sxs-lookup"><span data-stu-id="4f736-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a><span data-ttu-id="4f736-110">Ajouter plusieurs utilisateurs dans le centre d’administration Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4f736-110">Add multiple users in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="4f736-111">Connectez-vous à Microsoft 365 à l’aide de votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="4f736-111">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="4f736-112">Dans le centre d’administration, **Choisissez utilisateurs** \> **actifs**.</span><span class="sxs-lookup"><span data-stu-id="4f736-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="4f736-113">Sélectionnez **ajouter plusieurs utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="4f736-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="4f736-114">Dans le panneau **Importer plusieurs utilisateurs**, vous pouvez éventuellement télécharger un exemple de fichier CSV avec ou sans exemple de données inclus.</span><span class="sxs-lookup"><span data-stu-id="4f736-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="4f736-115">Votre feuille de calcul doit inclure les **mêmes en-têtes de colonne** que ceux de l'exemple (Nom d'utilisateur, Prénom, etc.). Si vous utilisez le modèle, ouvrez-le dans un outil d'édition de texte tel que Notepad, laissez les données de la ligne 1 inchangées et entrez uniquement des données dans la ligne 2 et les lignes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4f736-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="4f736-116">Votre feuille de calcul doit également inclure des valeurs pour le nom d'utilisateur (tel que alexandre@contoso.com) et un nom complet (tel que Alexandre Chauvin) pour chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4f736-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="4f736-117">Entrez un chemin d'accès dans la zone, ou choisissez **Parcourir** pour accéder à l'emplacement du fichier CSV, puis sélectionnez **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="4f736-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="4f736-p103">S'il existe des problèmes avec le fichier, ceux-ci s'affichent dans le panneau. Vous pouvez également télécharger un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="4f736-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="4f736-120">Dans la boîte de dialogue **Définir les options utilisateur**, vous pouvez définir le statut de connexion et choisir la licence produit à affecter à tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4f736-120">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="4f736-121">Dans la boîte de dialogue **Affichez vos résultats**, vous pouvez choisir d'envoyer les résultats à vous-même ou à d'autres utilisateurs (les mots de passe seront au format texte brut). En outre, vous pouvez voir combien d'utilisateurs ont été créés et si vous avez besoin d'acheter des licences supplémentaires pour les attribuer à certains des nouveaux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4f736-121">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="4f736-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4f736-122">Next steps</span></span>
<span data-ttu-id="4f736-123"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="4f736-123"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="4f736-124">À présent que ces personnes disposent de comptes, elles doivent [Télécharger et installer ou réinstaller Microsoft 365 ou Office 2016 sur un PC ou un Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="4f736-124">Now that these people have accounts, they need to [Download and install or reinstall Microsoft 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="4f736-125">Chaque membre de votre équipe peut installer Microsoft 365 sur un maximum de 5 PC ou Mac.</span><span class="sxs-lookup"><span data-stu-id="4f736-125">Each person on your team can install Microsoft 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="4f736-126">Chaque personne peut également [configurer les applications Office et le courrier électronique sur un appareil mobile sur un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) maximum de 5 tablettes et 5 téléphones, comme des iPhone, des iPad et des tablettes et tablettes Android.</span><span class="sxs-lookup"><span data-stu-id="4f736-126">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="4f736-127">Ainsi, ils peuvent modifier les fichiers Office à partir de n’importe quel endroit.</span><span class="sxs-lookup"><span data-stu-id="4f736-127">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="4f736-128">Consultez la rubrique [configurer Microsoft 365 pour les entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) pour une liste de bout en bout des étapes de configuration.</span><span class="sxs-lookup"><span data-stu-id="4f736-128">See [Set up Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a><span data-ttu-id="4f736-129">Plus d’informations sur la façon d’ajouter des utilisateurs à Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4f736-129">More information about how to add users to Microsoft 365</span></span>
<span data-ttu-id="4f736-130"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="4f736-130"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="4f736-131">Qu'est-ce que le format CSV ?</span><span class="sxs-lookup"><span data-stu-id="4f736-131">Not sure what CSV format is?</span></span>
<span data-ttu-id="4f736-132"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="4f736-132"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="4f736-p106">Un fichier CSV inclut des valeurs séparées par des virgules. Vous pouvez créer ou modifier un fichier comme celui-ci avec un éditeur de texte ou un tableur comme Excel.</span><span class="sxs-lookup"><span data-stu-id="4f736-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="4f736-135">Vous pouvez télécharger [cet exemple de feuille de calcul](https://www.microsoft.com/download/details.aspx?id=45485) pour commencer.</span><span class="sxs-lookup"><span data-stu-id="4f736-135">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point.</span></span> <span data-ttu-id="4f736-136">N’oubliez pas que Microsoft 365 nécessite des en-têtes de colonne dans la première ligne afin de ne pas les remplacer par d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="4f736-136">Remember that Microsoft 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="4f736-137">Enregistrez le fichier avec un nouveau nom et spécifiez le format CSV.</span><span class="sxs-lookup"><span data-stu-id="4f736-137">Save the file with a new name, and specify CSV format.</span></span>
  
![Image expliquant comment enregistrer un fichier au format CSV dans Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="4f736-p108">Une fois le fichier enregistré, il est probable qu'un message indiquant que certaines fonctionnalités de votre classeur seront perdues si vous enregistrez le fichier au format CSV s'affiche. Ceci est normal. Cliquez sur **Oui** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="4f736-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Image de l'invite rencontrée dans Excel vous demandant si vous voulez vraiment enregistrer le fichier au format CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="4f736-143">Conseils pour la mise en forme de votre feuille de calcul</span><span class="sxs-lookup"><span data-stu-id="4f736-143">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="4f736-144"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="4f736-144"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="4f736-145">**Ai-je besoin des mêmes en-têtes de colonne que dans l'exemple de feuille de calcul ?**</span><span class="sxs-lookup"><span data-stu-id="4f736-145">**Do I need the same column headings as in the sample spreadsheet?**</span></span> <span data-ttu-id="4f736-146">Oui.</span><span class="sxs-lookup"><span data-stu-id="4f736-146">Yes.</span></span> <span data-ttu-id="4f736-147">La première ligne de l'exemple de feuille de calcul inclut les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="4f736-147">The sample spreadsheet contains column headings in the first row.</span></span> <span data-ttu-id="4f736-148">Ces en-têtes sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="4f736-148">These headings are required.</span></span> <span data-ttu-id="4f736-149">Pour chaque utilisateur que vous souhaitez ajouter à Microsoft 365, créez une ligne sous l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="4f736-149">For each user you want to add to Microsoft 365, create a row under the heading.</span></span> <span data-ttu-id="4f736-150">Si vous ajoutez, modifiez ou supprimez l’un des en-têtes de colonne, Microsoft 365 peut ne pas être en mesure de créer des utilisateurs à partir des informations contenues dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="4f736-150">If you add, change, or delete any of the column headings, Microsoft 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="4f736-p110">**Que faire si je n'ai pas toutes les informations requises pour chaque utilisateur ?** Le nom de l'utilisateur et le nom d'affichage sont obligatoires. Vous ne pouvez pas ajouter un nouvel utilisateur sans ces informations. S'il vous manque d'autres informations, par exemple le numéro de télécopie, vous pouvez insérer un espace suivi d'une virgule pour indiquer que le champ est vide.</span><span class="sxs-lookup"><span data-stu-id="4f736-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="4f736-154">**Quelle est la taille de la feuille de calcul ?**</span><span class="sxs-lookup"><span data-stu-id="4f736-154">**How small or large can the spreadsheet be?**</span></span> <span data-ttu-id="4f736-155">La feuille de calcul doit comporter au moins deux lignes.</span><span class="sxs-lookup"><span data-stu-id="4f736-155">The spreadsheet must have at least two rows.</span></span> <span data-ttu-id="4f736-156">One is for the column headings (the user data column label) and one for the user.</span><span class="sxs-lookup"><span data-stu-id="4f736-156">One is for the column headings (the user data column label) and one for the user.</span></span> <span data-ttu-id="4f736-157">You cannot have more than 251 rows.</span><span class="sxs-lookup"><span data-stu-id="4f736-157">You cannot have more than 251 rows.</span></span> <span data-ttu-id="4f736-158">If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="4f736-158">If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="4f736-159">**Quelles langues puis-je utiliser ?**</span><span class="sxs-lookup"><span data-stu-id="4f736-159">**What languages can I use?**</span></span> <span data-ttu-id="4f736-160">Lorsque vous créez votre feuille de calcul, vous pouvez entrer des étiquettes de colonne de données utilisateur dans n’importe quelle langue ou tous les caractères, mais vous ne devez pas modifier l’ordre des étiquettes, comme illustré dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="4f736-160">When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample.</span></span> <span data-ttu-id="4f736-161">You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="4f736-161">You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="4f736-p113">**Que dois-je faire si j'ajoute des utilisateurs de régions ou de pays différents ?** Créez une feuille de calcul distincte pour chaque zone. Vous devez exécuter l'Assistant Ajouter des utilisateurs en bloc avec chaque feuille de calcul, et donner ainsi un seul emplacement à tous les utilisateurs inclus dans le fichier que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="4f736-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="4f736-p114">**Le nombre de caractères que je peux utiliser est-il limité ?** Le tableau suivant indique les étiquettes de colonne des données utilisateur et le nombre maximal de caractères autorisés pour chacune d'elles dans l'exemple de feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="4f736-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="4f736-167">**Étiquette de colonne des données utilisateur**</span><span class="sxs-lookup"><span data-stu-id="4f736-167">**User data column label**</span></span>|<span data-ttu-id="4f736-168">**Longueur de caractères maximale**</span><span class="sxs-lookup"><span data-stu-id="4f736-168">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4f736-169">Nom d'utilisateur (requis)</span><span class="sxs-lookup"><span data-stu-id="4f736-169">User Name (Required)</span></span>  <br/> |<span data-ttu-id="4f736-170">79 y compris le signe arobase (@), au format name@domain. \<extension\> .</span><span class="sxs-lookup"><span data-stu-id="4f736-170">79 including the at sign (@), in the format name@domain.\<extension\>.</span></span> <span data-ttu-id="4f736-171">L’alias de l’utilisateur ne peut pas dépasser 50 caractères, et le nom de domaine ne peut pas dépasser 48 caractères.</span><span class="sxs-lookup"><span data-stu-id="4f736-171">The user's alias cannot exceed 50 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="4f736-172">Prénom</span><span class="sxs-lookup"><span data-stu-id="4f736-172">First Name</span></span>  <br/> |<span data-ttu-id="4f736-173">64</span><span class="sxs-lookup"><span data-stu-id="4f736-173">64</span></span>  <br/> |
|<span data-ttu-id="4f736-174">Nom</span><span class="sxs-lookup"><span data-stu-id="4f736-174">Last Name</span></span>  <br/> |<span data-ttu-id="4f736-175">64</span><span class="sxs-lookup"><span data-stu-id="4f736-175">64</span></span>  <br/> |
|<span data-ttu-id="4f736-176">Nom d'affichage (requis)</span><span class="sxs-lookup"><span data-stu-id="4f736-176">Display Name (required)</span></span>  <br/> |<span data-ttu-id="4f736-177">256</span><span class="sxs-lookup"><span data-stu-id="4f736-177">256</span></span>  <br/> |
|<span data-ttu-id="4f736-178">Poste</span><span class="sxs-lookup"><span data-stu-id="4f736-178">Job Title</span></span>  <br/> |<span data-ttu-id="4f736-179">64</span><span class="sxs-lookup"><span data-stu-id="4f736-179">64</span></span>  <br/> |
|<span data-ttu-id="4f736-180">Service</span><span class="sxs-lookup"><span data-stu-id="4f736-180">Department</span></span>  <br/> |<span data-ttu-id="4f736-181">64</span><span class="sxs-lookup"><span data-stu-id="4f736-181">64</span></span>  <br/> |
|<span data-ttu-id="4f736-182">Numéro du bureau</span><span class="sxs-lookup"><span data-stu-id="4f736-182">Office Number</span></span>  <br/> |<span data-ttu-id="4f736-183">128</span><span class="sxs-lookup"><span data-stu-id="4f736-183">128</span></span>  <br/> |
|<span data-ttu-id="4f736-184">Téléphone (bureau)</span><span class="sxs-lookup"><span data-stu-id="4f736-184">Office Phone</span></span>  <br/> |<span data-ttu-id="4f736-185">64</span><span class="sxs-lookup"><span data-stu-id="4f736-185">64</span></span>  <br/> |
|<span data-ttu-id="4f736-186">Téléphone mobile</span><span class="sxs-lookup"><span data-stu-id="4f736-186">Mobile Phone</span></span>  <br/> |<span data-ttu-id="4f736-187">64</span><span class="sxs-lookup"><span data-stu-id="4f736-187">64</span></span>  <br/> |
|<span data-ttu-id="4f736-188">Télécopie</span><span class="sxs-lookup"><span data-stu-id="4f736-188">Fax</span></span>  <br/> |<span data-ttu-id="4f736-189">64</span><span class="sxs-lookup"><span data-stu-id="4f736-189">64</span></span>  <br/> |
|<span data-ttu-id="4f736-190">Adresse</span><span class="sxs-lookup"><span data-stu-id="4f736-190">Address</span></span>  <br/> |<span data-ttu-id="4f736-191">1023</span><span class="sxs-lookup"><span data-stu-id="4f736-191">1023</span></span>  <br/> |
|<span data-ttu-id="4f736-192">Ville</span><span class="sxs-lookup"><span data-stu-id="4f736-192">City</span></span>  <br/> |<span data-ttu-id="4f736-193">128</span><span class="sxs-lookup"><span data-stu-id="4f736-193">128</span></span>  <br/> |
|<span data-ttu-id="4f736-194">Département ou région</span><span class="sxs-lookup"><span data-stu-id="4f736-194">State or Province</span></span>  <br/> |<span data-ttu-id="4f736-195">128</span><span class="sxs-lookup"><span data-stu-id="4f736-195">128</span></span>  <br/> |
|<span data-ttu-id="4f736-196">Code postal</span><span class="sxs-lookup"><span data-stu-id="4f736-196">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="4f736-197">40</span><span class="sxs-lookup"><span data-stu-id="4f736-197">40</span></span>  <br/> |
|<span data-ttu-id="4f736-198">Pays ou région</span><span class="sxs-lookup"><span data-stu-id="4f736-198">Country or Region</span></span>  <br/> |<span data-ttu-id="4f736-199">128</span><span class="sxs-lookup"><span data-stu-id="4f736-199">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a><span data-ttu-id="4f736-200">Vous rencontrez toujours des problèmes lors de l’ajout d’utilisateurs à Microsoft 365 ?</span><span class="sxs-lookup"><span data-stu-id="4f736-200">Still having problems when adding users to Microsoft 365?</span></span>

- <span data-ttu-id="4f736-p116">**Vérifiez que la feuille de calcul est correctement mise en forme.** Examinez les en-têtes des colonnes pour vous assurer qu'ils correspondent à ceux de l'exemple de fichier. Veillez à respecter le nombre de caractères autorisés et assurez-vous que chaque champ est séparé par une virgule.</span><span class="sxs-lookup"><span data-stu-id="4f736-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="4f736-204">**Si vous ne voyez pas les nouveaux utilisateurs dans Microsoft 365 immédiatement, patientez quelques minutes.**</span><span class="sxs-lookup"><span data-stu-id="4f736-204">**If you don't see the new users in Microsoft 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="4f736-205">Les modifications apportées à tous les services de Microsoft 365 peuvent prendre un peu de temps.</span><span class="sxs-lookup"><span data-stu-id="4f736-205">It can take a little while for changes to go across all the services in Microsoft 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="4f736-206">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="4f736-206">Related articles</span></span>

[<span data-ttu-id="4f736-207">Ajouter des utilisateurs individuellement ou en bloc à Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4f736-207">Add users individually or in bulk to Microsoft 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




