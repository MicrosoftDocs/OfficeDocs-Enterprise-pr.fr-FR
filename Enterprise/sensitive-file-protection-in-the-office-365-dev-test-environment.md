---
title: Protection des fichiers sensibles dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Résumé: conFigurez et montrez comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu'ils sont publiés dans une collection de sites SharePoint Online incorrecte."
ms.openlocfilehash: 4b65df7fe194d543acaf1c3ba6f104681a998dc6
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741300"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protection des fichiers sensibles dans l’environnement de développement/test Office 365

 **Résumé:** ConFigurez et montrez comment Office 365 Information Rights Management protège vos fichiers sensibles, même s'ils sont publiés dans une collection de sites SharePoint Online incorrecte.
  
La gestion des droits relatifs à l'information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger des documents qui sont téléchargés à partir de bibliothèques et de listes SharePoint Online. Les fichiers téléchargés sont chiffrés et contiennent les autorisations ouvrir, copier, enregistrer et imprimer qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.
  
Les instructions de cet article vous permettent d'activer et de tester la gestion des droits relatifs à l'information (IRM) dans Office 365 pour les fichiers contenant des informations sensibles possibles dans votre abonnement d'évaluation Office 365.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher un plan de tous les Articles de la pile de guides de laboratoire de Test Office 365.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: créer votre environnement de développement/test Office 365

Si vous souhaitez simplement tester la protection des fichiers sensibles avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la protection des fichiers sensibles ne nécessite pas l'environnement de développement/test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu'option pour vous permettre de tester la protection des fichiers sensibles et de l'expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Phase 2: montrer comment les documents provenant de sites protégés par des autorisations peuvent être divulgués

Dans cette phase, vous démontrez qu'une personne peut télécharger un document à partir d'un site protégé par des autorisations, puis le télécharger vers un site disposant d'autorisations étendues.
  
Tout d'abord, vous ajoutez trois nouveaux comptes d'utilisateur qui représentent les cadres et affectez-leur des licences Office 365 E5.
  
