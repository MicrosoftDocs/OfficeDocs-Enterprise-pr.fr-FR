---
title: Ajouter plusieurs utilisateurs simultanément à Office 365 - Aide de l'administrateur
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
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
description: 'Découvrez comment ajouter plusieurs utilisateurs à Office 365 pour les entreprises à partir d’une liste dans une feuille de calcul ou dans un autre fichier au format CSV. Regardez une vidéo sur YouTube qui explique comment ajouter des comptes à Office 365. À la fin de ce processus, chaque utilisateur disposant d’un compte dispose d’une boîte aux lettres Office 365. '
ms.openlocfilehash: 16cea3b09da7d6450efd09bad0937bfcef9f70ab
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813492"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Ajouter plusieurs utilisateurs simultanément à Office 365 - Aide de l’administrateur

[] Les membres de votre équipe ont besoin d'un compte d'utilisateur pour pouvoir se connecter et accéder aux services Office 365, tels que le courrier et Office. Si votre équipe compte de nombreux membres, vous pouvez ajouter tous leurs comptes simultanément à partir d'une feuille de calcul Excel ou d'un autre fichier enregistré au format CSV. [Qu'est-ce que le format CSV ?](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a>Ajouter plusieurs utilisateurs à Office 365 dans le centre d’administration Microsoft 365

1. Connectez-vous à Office 365 avec votre compte professionnel ou scolaire. 
    
2. Dans le centre d’administration, **Choisissez** \> utilisateurs **actifs**.

3. Sélectionnez **ajouter plusieurs utilisateurs**.

4. Dans le panneau **Importer plusieurs utilisateurs**, vous pouvez éventuellement télécharger un exemple de fichier CSV avec ou sans exemple de données inclus. 
    
    Votre feuille de calcul doit inclure les **mêmes en-têtes de colonne** que ceux de l'exemple (Nom d'utilisateur, Prénom, etc.). Si vous utilisez le modèle, ouvrez-le dans un outil d'édition de texte tel que Notepad, laissez les données de la ligne 1 inchangées et entrez uniquement des données dans la ligne 2 et les lignes suivantes. 
    
    Votre feuille de calcul doit également inclure des valeurs pour le nom d'utilisateur (tel que alexandre@contoso.com) et un nom complet (tel que Alexandre Chauvin) pour chaque utilisateur. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Entrez un chemin d'accès dans la zone, ou choisissez **Parcourir** pour accéder à l'emplacement du fichier CSV, puis sélectionnez **Vérifier**.
  
    S'il existe des problèmes avec le fichier, ceux-ci s'affichent dans le panneau. Vous pouvez également télécharger un fichier journal.
    
5. Dans la boîte de dialogue **Définir les options utilisateur**, vous pouvez définir le statut de connexion et choisir la licence produit à affecter à tous les utilisateurs. 
    
6. Dans la boîte de dialogue **Affichez vos résultats**, vous pouvez choisir d'envoyer les résultats à vous-même ou à d'autres utilisateurs (les mots de passe seront au format texte brut). En outre, vous pouvez voir combien d'utilisateurs ont été créés et si vous avez besoin d'acheter des licences supplémentaires pour les attribuer à certains des nouveaux utilisateurs. 
    
## <a name="watch-the-video"></a>Voir la vidéo
<a name="bk_preview"> </a>

 Regardez une courte vidéo qui vous montre comment ajouter des utilisateurs en bloc. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Étapes suivantes
<a name="bk_preview"> </a>

