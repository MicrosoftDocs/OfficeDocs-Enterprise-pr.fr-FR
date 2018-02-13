---
title: "Environnement de développement/test isolé de SharePoint Online équipe site"
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
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "Résumé : Configuration d’un site d’équipe SharePoint en ligne qui est isolé du reste de l’organisation dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: 75a469b50603d5eb398d1e15d37c6745bc0a48b8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>Environnement de développement/test isolé de SharePoint Online équipe site

 **Résumé :** Configurer un site d’équipe SharePoint en ligne qui est isolé du reste de l’organisation dans votre environnement de développement/test d’Office 365.
  
Les sites d’équipe SharePoint Online dans Office 365 sont des emplacements pour la collaboration à l’aide d’une bibliothèque de documents commune, un bloc-notes OneNote et d’autres services. Dans de nombreux cas, vous souhaitez accès étendu et la collaboration entre les départements ou organisations. Toutefois, dans certains cas, vous souhaitez contrôler étroitement l’accès et les autorisations pour la collaboration entre un petit groupe de personnes.
  
Accès à des sites d’équipe SharePoint Online et à ce que peuvent faire les utilisateurs est contrôlé par les niveaux d’autorisation et des groupes SharePoint. Par défaut, les sites SharePoint Online ont trois niveaux d’accès :
  
- **Membres**, qui peut afficher, créer et modifier des ressources sur le site.
    
- **Propriétaires**, qui ont un contrôle total du site, y compris la possibilité de modifier les autorisations.
    
- **Les visiteurs**, qui peut uniquement afficher des ressources sur le site.
    
Les étapes de cet article vous guide dans la configuration d’un site d’équipe SharePoint Online isolé pour un projet de recherche secret nommé ProjectX. Les conditions d’accès sont les suivants :
  
- Seuls les membres du projet peuvent accéder au site et à son contenu (documents, bloc-notes OneNote, pages), avec des niveaux d’autorisation SharePoint pour éditer et afficher contrôlés via l’appartenance au groupe.
    
- Seuls le créateur du site et les membres d’un groupe d’administrateurs du site peuvent effectuer l’administration du site, y compris la modification des autorisations au niveau du site.
    
Il existe trois phases de configuration d’un site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365 :
  
1. Créez l’environnement de développement/test Office 365.
    
2. Créez les utilisateurs et groupes pour ProjectX.
    
3. Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler.
    
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous voulez simplement créer un site d’équipe SharePoint Online isolé de manière légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez créer un site d’équipe SharePoint Online isolé dans une configuration d’entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La création d’un site SharePoint Online isolé ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server AD. Il est proposé comme option dans cet article afin que vous puissiez tester un site SharePoint Online isolé et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>Phase 2 : Créer des comptes d’utilisateurs et de groupes d’accès

Suivez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour se connecter à votre abonnement à Office 365 piste avec votre compte d’administrateur global à partir de :
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
Pour créer de nouveaux groupes d’accès pour le site d’équipe ProjectX SharePoint Online, exécuter ces commandes à partir de l’invite de Windows Azure Active Directory Module pour Windows PowerShell :
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) pour un fichier texte qui contient toutes les commandes de PowerShell dans cet article.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de conduire le concepteur et l’enregistrer dans un emplacement sûr.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de conduire l’Organise-notes et l’enregistrer dans un emplacement sûr.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de l’affichage de la commande **New-MsolUser** , notez le mot de passe généré pour le compte de vice-président du développement et de l’enregistrer dans un emplacement sûr.
  
Ensuite, pour ajouter de nouveaux comptes pour les nouveaux groupes d’accès, exécutez ces commandes PowerShell à partir de l’invite de Windows Azure Active Directory Module pour Windows PowerShell :
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

Résultats :
  
- Le groupe d’accès membres ProjectX contenant les comptes Concepteur de conduire et mener l’Organise-notes
    