Suivez les instructions de la procédure [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (si nécessaire) et vous connecter à votre nouvel abonnement Office 365 à partir de:
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
Dans la boîte de dialogue **demande d'informations d'identification Windows PowerShell** , tapez le nom de l'administrateur jdoe@contosotoycompany.onmicrosoft.comgénéral Office 365 (exemple:) et le mot de passe de votre abonnement d'évaluation Office 365.
  
Renseignez le nom de votre organisation (par exemple: contosotoycompany) et le code pays à deux caractères pour votre emplacement, puis exécutez les commandes suivantes à partir de l'invite module Windows Azure Active Directory pour Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l'affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte PDG et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l'affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte directeur financier et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l'affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte directeur de directeur de sécurité et enregistrez-le dans un emplacement sécurisé.
  
Ensuite, créez un groupe de cadres privés et ajoutez-y les nouveaux comptes exécutifs.
  
1. Dans votre navigateur, accédez au portail Office [http://admin.microsoft.com](http://admin.microsoft.com) et connectez-vous à votre abonnement d'évaluation Office 365 avec votre compte d'administrateur général.
    
  - Si vous utilisez l'environnement de développement/test Office 365 léger, ouvrez une session privée d'Internet Explorer ou de votre navigateur, puis connectez-vous à partir de votre ordinateur local.
    
  - Si vous utilisez l'environnement de développement/test Office 365 entreprise simulé, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. Dans l'onglet **Accueil Microsoft Office** , cliquez sur **administrateurs _GT_ groupes > groupes**, puis cliquez sur **Ajouter un groupe**.
    
3. Dans **Ajouter un groupe**, sélectionnez **groupe Office 365** pour le type de groupe, tapez **cadres** dans **nom** et **ID de groupe**, sélectionnez **privé** pour la **confidentialité**, puis cliquez sur **Sélectionner le propriétaire**.
    
4. Dans la liste, cliquez sur le nom de votre compte d'administrateur général.
    
5. Cliquez sur **Ajouter**, puis sur **Fermer**.
    
6. Dans la liste des groupes, cliquez sur **cadres**.
    
7. Cliquez sur **Modifier pour les membres**.
    
8. Cliquez sur **Ajouter des membres**. Dans la liste des membres, sélectionnez les comptes d'utilisateur suivants:
    
  - Directeur général
    
  - Directeur financier
    
  - Directeur des opérations
    
9. Cliquez sur **Enregistrer**, puis sur **Fermer**.
    
10. Fermez l'onglet **Centre d'administration Office** .
    
Ensuite, vous créez une collection de sites Executives et autorisez uniquement les membres du groupe cadres à y accéder.
  
1. Dans l'onglet **Accueil Microsoft Office** , cliquez sur la vignette **administrateur** .
    
2. Dans l'onglet **Centre d'administration Office** , cliquez sur centres d'administration **> SharePoint**.
    
3. Dans l'onglet **Centre d'administration SharePoint** , cliquez sur **nouvelle collection de sites privée >**.
    
4. Dans le volet nouvelle collection de sites, tapez **cadres** dans **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d'administrateur général dans **administrateur**, puis cliquez sur **OK**.
    
5. Patientez jusqu'à ce que la collection de sites ait été créée. Lorsque vous avez terminé, copiez l'URL de la nouvelle collection de sites Executives et collez-la dans un nouvel onglet de votre navigateur.
    
6. Dans le coin supérieur droit de la collection de sites **cadres** , cliquez sur l'icône des paramètres, puis cliquez sur **partagé avec**.
    
7. Dans **partager «cadres»**, cliquez sur **avancé**.
    
8. Dans la liste des groupes SharePoint, cliquez sur membres de la **direction**.
    
9. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
10. Dans **partager «cadres»**, tapez **cadres**, cliquez sur le groupe **cadres** , puis cliquez sur **partager**.
    
11. Fermez l'onglet **personnes et groupes** .
    
Ensuite, vous autorisez tout le monde à accéder à la collection de sites de ventes.
  
1. À partir de l'onglet **Centre d'administration SharePoint** , copiez l'URL de la collection de sites de ventes et collez-la dans un nouvel onglet de votre navigateur..
    
2. Dans le coin supérieur droit, cliquez sur l'icône des paramètres, puis cliquez sur **partagé avec**.
    
3. Dans **partager «collection de sites de ventes»**, cliquez sur **avancé**.
    
4. Dans la liste des groupes SharePoint, cliquez sur membres de la **collection de sites de ventes**.
    
5. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
6. Dans **partager «collection de sites de ventes»**, tapez **tout le monde**, cliquez sur **tout le monde sauf les utilisateurs externes**, puis cliquez sur **partager**.
    
7. Fermez les onglets **collection de sites de ventes** et **SharePoint** .
    
Ensuite, connectez-vous avec un compte exécutif et créez un document dans la collection de sites cadres.
  
1. Dans l'onglet **Accueil Microsoft Office** , cliquez sur l'icône de l'utilisateur dans le coin supérieur droit, **** puis cliquez sur Déconnexion.
    
2. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Sur la page **de connexion à Office 365** , cliquez sur **utiliser un autre compte**.
    
4. Tapez le nom du compte **PDG** et son mot de passe, puis cliquez sur **se connecter**.
    
5. dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites cadres ( **https://**\<organisation name>**. sharepoint.com/sites/executives**).
    
6. Cliquez sur **documents**, sur **nouveau,** puis sur **document Word**.
    
7. Cliquez dans la barre de titre et tapez **sensitiveData-BeforeIRM**.
    
8. Cliquez dans le corps du document et tapez le compte- **rendu de la dernière réunion**, puis cliquez sur **cadres**.
    
     Vous devriez voir **sensitiveData-beforeirm. docx** dans le dossier **documents** .
    
Ensuite, téléchargez une copie locale du document sensitiveData-beforeirm. docx, puis publiez-le accidentellement dans la collection de sites Sales.
  
1. Sur votre ordinateur local, créez un dossier (par exemple, C:\\guides\\SensitiveDataTestFiles).
    
2. Dans l'onglet **documents** de votre navigateur, sélectionnez le document **sensitiveData-beforeirm. docx** , cliquez sur les ellipses, puis cliquez sur **Télécharger**.
    
3. Stockez le document **sensitiveData-beforeirm. docx** dans le dossier créé à l'étape 1.
    
4. dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites de vente ( **https://**\<organisation name>**. sharepoint.com/sites/sales**).
    
5. Cliquez sur le dossier **documents** de la **collection de sites de ventes**.
    
6. Cliquez sur **Télécharger**, puis spécifiez **sensitiveData-beforeirm. docx** dans le dossier créé à l'étape 1, puis cliquez sur **OK**.
    
7. Vérifiez que le document **sensitiveData-beforeirm. docx** se trouve dans le dossier **documents** .
    
8. Fermez les onglets **ventes** et **SharePoint** .
    
Ensuite, connectez-vous en tant que utilisateur 5 et essayez d'ouvrir le document sensitiveData-beforeirm. docx dans la collection de sites de ventes.
  
1. Dans l'onglet **Accueil Microsoft Office** , cliquez sur l'icône de l'utilisateur dans le coin supérieur droit, **** puis cliquez sur Déconnexion.
    
2. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Sur la page **de connexion à Office 365** , cliquez sur **utiliser un autre compte**.
    
4. Tapez le nom du compte utilisateur 5 et son mot de passe, puis cliquez sur **se connecter**.
    
5. Dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites de ventes.
    
6. Dans le dossier **documents** de la **collection de sites de ventes**, cliquez sur le **sensitiveData-beforeirm. docx** .
    
    Vous devriez voir son contenu.
    
7. Fermez les onglets **documents** et **collection de sites de ventes** .
    
En publiant accidentellement le document sensitiveData-beforeirm. docx sur la collection de sites de ventes, le PDG a contourné la sécurité des autorisations de la collection de sites cadres.
  
Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.
  
1. Dans l'onglet **Accueil Microsoft Office** , cliquez sur l'icône de l'utilisateur dans le coin supérieur droit, **** puis cliquez sur Déconnexion.
    
2. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Sur la page **de connexion Office 365** , cliquez sur le nom du compte d'administrateur général, tapez son mot de passe, puis cliquez sur **se connecter**.
    
4. Dans l'onglet **Accueil Microsoft Office** , cliquez sur **Centre d'administration > > SharePoint**.
    
5. Dans l'onglet **Centre d'administration SharePoint** , cliquez sur **paramètres**.
    
6. Dans la page, dans la section gestion des droits relatifs à l' **information (IRM)** , sélectionnez **utiliser le service IRM spécifié dans votre configuration**, puis actualiser les **paramètres IRM**.
    
7. Fermez l'onglet **Centre d'administration SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Phase 3: utiliser la gestion des droits relatifs à l'information (IRM) SharePoint avec un groupe privé Office 365

Dans cette phase, vous utilisez la gestion des droits relatifs à l'information (IRM) de SharePoint avec un groupe privé Office 365 pour protéger l'accès à un document avec des informations sensibles, même s'il est publié sur un site avec des autorisations ouvertes.
  
Tout d'abord, vous activez et configurez la gestion des droits relatifs à l'information pour la bibliothèque de documents de la collection de sites cadres. 
  
1. Dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites cadres.
    
2. Cliquez sur **Documents**.
    
3. Dans le coin supérieur droit, cliquez sur l'icône Paramètres, puis cliquez sur paramètres de la **bibliothèque**.
    
4. Sur la page **paramètres** , sous **autorisations et gestion**, cliquez sur **gestion des droits relatifs**à l'information.
    
5. Sur la page **paramètres de gestion des droits relatifs** à l'information:
    
  - Sélectionnez **restreindre l'autorisation aux documents de cette bibliothèque au téléchargement**.
    
  - Pour **créer un titre de stratégie d'autorisation**, tapez **dirigeants**.
    
  - Pour **Ajouter une description de stratégie d'autorisation**, tapez **IRM pour les cadres**.
    
6. Cliquez sur **Afficher les options**.
    
7. Sous **définir d'autres paramètres de la bibliothèque IRM**, sélectionnez **ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge IRM**.
    
8. Sous **configurer les droits d'accès au document**, sélectionnez **autoriser les visualiseurs à imprimer** et **autoriser les utilisateurs à écrire sur une copie du document téléchargé**.
    
9. Sous **définir la protection de groupe et l'intervalle des informations d'identification**, sélectionnez **autoriser la protection de groupe. Groupe par défaut**, puis tapez **Executives**.
    
10. Cliquez sur **OK**.
    
Ensuite, en tant que PDG, vous chargez un nouveau document dans le dossier de documents cadres, le télécharger, puis le charger accidentellement dans le dossier des documents de vente.
  
1. Ouvrez le dossier local dans lequel vous avez stocké le document **sensitiveData-beforeirm. docx** .
    
2. Cliquez avec le bouton droit sur **sensitiveData-beforeirm. docx**, puis cliquez sur **copier**.
    
3. Cliquez avec le bouton droit dans le dossier, puis cliquez sur **coller**.
    
4. Renommez le nouveau fichier **sensitiveData-BeforeIRM-Copy. docx** en **sensitiveData-AfterIRM. docx**.
    
5. À partir de l'onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l'icône de l'utilisateur dans le coin supérieur **** droit, puis cliquez sur Déconnexion.
    
6. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
7. Sur la page **de connexion à Office 365** , cliquez sur le nom du compte PDG, tapez son mot de passe, puis cliquez sur **se connecter**.
    
8. Dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites cadres.
    
9. Sur la page **documents** , cliquez sur **charger**, spécifiez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, puis cliquez sur **ouvrir**.
    
10. Sélectionnez le nouveau document **sensitiveData-AfterIRM. docx** dans la page **documents** , cliquez sur les points de suspension (...) dans la barre de menus, puis cliquez sur **Télécharger**.
    
11. Lorsque vous y êtes invité, enregistrez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, en remplaçant la version d'origine.
    
12. Fermez l'onglet de la page **documents** .
    
13. Dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites de ventes.
    
14. Cliquez sur **Documents**.
    
15. Sur la page **documents** , cliquez sur **charger**, spécifiez le document **sensitiveData-AfterIRM. docx** dans votre dossier local, puis cliquez sur **ouvrir**.
    
16. Fermez les onglets **collection de sites de ventes** et **SharePoint** .
    
Ensuite, en tant qu'utilisateur normal, vous tentez d'accéder au document **sensitiveData-AfterIRM. docx** dans le dossier Sales document.
  
1. À partir de l'onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l'icône de l'utilisateur dans le coin supérieur **** droit, puis cliquez sur Déconnexion.
    
2. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Sur la page **de connexion à Office 365** , cliquez sur le nom du compte utilisateur 5, tapez son mot de passe, puis cliquez sur **se connecter**.
    
4. Dans un nouvel onglet de votre navigateur, tapez l'URL de la collection de sites de ventes.
    
5. Cliquez sur **Documents**.
    
6. Sur la page **documents** , ouvrez le document **sensitiveData-AfterIRM. docx** .
    
    Un message indiquant «Désolé, Word Online ne peut pas ouvrir ce document, car il est protégé par la gestion des droits relatifs à l'information (IRM).» 
    
7. Cliquez sur **modifier dans Word**. Vous êtes invité à indiquer si vous souhaitez ouvrir le fichier. Cliquez sur **Oui**.
    
8. Vous êtes invité à vous connecter. Tapez le nom de compte du compte utilisateur 5, puis cliquez sur **suivant**.
    
9. Vous êtes invité à fournir le mot de passe. Tapez le mot de passe du compte utilisateur 5, puis cliquez sur **se connecter**. 
    
    Le message suivant doit s'afficher: «vous ne disposez pas des informations d'identification qui vous permettent d'ouvrir ce document».
    
10. Cliquez sur **non**.
    
Une autre façon d'afficher la protection IRM consiste à examiner les fichiers figurant dans votre dossier local. **SensitiveData-AfterIRM. docx** doit être plus volumineux que le fichier **sensitiveData-beforeirm. docx** . Le fichier **sensitiveData-AfterIRM. docx** est chiffré et les informations de protection IRM sont ajoutées.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


