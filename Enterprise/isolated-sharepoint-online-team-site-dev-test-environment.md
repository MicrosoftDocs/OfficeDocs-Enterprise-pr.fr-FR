---
title: Site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: 'Résumé : Configurer un site d’équipe SharePoint Online isolé du reste de l’organisation dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915049"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>Site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365

 **Résumé :** Configurer un site d’équipe SharePoint Online isolé du reste de l’organisation dans votre environnement de développement/test Office 365.
  
Sites d’équipe SharePoint Online dans Office 365 sont des emplacements pour la collaboration à l’aide d’une bibliothèque de documents commune, un bloc-notes OneNote et d’autres services. Dans de nombreux cas, vous souhaitez accéder à l’échelle et collaboration entre les départements ou organisations. Toutefois, dans certains cas, vous souhaitez contrôler étroitement les accès et les autorisations pour la collaboration entre un petit groupe de personnes.
  
Accès aux sites d’équipe SharePoint Online et les utilisateurs peuvent faire est contrôlé par les groupes SharePoint et les niveaux d’autorisation. Par défaut, les sites SharePoint Online disposent des trois niveaux d’accès :
  
- Les **membres** peuvent afficher, créer et modifier des ressources sur le site.
    
- Les **propriétaires** ont un contrôle total sur le site, et peuvent même modifier les autorisations.
    
- Les **Visiteurs** peuvent uniquement afficher les ressources du site.
    
Étapes de cet article vous aide à la configuration d’un site d’équipe SharePoint Online isolé pour un projet de recherche secrète nommé ProjectX. Les exigences d’accès sont les suivants :
  
- Seuls les membres du projet peuvent accéder au site et à son contenu (documents, bloc-notes OneNote, pages), avec des niveaux d’autorisation SharePoint pour éditer et afficher contrôlés via l’appartenance au groupe.
    
- Seuls le créateur du site et les membres d’un groupe d’administrateurs du site peuvent effectuer l’administration du site, y compris la modification des autorisations au niveau du site.
    
Il existe trois phases de configuration d’un site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365 :
  
1. Créez l’environnement de développement/test Office 365.
    
2. Créez les utilisateurs et groupes pour ProjectX.
    
3. Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler.
    
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez simplement créer un site d’équipe SharePoint Online isolé dans une solution légère avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez créer un site d’équipe SharePoint Online isolé dans une configuration enterprise simulé, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La création d’un site SharePoint Online isolé ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server AD. Il est proposé comme option dans cet article afin que vous puissiez tester un site SharePoint Online isolé et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>Phase 2 : Créer des comptes d’utilisateurs et groupes d’accès