- Le groupe d’accès Admins-ProjectX contient le compte d’administrateur global pour votre version d’essai
    
- Le groupe d’accès-visionneuses ProjectX contient le compte d’utilisateur vice-président du développement
    
La figure 1 illustre l’accès aux groupes et leur appartenance.
  
**Figure 1**

![Groupes Office 365 et leur appartenance pour un site de groupe SharePoint Online isolé](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>Phase 3 : Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler

Pour créer un site d’équipe SharePoint Online pour ProjectX, effectuez les opérations suivantes :
  
1. En utilisant un navigateur soit sur votre ordinateur local (configuration léger) ou sur CLIENT1 (configuration entreprise simulation), connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet Nouveau SharePoint dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la zone **nom du site d’équipe**, tapez **ProjectX**. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**.
    
5. Dans la **description de site d’équipe**, tapez le **site SharePoint pour ProjectX**, puis cliquez sur **suivant**.
    
6. À **qui voulez-vous ajouter**? volet, cliquez sur **Terminer**.
    
7. Sur le nouvel onglet **Accueil-ProjectX** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
8. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
9. Dans la nouvelle **autorisations : projet X** dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
10. Dans la boîte de dialogue **Paramètres de demandes d’accès** , désactivez **Autoriser les demandes d’accès** et de **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur **OK**.
    
11. Dans la liste, cliquez sur **Les membres de ProjectX** .
    
12. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
13. Dans la boîte de dialogue **partage** , **ProjectX-membres**de type, sélectionnez-le, puis cliquez sur **partage**.
    
14. Cliquez sur le bouton de retour de votre navigateur.
    
15. Dans la liste, cliquez sur **ProjectX propriétaires** .
    
16. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
17. Dans la boîte de dialogue de **partage** , tapez **Admins-ProjectX**, sélectionnez-le, puis cliquez sur **partage**.
    
18. Cliquez sur le bouton de retour de votre navigateur.
    
19. Dans la liste, cliquez sur **Les visiteurs de ProjectX** .
    
20. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
21. Dans la boîte de dialogue **partage** , **ProjectX-visionneuses**de type, sélectionnez-le, puis cliquez sur **partage**.
    
22. Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **Accueil-ProjectX** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint des membres ProjectX contient uniquement le groupe d’accès membres ProjectX (qui contienne uniquement les comptes d’utilisateurs Concepteur de conduire et mener l’Organise-notes) et le groupe ProjectX (qui contient uniquement le compte d’utilisateur administrateur global).
    
- Le groupe SharePoint propriétaires de ProjectX contient uniquement le groupe d’accès Admins-ProjectX (qui contient uniquement le compte d’utilisateur administrateur global).
    
- Le groupe SharePoint visiteurs de ProjectX contient uniquement le groupe d’accès ProjectX-afficheurs (qui contient uniquement le compte d’utilisateur vice-président du développement).
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe ProjectX-Administrateurs).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, ni demander l’accès au site.
    
La figure 2 présente les groupes SharePoint et leur appartenance.
  
**Figure 2**

