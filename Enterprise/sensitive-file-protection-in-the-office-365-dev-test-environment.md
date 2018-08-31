---
title: Protection des fichiers sensibles dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Résumé : Configurer et démontrer comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.'
ms.openlocfilehash: d866c8ef9d81ec3a80c466040dab34de8af2c1de
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915699"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protection des fichiers sensibles dans l’environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer comment Office 365 Information Rights Management protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.
  
La Gestion des droits relatifs à l’information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger les documents qui sont téléchargés à partir de listes et bibliothèques SharePoint Online. Les fichiers téléchargés sont chiffrés et contiennent les autorisations d’ouverture, de copie, d’enregistrement et d’impression qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.
  
Grâce aux instructions fournies dans cet article, vous activez et testez IRM dans Office 365 pour les fichiers contenant d’éventuelles informations sensibles dans votre abonnement à la version d’évaluation d’Office 365.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1 : créer votre environnement de développement/test Office 365

Si vous souhaitez simplement tester la protection des fichiers sensibles avec une configuration minimale, suivez les instructions des étapes 2 et 3 de [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la protection des fichiers sensibles ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection des fichiers sensibles et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Phase 2 : Démontrez comment une fuite de documents est possible à partir de sites protégés par des autorisations

Lors de cette phase, vous démontrez qu’une personne peut télécharger un document à partir d’un site protégé par des autorisations, puis le télécharger sur un site disposant d’autorisations élargies.
  
Tout d’abord, vous ajoutez trois nouveaux comptes d’utilisateur qui représentent les cadres et vous leur affectez des licences Office 365 E5.
  
Utilisez les instructions indiquées dans [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (le cas échéant) et de se connecter à votre nouvel abonnement Office 365 à partir de :
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez le nom de l’administrateur général Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe de votre abonnement à la version d’évaluation d’Office 365.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte CEO et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte CFO et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte COO et enregistrez-le dans un emplacement sécurisé.
  
Ensuite, créez un groupe de cadres privé et ajoutez les nouveaux comptes d’encadrement.
  
1. Dans votre navigateur, accédez au portail Office à [http://portal.office.com](http://portal.office.com) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer ou votre navigateur et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 avec entreprise simulée, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. Dans l’onglet **Accueil Microsoft Office** , cliquez sur **Administration > Groupes > Groupes**, puis cliquez sur **Ajouter un groupe**.
    
3. Dans **Ajouter un groupe**, sélectionnez **Groupe Office 365** pour le type de groupe, tapez **Cadres** dans **Nom** et **ID de groupe**, sélectionnez **Privé** pour **Confidentialité**, puis cliquez sur **Sélectionner le propriétaire**.
    
4. Dans la liste, cliquez sur le nom de votre compte d’administrateur général.
    
5. Cliquez sur **Ajouter**, puis sur **Fermer**.
    
6. Dans la liste de groupes, cliquez sur **Cadres**.
    
7. Cliquez sur **Modifier pour les membres**.
    
8. Cliquez sur **Ajouter des membres**. Dans la liste des membres, sélectionnez les comptes d’utilisateur suivants :
    
  - Directeur général
    
  - Directeur financier
    
  - Directeur des opérations
    
9. Cliquez sur **Enregistrer**, puis sur **Fermer**.
    
10. Fermez l’onglet **Centre d’administration Office**.
    
Ensuite, créez une collection de sites de cadres et autorisez uniquement les membres du groupe de cadres à y accéder.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur la mosaïque **Admin**.
    
2. Dans l’onglet **Centre d’administration d’Office** , cliquez sur **centres d’administration > SharePoint**.
    
3. Dans l’onglet **Centre d’administration SharePoint** , cliquez sur **Nouveau > collection de sites privée**.
    
4. Dans le volet nouvelle collection de sites, tapez **cadres** dans **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d’administrateur général dans **administrateur**, puis cliquez sur **OK**.
    
5. Attendez que la nouvelle collection de sites a été créée. Lorsque vous avez terminé, copiez l’URL de la nouvelle collection de sites responsables et collez-le dans un nouvel onglet de votre navigateur.
    
6. Dans le coin supérieur droit de la collection de sites **Cadres**, cliquez sur l’icône des paramètres, puis cliquez sur **Partagé avec**.
    
7. Dans **partage de « Responsables »**, cliquez sur **Avancé**.
    
8. Dans la liste des groupes SharePoint, cliquez sur **Membres de cadres**.
    
9. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
10. Dans **partage de « Responsables »**, tapez **cadres**, cliquez sur le groupe de **cadres** , puis cliquez sur **partager**.
    
11. Fermez l’onglet **personnes et groupes** .
    
Ensuite, autorisez tout le monde à accéder à la collection de sites de ventes.
  
1. Sous l’onglet **Centre d’administration SharePoint** , copiez l’URL de la collection de sites ventes et collez-le dans un nouvel onglet de votre navigateur...
    
2. Dans le coin supérieur droit, cliquez sur l’icône Paramètres, puis cliquez sur **partagé avec**.
    
3. Dans **partage de « Collection de sites ventes »**, cliquez sur **Avancé**.
    
4. Dans la liste des groupes SharePoint, cliquez sur **Membres de la collection de sites de ventes**.
    
5. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
6. Dans **partage de « Collection de sites ventes »**, tapez **tout le monde**, cliquez sur **tout le monde, à l’exception des utilisateurs externes**, puis cliquez sur **partager**.
    
7. Fermez les onglets **Collection de sites de ventes** et **SharePoint**.
    
Ensuite, connectez-vous avec un compte de cadre et créez un document dans la collection de sites Cadres.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.
    
4. Entrez le nom du compte **CEO** et le mot de passe associé, puis cliquez sur **Se connecter**.
    
5. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/executives**).
    
6. Cliquez sur **Documents**et cliquez sur **Nouveau,** puis cliquez sur **Document Word**.
    
7. Cliquez dans la barre de titre et tapez **SensitiveData-BeforeIRM**.
    
8. Cliquez dans le corps du document et tapez **Compte-rendu du dernier conseil d’administration**, puis cliquez sur **Cadres**.
    
      Vous devriez voir **SensitiveData-BeforeIRM.docx** dans le dossier **Documents**.
    
Ensuite, vous téléchargez une copie locale du document SensitiveData-BeforeIRM.docx et la publiez accidentellement dans la collection de sites Ventes.
  
1. Sur votre ordinateur local, créez un nouveau dossier (par exemple, c :\\TLGs\\SensitiveDataTestFiles).
    
2. Dans l’onglet **Documents** de votre navigateur, sélectionnez le document **SensitiveData-BeforeIRM.docx** et cliquez sur les points de suspension, puis sur **Télécharger**.
    
3. Rangez le document **SensitiveData-BeforeIRM.docx** dans le dossier créé dans l’étape 1.
    
4. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/sales**).
    
5. Cliquez sur le dossier **Documents** de la **collection de sites de ventes**.
    
6. Cliquez sur **Télécharger**, puis spécifiez le document **SensitiveData-BeforeIRM.docx** dans le dossier créé à l’étape 1, puis cliquez sur **OK**.
    
7. Vérifiez que le document **SensitiveData-BeforeIRM.docx** se trouve dans le dossier **Documents**.
    
8. Fermez les onglets **Ventes** et **SharePoint**.
    
Ensuite, connectez-vous en tant que Utilisateur 5 et essayez d’ouvrir le document SensitiveData-BeforeIRM.docx dans la collection de sites de ventes.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.
    
4. Entrez le nom du compte Utilisateur 5 et le mot de passe associé, puis cliquez sur **Se connecter**.
    
5. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.
    
6. Dans le dossier **Documents** de la **Collection de sites de ventes**, cliquez sur le document **SensitiveData-BeforeIRM.docx**. 
    
    Vous devriez voir son contenu.
    
7. Fermez les onglets **Documents** et **Collection de sites de ventes**.
    
En publiant accidentellement le document SensitiveData-BeforeIRM.docx sur la collection de sites de ventes, le directeur général a ignoré la sécurité des autorisations de la collection de sites Cadres.
  
Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Sur la page **Connexion à Office 365**, cliquez sur le nom de compte de l’administrateur général, tapez son mot de passe, puis cliquez sur **Se connecter**.
    
4. Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Administrateur > Centres d’administration > SharePoint**.
    
5. Dans l’onglet **Centre d’administration SharePoint**, cliquez sur **Paramètres**.
    
6. Sur la page **Paramètres**, dans la section **Gestion des droits relatifs à l’information (IRM)**, sélectionnez **Utiliser le service IRM spécifié dans votre configuration**, puis sélectionnez **Actualiser les paramètres IRM**.
    
7. Fermez l’onglet **Centre d’administration SharePoint**.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Phase 3 : Utiliser la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365

Lors de cette phase, vous utilisez la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365 pour protéger l’accès à un document contenant des informations sensibles, même lorsqu’il est publié sur un site avec des autorisations d’ouverture.
  
Tout d’abord, vous activez et configurez IRM pour la bibliothèque de documents de la collection de sites Cadres.  
  
1. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.
    
2. Cliquez sur **Documents**.
    
3. Dans le coin supérieur droit, cliquez sur l’icône des paramètres, puis sur **Paramètres de la bibliothèque**.
    
4. Sur la page **Paramètres**, sous **Autorisations et gestion**, cliquez sur **Gestion des droits relatifs à l’information**.
    
5. Dans la page **Paramètres de gestion des droits relatifs à l’information** :
    
  - Sélectionnez **Restreindre l’accès aux documents de cette bibliothèque au téléchargement**.
    
  - Pour **Créer un titre de la stratégie d’autorisation**, tapez **Cadres**.
    
  - Pour **Ajouter une description de la stratégie d’autorisation**, tapez **IRM pour les cadres**.
    
6. Cliquez sur **Afficher les options**.
    
7. Sous **Définir d’autres paramètres de la bibliothèque IRM**, sélectionnez **Ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge IRM**.
    
8. Sous **Configurer les droits d’accès aux documents**, sélectionnez **Autoriser les utilisateurs à imprimer** et **Autoriser les utilisateurs à écrire sur une copie du document téléchargé**.
    
9. Sous **Définir la protection de groupe et l’intervalle d’informations d’identification**, sélectionnez **Autoriser la protection de groupe** et pour **Groupe par défaut**, tapez **Cadres**.
    
10. Cliquez sur **OK**.
    
Ensuite, en jouant le rôle du directeur général, vous chargez un nouveau document dans le dossier de documents Cadres, le téléchargez, puis le chargez accidentellement dans le dossier de documents Ventes.
  
1. Ouvrez le dossier local où est stocké le document **SensitiveData-BeforeIRM.docx**.
    
2. 	Cliquez avec le bouton droit sur **SensitiveData-BeforeIRM.docx**, puis cliquez sur **Copier**.
    
3. Cliquez avec le bouton droit dans le dossier, puis cliquez sur **Coller**.
    
4. Renommez le nouveau fichier **SensitiveData-BeforeIRM - Copy.docx** **- AfterIRM.docx SensitiveData**.
    
5. Dans l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
6. Accédez à [http://portal.office.com](http://portal.office.com).
    
7. Sur la page **Connexion à Office 365**, cliquez sur le nom du compte CEO, tapez son mot de passe, puis cliquez sur **Se connecter**.
    
8. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.
    
9. Sur la page **Documents**, cliquez sur **Charger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.
    
10. Sélectionnez le nouveau document **SensitiveData-AfterIRM.docx** dans la page **Documents** et cliquez sur les points de suspension (...) dans la barre de menus, puis cliquez sur **Télécharger**.
    
11. Lorsque vous y êtes invité, enregistrez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, en remplaçant la version d’origine.
    
12. Fermez l’onglet de la page **Documents**.
    
13. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.
    
14. Cliquez sur **Documents**.
    
15. Sur la page **Documents**, cliquez sur **Charger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.
    
16. Fermez les onglets **Collection de sites de ventes** et **SharePoint**.
    
Ensuite, en tant qu’utilisateur normal, essayez d’accéder au document **SensitiveData-AfterIRM.docx** dans le dossier de documents Ventes.
  
1. Dans l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5, tapez son mot de passe, puis cliquez sur **se connecter**.
    
4. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites ventes.
    
5. Cliquez sur **Documents**.
    
6. Sur la page **Documents**, ouvrez le document **SensitiveData-AfterIRM.docx**. 
    
    Vous devez voir un message indiquant « Désolé, Word Online ne peut pas ouvrir ce document, car il est protégé par la Gestion des droits relatifs à l’information (IRM). »  
    
7. Cliquez sur **Modifier dans Word**. Vous êtes invité à indiquer si vous souhaitez ouvrir le fichier. Cliquez sur **Oui**.
    
8. Vous êtes invité à vous connecter. Tapez le nom du compte Utilisateur 5, puis cliquez sur **Suivant**.
    
9. Vous êtes invité à fournir le mot de passe. Tapez le mot de passe du compte Utilisateur 5, puis cliquez sur **Se connecter**.  
    
    Vous devez voir un message indiquant ce qui suit : « Vous ne disposez pas des informations d’identification requises pour ouvrir ce document. »
    
10. Cliquez sur **Non**.
    
Pour afficher la protection IRM, vous pouvez également examiner les fichiers dans votre dossier local. Le fichier **SensitiveData-AfterIRM.docx** doit être beaucoup plus volumineux que le fichier **SensitiveData-BeforeIRM.docx**. Le fichier **SensitiveData-AfterIRM.docx** est chiffré et contient les informations sur la protection IRM.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


