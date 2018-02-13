---
title: "Protection des fichiers sensibles dans l’environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Résumé : Configuration et montrez comment Information Rights Management d’Office 365 protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte."
ms.openlocfilehash: 22f12143dc7cb50c19a135f51c08cb4b9bf02f38
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Protection des fichiers sensibles dans l’environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer comment Information Rights Management d’Office 365 protège vos fichiers sensibles, même lorsqu’elles sont validées dans la collection de sites SharePoint Online incorrecte.
  
La Gestion des droits relatifs à l’information (IRM) dans Office 365 est un ensemble de fonctionnalités permettant de protéger les documents qui sont téléchargés à partir de listes et bibliothèques SharePoint Online. Les fichiers téléchargés sont chiffrés et contiennent les autorisations d’ouverture, de copie, d’enregistrement et d’impression qui reflètent la bibliothèque SharePoint Online dans laquelle ils ont été stockés.
  
Grâce aux instructions fournies dans cet article, vous activez et testez IRM dans Office 365 pour les fichiers contenant d’éventuelles informations sensibles dans votre abonnement à la version d’évaluation d’Office 365.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1 : créer votre environnement de développement/test Office 365

Si vous souhaitez juste tester la protection des fichiers sensibles de façon légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la protection des fichiers sensibles dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la protection des fichiers sensibles ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection des fichiers sensibles et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Phase 2 : Démontrez comment une fuite de documents est possible à partir de sites protégés par des autorisations

Lors de cette phase, vous démontrez qu’une personne peut télécharger un document à partir d’un site protégé par des autorisations, puis le télécharger sur un site disposant d’autorisations élargies.
  
Tout d’abord, vous ajoutez trois nouveaux comptes d’utilisateur qui représentent les cadres et vous leur affectez des licences Office 365 E5.
  
Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell (si nécessaire) et de vous connecter à votre nouvel abonnement Office 365 à partir de :
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** , tapez le nom d’administrateur global de Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe de votre abonnement d’évaluation d’Office 365.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur général et l’enregistrer dans un emplacement sûr.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur financier et l’enregistrer dans un emplacement sûr.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de directeur des opérations et l’enregistrer dans un emplacement sûr.
  
Ensuite, créez un groupe de cadres privé et ajoutez les nouveaux comptes d’encadrement.
  
1. Dans votre navigateur, accédez au portail Office à [http://portal.office.com](http://portal.office.com) et connectez-vous à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer ou votre navigateur et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 avec entreprise simulée, utilisez le portail Azure pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin > groupes > groupes de**, puis cliquez sur **Ajouter un groupe**.
    
3. Dans **Ajouter un groupe**, sélectionnez **groupe d’Office 365** pour le type de groupe tapez **dirigeants** dans le **nom** et l' **Id de groupe**, sélectionnez **privé** pour la **confidentialité**, puis cliquez sur **Sélectionner un propriétaire**.
    
4. Dans la liste, cliquez sur le nom de votre compte d’administrateur général.
    
5. Cliquez sur **Ajouter**, puis cliquez sur **Fermer**.
    
6. Dans la liste groupes, cliquez sur **cadres**.
    
7. Cliquez sur **Modifier pour les membres**.
    
8. Cliquez sur **Ajouter des membres**. Dans la liste des membres, sélectionnez les comptes d’utilisateurs suivants :
    
  - Directeur général
    
  - Directeur financier
    
  - Directeur des opérations
    
9. Cliquez sur **Enregistrer**, puis cliquez sur **Fermer**.
    
10. Fermez l’onglet **Centre d’administration de l’Office** .
    
Ensuite, créez une collection de sites de cadres et autorisez uniquement les membres du groupe de cadres à y accéder.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .
    
2. Dans l’onglet **Centre d’administration d’Office** , cliquez sur **Centre d’administration > SharePoint**.
    
3. Dans l’onglet **Centre d’administration de SharePoint** , cliquez sur **Nouveau > collection de sites privé**.
    
4. Dans le nouveau volet de collection de sites, tapez **dirigeants** dans le **titre**, cadres dans la zone URL, spécifiez le nom de votre compte d’administrateur global dans **l’administrateur**et puis cliquez sur **OK**.
    
5. Attendez que la nouvelle collection de site a été créée. Lorsque vous avez terminé, copiez l’URL de la collection de sites de cadres et les coller dans un nouvel onglet de votre navigateur.
    
6. Dans le coin supérieur droit de la collection de sites de **cadres** , cliquez sur l’icône de paramètres, puis cliquez sur **partagé avec**.
    
7. Dans **partage 'Dirigeants'**, cliquez sur **Avancé**.
    
8. Dans la liste des groupes SharePoint, cliquez sur **Membres de la direction**.
    
9. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
10. Dans **partage 'Dirigeants'**, tapez des **cadres**, cliquez sur le groupe de **cadres** , puis cliquez sur **partage**.
    
11. Fermez l’onglet **personnes et groupes** .
    
Ensuite, autorisez tout le monde à accéder à la collection de sites de ventes.
  
1. Dans l’onglet **Centre d’administration SharePoint** , copiez l’URL de la collection de sites de vente et le coller dans un nouvel onglet de votre navigateur...
    
2. Dans le coin supérieur droit, cliquez sur l’icône de paramètres, puis cliquez sur **partagé avec**.
    
3. Dans **partage « Collection de sites ventes »**, cliquez sur **Avancé**.
    
4. Dans la liste des groupes SharePoint, cliquez sur **membres de collection de sites de vente**.
    
5. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
6. Dans **partage « Collection de sites de vente »**, tapez **tout le monde**, cliquez sur **tout le monde excepté les utilisateurs externes**, puis cliquez sur **partage**.
    
7. Fermer les onglets de la **collection de sites de vente** et de **SharePoint** .
    
Ensuite, connectez-vous avec un compte de cadre et créez un document dans la collection de sites Cadres.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.
    
4. Tapez le nom du compte **PDG** et son mot de passe, puis cliquez sur **se connecter**.
    
5. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/executives**).
    