![Groupes SharePoint Online et leur appartenance pour un site de groupe SharePoint Online isolé](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
Maintenant illustrons access en utilisant le compte d’utilisateur de conduire le concepteur :
  
1. Fermer l’onglet **Accueil-ProjectX** dans votre navigateur, puis cliquez sur l’onglet **d’Accueil de Microsoft Office** dans votre navigateur.
    
2. Cliquez sur le nom de l’administrateur général, puis cliquez sur **se déconnecter**.
    
3. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom de compte de conduire le concepteur et son mot de passe.
    
4. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
5. Sur le nouvel onglet **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone de recherche, activez la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour que le site d’équipe ProjectX.
    
6. Cliquez sur l’icône Paramètres. Notez qu’il n’existe aucune option pour les **Autorisations du Site**. Cela est correct, car seuls les membres du groupe Administrateurs de le ProjectX peuvent modifier les autorisations sur le site
    
7. Ouvrez le bloc-notes ou un éditeur de texte de votre choix.
    
8. Copiez l’URL du site d’équipe ProjectX et le coller dans une nouvelle ligne dans le bloc-notes ou votre éditeur de texte.
    
9. Sur le nouvel onglet **Accueil-ProjectX** dans votre navigateur, cliquez sur **Documents**.
    
10. Copiez l’URL du dossier de documents ProjectX et collez-la dans une nouvelle ligne dans le bloc-notes ou dans votre éditeur de texte.
    
11. Dans le nouvel onglet de **ProjectX-Documents** dans votre navigateur, cliquez sur **Nouveau > document Word**.
    
12. Tapez du texte dans la page **En ligne de Word** , attendez que l’état indiquer **l’enregistrement**et cliquez sur le bouton précédente de votre navigateur, puis actualisez la page. Vous devriez voir un nouveau **Document.docx** dans le dossier **Documents** .
    
13. Cliquez sur le bouton de sélection pour le document **Document.docx** , puis cliquez sur **obtenir un lien**.
    
14. Copiez l’URL dans la boîte de dialogue **partage 'Document.docx'** et collez-le sur une nouvelle ligne dans le bloc-notes ou votre éditeur de texte et puis fermez la boîte de dialogue **partage 'Document.docx'** .
    
15. Fermer les onglets de **Documents ProjectX** et **SharePoint** dans votre navigateur, puis cliquez sur l’onglet **d’Accueil de Microsoft Office** .
    
16. Cliquez sur le nom du **Concepteur de prospect** , puis cliquez sur **se déconnecter**.
    
Maintenant nous allons démontrer access en utilisant le compte d’utilisateur vice-président du développement :
  
1. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom de compte de vice-président du développement et de son mot de passe.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Sur le nouvel onglet **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone de recherche, activez la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour que le site d’équipe ProjectX.
    
4. Cliquez sur **Documents**, puis cliquez sur le fichier **Document.docx** .
    
5. Dans l’onglet **Document.docx** dans votre navigateur, essayez de modifier le texte. Vous devriez voir un message indiquant que **ce document est en lecture seule.** Ceci est dû au fait que le compte d’utilisateur vice-président du développement dispose uniquement d’autorisations d’affichage pour le site.
    
6. Fermer les onglets **Document.docx**et **ProjectX-Documents** **SharePoint** dans votre navigateur.
    
7. Cliquez sur l’onglet **d’Accueil de Microsoft Office** , cliquez sur le nom du **Directeur de développement** , puis cliquez sur **se déconnecter**.
    
Maintenant nous allons démontrer l’accès avec un compte d’utilisateur qui n’est pas autorisé :
  
1. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom du compte utilisateur 3 et son mot de passe.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone Rechercher et puis activer la recherche. Vous devriez voir le message **rien ici correspond à votre recherche.**
    
4. À partir de l’instance ouverte de bloc-notes ou votre éditeur de texte, copiez l’URL du site de ProjectX dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .
    
5. Dans le bloc-notes ou votre éditeur de texte, copiez l’URL du dossier Documents de ProjectX dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .
    
6. Dans le bloc-notes ou votre éditeur de texte, copiez l’URL pour le fichier Documents.docx dans la barre d’adresses de votre navigateur et appuyez sur **entrée**. Vous devriez voir une page **Accès refusé** .
    
7. Fermer l’onglet **SharePoint** dans votre navigateur, cliquez sur l’onglet **d’Accueil de Microsoft Office** , cliquez sur le nom de **l’utilisateur 3** , puis cliquez sur **se déconnecter**.
    
Votre site SharePoint Online isolé est prêt pour une expérimentation supplémentaire.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous souhaitez déployer un site d'équipe SharePoint Online isolé en production, lisez la procédure détaillée dans la rubrique [Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Voir aussi

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