Utilisez les instructions de [se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour se connecter à votre abonnement à Office 365 piste avec votre compte d’administrateur global à partir de :
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
Pour créer les nouveaux groupes d’accès pour le site d’équipe ProjectX SharePoint Online, exécutez les commandes suivantes depuis l’invite de Windows Azure Active Directory Module pour Windows PowerShell :
  
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
> Cliquez [ici](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) pour un fichier texte qui contient toutes les commandes PowerShell dans cet article.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Responsable de la conception et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Responsable de la recherche et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

À partir de la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte VP du développement et enregistrez-le dans un emplacement sécurisé.
  
Ensuite, pour ajouter les nouveaux comptes pour les nouveaux groupes d’accès, exécutez ces commandes PowerShell depuis l’invite de Windows Azure Active Directory Module pour Windows PowerShell :
  
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
  
- Le groupe d’accès ProjectX : les membres contenant les comptes Designer conduire et enquêteur prospect
    
- Le groupe d’accès ProjectX-Admins contient le compte d’administrateur global de votre abonnement d’évaluation
    
- Le groupe d’accès ProjectX-visionneuses contient le compte d’utilisateur relatives au vice-président de développement
    
La figure 1 montre les groupes d’accès et de leur appartenance.
  
**Figure 1**

![Groupes Office 365 et leur appartenance pour un site de groupe SharePoint Online isolé](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>Phase 3 : Créer un nouveau site d’équipe ProjectX SharePoint Online et isoler

Pour créer un site d’équipe SharePoint Online pour ProjectX, procédez comme suit :
  
1. Via un navigateur soit sur votre ordinateur local (configuration léger) ou sur CLIENT1 (configuration entreprise simulé), connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet SharePoint de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans **nom du site d’équipe**, tapez **ProjectX**. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**.
    
5. Dans **Description du site d’équipe**, saisissez **Site SharePoint pour ProjectX**, puis cliquez sur **Suivant**.
    
6. **Qui vous voulez ajouter**? volet, cliquez sur **Terminer**.
    
7. Dans le nouvel onglet **ProjectX-Accueil** de votre navigateur, dans la barre d’outils, cliquez sur l’icône des paramètres, puis sur **Autorisations du site**.
    
8. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
9. Dans le nouvel onglet **Autorisations : Projet X** de votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
10. Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les demandes d’accès** (afin que les trois cases à cocher soient désactivées), puis cliquez sur **OK**.
    
11. Cliquez sur **Membres de ProjectX** dans la liste.
    
12. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
13. Dans la boîte de dialogue **Partager**, saisissez **ProjectX-Membres**, sélectionnez-le, puis cliquez sur **Partager**.
    
14. Cliquez sur le bouton de retour de votre navigateur.
    
15. Cliquez sur **Propriétaires de ProjectX** dans la liste.
    
16. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
17. Dans la boîte de dialogue **Partager**, saisissez **ProjectX-Administrateurs**, sélectionnez-le, puis cliquez sur **Partager**.
    
18. Cliquez sur le bouton de retour de votre navigateur.
    
19. Cliquez sur **Visiteurs de ProjectX** dans la liste.
    
20. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
21. Dans la boîte de dialogue **Partager**, saisissez **ProjectX-Utilisateurs**, sélectionnez-le, puis cliquez sur **Partager**.
    
22. Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **ProjectX-Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.

    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint des membres ProjectX contient uniquement le groupe d’accès ProjectX-membres (qui contienne uniquement les comptes d’utilisateur Designer conduire et enquêteur conduire) et le groupe ProjectX (qui contient le compte d’utilisateur administrateur global uniquement).
    
- Groupe SharePoint propriétaires de ProjectX contient uniquement le groupe d’accès Admins-ProjectX (qui contient le compte d’utilisateur administrateur global uniquement).
    
- Le groupe SharePoint des visiteurs ProjectX contient uniquement le groupe d’accès-visionneuses ProjectX (qui contient le compte d’utilisateur relatives au vice-président développement uniquement).
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe ProjectX-Administrateurs).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, ni demander l’accès au site.
    
La figure 2 présente les groupes SharePoint et leur appartenance.
  
**Figure 2**

![Groupes SharePoint Online et leur appartenance pour un site de groupe SharePoint Online isolé](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
Maintenant nous allons démontrer access en utilisant le compte d’utilisateur Designer conduire :
  
1. Fermez l’onglet **ProjectX-Accueil** dans votre navigateur, puis cliquez sur l’onglet **Accueil Microsoft Office** du navigateur.
    
2. Cliquez sur le nom de votre administrateur général, puis cliquez sur **Déconnexion**.
    
3. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom du compte Designer conduire et son mot de passe.
    
4. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
5. Dans l’onglet nouveau **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone Rechercher, activer la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour le site d’équipe ProjectX.
    
6. Cliquez sur l’icône des paramètres. Notez qu’il n’existe pas d’option pour **Autorisations du site**. Cela est correct puisque seuls les membres du groupe ProjectX-Administrateurs peuvent modifier les autorisations sur le site
    
7. Ouvrez le bloc-notes ou un éditeur de texte de votre choix.
    
8. Copiez l’URL du site d’équipe ProjectX et le coller dans une nouvelle ligne dans le bloc-notes ou votre éditeur de texte.
    
9. Dans le nouvel onglet **ProjectX-Accueil** de votre navigateur, cliquez sur **Documents**.
    
10. Copiez l’URL du dossier de documents ProjectX et collez-la dans une nouvelle ligne dans le bloc-notes ou dans votre éditeur de texte.
    
11. Dans le nouvel onglet **ProjectX-Documents** de votre navigateur, cliquez sur **Nouveau > Document Word**.
    
12. Saisissez du texte dans la page **Word Online**, attendez que l’état indique **Enregistré**et cliquez sur le bouton de retour de votre navigateur, puis actualisez la page. Vous devriez voir un nouveau **Document.docx** dans le dossier **Documents**.
    
13. Cliquez sur les points de suspension du document **Document.docx**, puis sur **Obtenir un lien**.
    
14. Copiez l’URL dans la boîte de dialogue **partager 'Document.docx'** et coller dans une nouvelle ligne dans le bloc-notes ou votre éditeur de texte, puis fermez la boîte de dialogue **partager « Document.docx »** .
    
15. Fermez les onglets **ProjectX-Documents** et **SharePoint** dans votre navigateur, puis cliquez sur l’onglet **Accueil Microsoft Office**.
    
16. Cliquez sur le nom **Responsable de la conception**, puis cliquez sur **Déconnexion**.

    
Maintenant nous allons démontrer access à l’aide du compte d’utilisateur relatives au vice-président de développement :
  
1. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom du compte VP de développement et son mot de passe.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, tapez **ProjectX** dans la zone Rechercher, activer la recherche, puis cliquez sur le site d’équipe **ProjectX** . Vous devriez voir un nouvel onglet dans votre navigateur pour le site d’équipe ProjectX.
    
4. Cliquez sur **Documents**, puis sur le fichier **Document.docx**.
    
5. Dans l’onglet **Document.docx** de votre navigateur, essayez de modifier le texte. Vous devriez voir un message indiquant **Ce document est en lecture seule.** Ceci est dû au fait que le compte d’utilisateur VP du développement comporte seulement des autorisations d’affichage pour le site.
    
6. Fermer les onglets **Document.docx**, **ProjectX-Documents** et **SharePoint** de votre navigateur.
    
7. Cliquez sur l’onglet **Accueil Microsoft Office**, sur le nom **VP du développement**, puis sur **Déconnexion**.

    
Maintenant nous allons démontrer access avec un compte d’utilisateur qui n’a aucune autorisation :
  
1. Connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant le nom du compte utilisateur 3 et son mot de passe.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. 	Dans le nouvel onglet **SharePoint** de votre navigateur, saisissez **ProjectX** dans la zone de recherche, puis activez la recherche. Vous devriez voir le message **Aucun résultat ne correspond à votre recherche.**
    
4. À partir de l’instance ouverte du bloc-notes ou de votre éditeur de texte, copiez l’URL du site ProjectX dans la barre d’adresses de votre navigateur, puis appuyez sur **Entrée**. Vous devriez voir une page **Accès refusé**.
    
5. À partir du bloc-notes ou votre éditeur de texte, copiez l’URL du dossier Documents ProjectX dans la barre d’adresses de votre navigateur, puis appuyez sur **Entrée**. Vous devriez voir une page **Accès refusé**.
    
6. À partir du bloc-notes ou votre éditeur de texte, copiez l’URL du fichier Documents.docx dans la barre d’adresses de votre navigateur, puis appuyez sur **Entrée**. Vous devriez voir une page **Accès refusé**.
    
7. Fermez l’onglet **SharePoint** de votre navigateur, cliquez sur l’onglet **Accueil Microsoft Office**, sur le nom **Utilisateur 3**, puis sur **Déconnexion**.

    
Votre site SharePoint Online isolé est maintenant prête pour votre expérimentation supplémentaire.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous souhaitez déployer un site d'équipe SharePoint Online isolé en production, lisez la procédure détaillée dans la rubrique [Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Voir aussi

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