- À présent que ces personnes ont des comptes, elles doivent [Télécharger et installer ou réinstaller office 365 ou office 2016 sur un PC ou un Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Chaque membre de votre équipe peut installer Office 365 sur un maximum de 5 PC ou Mac. 
    
- Chaque personne peut également [configurer les applications Office et le courrier électronique sur un appareil mobile sur un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) maximum de 5 tablettes et 5 téléphones, comme des iPhone, des iPad et des tablettes et tablettes Android. Ainsi, ils peuvent modifier les fichiers Office à partir de n’importe quel endroit. 
    
    Voir [Configurer Office 365 pour les entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) pour obtenir une liste de bout en bout des étapes de configuration. 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Informations complémentaires sur l'ajout d'utilisateurs à Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>Qu'est-ce que le format CSV ?
<a name="__toc316652088"> </a>

Un fichier CSV inclut des valeurs séparées par des virgules. Vous pouvez créer ou modifier un fichier comme celui-ci avec un éditeur de texte ou un tableur comme Excel.
  
Vous pouvez télécharger [cet exemple de feuille de calcul](https://www.microsoft.com/download/details.aspx?id=45485) pour commencer. Rappelez-vous qu'Office 365 nécessite des en-têtes de colonne dans la première ligne, aussi ne les remplacez pas par d'autres informations. 
  
Enregistrez le fichier avec un nouveau nom et spécifiez le format CSV.
  
![Image expliquant comment enregistrer un fichier au format CSV dans Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Une fois le fichier enregistré, il est probable qu'un message indiquant que certaines fonctionnalités de votre classeur seront perdues si vous enregistrez le fichier au format CSV s'affiche. Ceci est normal. Cliquez sur **Oui** pour continuer. 
  
![Image de l'invite rencontrée dans Excel vous demandant si vous voulez vraiment enregistrer le fichier au format CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Conseils pour la mise en forme de votre feuille de calcul
<a name="__toc314595848"> </a>

- **Ai-je besoin des mêmes en-têtes de colonne que dans l'exemple de feuille de calcul ?** Oui. La première ligne de l'exemple de feuille de calcul inclut les en-têtes de colonne. Ces en-têtes sont obligatoires. Pour chaque utilisateur que vous voulez ajouter à Office 365, créez une ligne sous l'en-tête. Si vous ajoutez, modifiez ou supprimez l'un des en-têtes de colonne, il est possible qu'Office 365 ne puisse pas créer des utilisateurs à partir des informations du fichier. 
    
- **Que faire si je n'ai pas toutes les informations requises pour chaque utilisateur ?** Le nom de l'utilisateur et le nom d'affichage sont obligatoires. Vous ne pouvez pas ajouter un nouvel utilisateur sans ces informations. S'il vous manque d'autres informations, par exemple le numéro de télécopie, vous pouvez insérer un espace suivi d'une virgule pour indiquer que le champ est vide. 
    
- ** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet. 
    
- ** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format. 
    
- **Que dois-je faire si j'ajoute des utilisateurs de régions ou de pays différents ?** Créez une feuille de calcul distincte pour chaque zone. Vous devez exécuter l'Assistant Ajouter des utilisateurs en bloc avec chaque feuille de calcul, et donner ainsi un seul emplacement à tous les utilisateurs inclus dans le fichier que vous utilisez. 
    
- **Le nombre de caractères que je peux utiliser est-il limité ?** Le tableau suivant indique les étiquettes de colonne des données utilisateur et le nombre maximal de caractères autorisés pour chacune d'elles dans l'exemple de feuille de calcul. 
    
|**Étiquette de colonne des données utilisateur**|**Longueur de caractères maximale**|
|:-----|:-----|
|Nom d'utilisateur (requis)  <br/> |79 avec le symbole arobase (@), au format nom@domaine.\<extension\>. L'alias de l'utilisateur ne peut pas dépasser 30 caractères, et le nom de domaine 48 caractères.  <br/> |
|Prénom  <br/> |64  <br/> |
|Nom  <br/> |64  <br/> |
|Nom d'affichage (requis)  <br/> |256  <br/> |
|Poste  <br/> |64  <br/> |
|Service  <br/> |64  <br/> |
|Numéro du bureau  <br/> |128  <br/> |
|Téléphone (bureau)  <br/> |64  <br/> |
|Téléphone mobile  <br/> |64  <br/> |
|Télécopie  <br/> |64  <br/> |
|Adresse  <br/> |1023  <br/> |
|Ville  <br/> |128  <br/> |
|Département ou région  <br/> |128  <br/> |
|Code postal  <br/> |40  <br/> |
|Pays ou région  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>Vous rencontrez encore des problèmes lorsque vous ajoutez des utilisateurs à Office 365 ?

- **Vérifiez que la feuille de calcul est correctement mise en forme.** Examinez les en-têtes des colonnes pour vous assurer qu'ils correspondent à ceux de l'exemple de fichier. Veillez à respecter le nombre de caractères autorisés et assurez-vous que chaque champ est séparé par une virgule. 
    
- **Si vous ne voyez pas les nouveaux utilisateurs dans Office 365 immédiatement, patientez quelques minutes.** Les modifications apportées à l’ensemble des services dans Office 365 peuvent prendre un peu de temps. 
    
## <a name="related-articles"></a>Articles connexes

[Ajouter des utilisateurs individuellement ou en bloc à Office 365](https://docs.microsoft.com/office365/admin/add-users/add-users)