6. Cliquez sur **Documents**et cliquez sur **Nouveau,** puis cliquez sur **Document Word**.
    
7. Cliquez sur dans la barre de titre, tapez **SensitiveData-BeforeIRM**.
    
8. Cliquez dans le corps du document et tapez **Minutes à partir de la dernière réunion du Conseil**, puis cliquez sur **cadres**.
    
     Vous devriez voir **SensitiveData-BeforeIRM.docx** dans le dossier **Documents** .
    
Ensuite, vous téléchargez une copie locale du document SensitiveData-BeforeIRM.docx et la publiez accidentellement dans la collection de sites Ventes.
  
1. Sur votre ordinateur local, créez un nouveau dossier (par exemple, C:\\TLGs\\SensitiveDataTestFiles).
    
2. Sous l’onglet **Documents** de votre navigateur, sélectionnez le document **SensitiveData-BeforeIRM.docx** , cliquez sur le bouton de sélection, puis cliquez sur **Télécharger**.
    
3. Stocker le document **SensitiveData-BeforeIRM.docx** dans le dossier créé à l’étape 1.
    
4. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente ( **https://**\<nom de l’organisation >**.sharepoint.com/sites/sales**).
    
5. Cliquez sur le dossier de **Documents** de la **collection de sites de vente**.
    
6. Cliquez sur **Télécharger**, puis spécifiez **SensitiveData-BeforeIRM.docx** document dans le dossier créé à l’étape 1 et puis cliquez sur **OK**.
    
7. Vérifiez que le document **SensitiveData-BeforeIRM.docx** est dans le dossier **Documents** .
    
8. Fermer les onglets **ventes** et **SharePoint** .
    
Ensuite, connectez-vous en tant que Utilisateur 5 et essayez d’ouvrir le document SensitiveData-BeforeIRM.docx dans la collection de sites de ventes.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur **utiliser un autre compte**.
    
4. Tapez le nom de compte de User5 et de son mot de passe, puis cliquez sur **se connecter**.
    
5. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.
    
6. Dans le dossier **Documents** de la **collection de sites de vente**, cliquez sur le document **SensitiveData-BeforeIRM.docx** .
    
    Vous devriez voir son contenu.
    
7. Fermer les onglets de **Documents** et de **collection de sites de vente** .
    
En publiant accidentellement le document SensitiveData-BeforeIRM.docx sur la collection de sites de ventes, le directeur général a ignoré la sécurité des autorisations de la collection de sites Cadres.
  
Pour préparer Office 365 pour les phases 3 et 4, activez IRM pour SharePoint Online.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur le nom du compte administrateur global, tapez son mot de passe, puis cliquez sur **connexion**.
    
4. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin > centres d’administration > SharePoint**.
    
5. Dans l’onglet **Centre d’administration de SharePoint** , cliquez sur **paramètres**.
    
6. Dans la page **paramètres** , dans la section **Gestion des droits relatifs à l’Information (IRM)** , sélectionnez **utiliser le service IRM spécifié dans votre configuration**et sélectionnez **Actualiser les paramètres IRM**.
    
7. Fermez l’onglet **Centre d’administration SharePoint** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Phase 3 : Utiliser la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365

Lors de cette phase, vous utilisez la Gestion des droits relatifs à l’information de SharePoint avec un groupe privé d’Office 365 pour protéger l’accès à un document contenant des informations sensibles, même lorsqu’il est publié sur un site avec des autorisations d’ouverture.
  
Tout d’abord, vous activez et configurez IRM pour la bibliothèque de documents de la collection de sites Cadres.  
  
1. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.
    
2. Cliquez sur **Documents**.
    
3. Dans l’angle supérieur droit, cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
4. Dans la page **paramètres** , sous **autorisations et gestion**, cliquez sur **Information Rights Management**.
    
5. Dans la page **Paramètres de gestion des droits d’informations** :
    
  - Sélectionnez **restreindre l’accès aux documents de cette bibliothèque au téléchargement**.
    
  - Pour **créer un titre de stratégie d’autorisation**, tapez **dirigeants**.
    
  - Pour **Ajouter une description de stratégie d’autorisation**, tapez **IRM pour les cadres**.
    
6. Cliquez sur **Afficher les Options**.
    
7. Sous **définir les paramètres de la bibliothèque supplémentaires IRM**, sélectionnez **ne pas autoriser les utilisateurs à télécharger des documents qui ne prennent pas en charge les IRM**.
    
8. Sous **Configuration des droits d’accès document**, sélectionnez **Autoriser les utilisateurs à imprimer** et **Autoriser les utilisateurs à écrire sur une copie du document téléchargé**.
    
9. Sous **définir le groupe de protection et intervalle d’informations d’identification**, sélectionnez **Autoriser du groupe de protection** et pour le **groupe par défaut**, tapez des **cadres**.
    
10. Cliquez sur **OK**.
    
Ensuite, en jouant le rôle du directeur général, vous chargez un nouveau document dans le dossier de documents Cadres, le téléchargez, puis le chargez accidentellement dans le dossier de documents Ventes.
  
1. Ouvrez le dossier local dans lequel est stocké le document **SensitiveData-BeforeIRM.docx** .
    
2. Droit **SensitiveData-BeforeIRM.docx**, puis cliquez sur **Copier**.
    
3. Avec le bouton droit dans le dossier, puis cliquez sur **Coller**.
    
4. Renommez le nouveau fichier **SensitiveData-BeforeIRM - Copy.docx** **AfterIRM.docx-SensitiveData**.
    
5. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.
    
6. Accédez à [http://portal.office.com](http://portal.office.com).
    
7. Dans la page **Office 365 se connecter** , cliquez sur le nom de compte de PDG, tapez son mot de passe, puis cliquez sur **connexion**.
    
8. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites responsables.
    
9. Sur la page **Documents** , cliquez sur **Télécharger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.
    
10. Sélectionnez le nouveau document **SensitiveData-AfterIRM.docx** dans la page **Documents** et cliquez sur le bouton de sélection (...) dans la barre de menus, puis cliquez sur **Télécharger**.
    
11. Lorsque vous y êtes invité, enregistrez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, en remplaçant la version d’origine.
    
12. Fermer l’onglet de la page de **Documents** .
    
13. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.
    
14. Cliquez sur **Documents**.
    
15. Sur la page **Documents** , cliquez sur **Télécharger**, spécifiez le document **SensitiveData-AfterIRM.docx** dans votre dossier local, puis cliquez sur **Ouvrir**.
    
16. Fermer les onglets de la **collection de sites de vente** et de **SharePoint** .
    
Agissant comme un utilisateur normal, vous essayez ensuite d’accéder au document **SensitiveData-AfterIRM.docx** dans le dossier de document de vente.
  
1. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5, tapez son mot de passe, puis cliquez sur **connexion**.
    
4. Dans un nouvel onglet de votre navigateur, tapez l’URL de la collection de sites de vente.
    
5. Cliquez sur **Documents**.
    
6. Sur la page **Documents** , ouvrez le document **SensitiveData-AfterIRM.docx** .
    
    Vous devez voir un message indiquant « Désolé, Word Online ne peut pas ouvrir ce document, car il est protégé par la Gestion des droits relatifs à l’information (IRM). »  
    
7. Cliquez sur **Modifier dans Word**. Vous êtes invité si vous souhaitez ouvrir le fichier. Cliquez sur **Oui**.
    
8. Vous êtes invité à connexion tapez le nom de compte du compte User5, puis cliquez sur **suivant**.
    
9. Vous êtes invité à fournir le mot de passe. Tapez le mot de passe pour le compte User5 et puis cliquez sur **connexion**. 
    
    Vous devez voir un message indiquant ce qui suit : « Vous ne disposez pas des informations d’identification requises pour ouvrir ce document. »
    
10. Cliquez sur **non**.
    
Une autre façon de voir la protection IRM consiste à rechercher les fichiers dans votre dossier local. **SensitiveData-AfterIRM.docx** doit être beaucoup plus volumineux que le fichier **SensitiveData-BeforeIRM.docx** . Le fichier **AfterIRM.docx-SensitiveData** est crypté et possède les informations de protection IRM ajoutés.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


