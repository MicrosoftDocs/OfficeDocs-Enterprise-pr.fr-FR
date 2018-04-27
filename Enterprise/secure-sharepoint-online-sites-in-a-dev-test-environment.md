---
title: Sécuriser les sites SharePoint Online dans un environnement de développement/test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Résumé : Créez des sites d’équipe SharePoint Online publics, private, sensibles et hautement confidentielles dans un environnement de développement/test.'
ms.openlocfilehash: 8c02f1416cb00150e68dcc27dc7afb41bf82ed21
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Sécuriser des sites SharePoint Online dans un environnement de développement et de test

 **Résumé :** Créer des sites d’équipe SharePoint Online publics, private, sensibles et hautement confidentielles dans un environnement de développement/test.
  
Cet article fournit des instructions détaillées pour créer un environnement de développement/test qui inclut quatre types de sites d’équipe SharePoint Online pour la solution de [fichiers et des sites d’informations sécurisé SharePoint Online](secure-sharepoint-online-sites-and-files.md) .
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Utilisez cet environnement de développement/test pour expérimenter les comportements de protection des informations et optimiser les paramètres en fonction de vos besoins avant de déployer des sites d’équipe SharePoint Online en production.
  
## <a name="phase-1-create-your-devtest-environment"></a>Phase 1 : Créer votre environnement de développement et de test

Dans cette phase, vous obtenez des abonnements d’essai pour Office 365 et Enterprise Mobility + Security pour une entreprise fictive.
  
Suivez d’abord les instructions de la **Phase 2** de [l’environnement de développement et de test Office 365](office-365-dev-test-environment.md).
  
Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la vignette **Administration**.
    
3. Sous l’onglet **Centre d’administration Office** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **services d’achat** , trouver l’élément de la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris au-dessus de celle-ci, cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
Ensuite, activez la licence Enterprise Mobility + Security E5 pour votre compte d’administrateur général.
  
1. Sous l’onglet **Centre d’administration Office 365** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet de **licences** , activer la licence de produit pour la **mobilité d’entreprise + sécurité E5** **activé**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2 : Créer et configurer vos groupes et vos utilisateurs Azure Active Directory (AD)

Dans cette phase, vous créez et vous configurez les groupes et les utilisateurs Azure AD de votre organisation fictive.
  
Commencez par créer un ensemble de groupes pour une organisation standard avec le portail Azure.
  
1. Créer un onglet séparé dans votre navigateur, puis accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous à l’aide les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation Office 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Utilisateurs et groupes > Tous les groupes**.
    
3. Dans le panneau **Tous les groupes**, cliquez sur **+ Nouveau groupe**.
    
4. Dans le panneau **Groupe** :
    
  - Tapez **C-Suite** dans le champ **Nom**.
    
  - Sélectionnez **Affecté** dans le champ **Appartenance**.
    
  - Cliquez sur **Oui** pour **Activer les fonctionnalités Office**.
    
5. Cliquez sur **Créer** et fermez le panneau **Groupe**.
    
6. Répétez les étapes 3 à 5 pour les noms de groupe suivants :
    
  - Équipe Informatique
    
  - Équipe Recherche
    
  - Équipe Standard
    
  - Équipe Marketing
    
  - Équipe Ventes
    
7. Gardez ouvert l’onglet du portail Azure dans votre navigateur.
    
Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > Licences > Tous les produits**.
    
2. Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**, puis cliquez sur **affecter**.
    
3. Dans le panneau **Affecter une licence**, cliquez sur **Utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - C-Suite
    
  - Équipe Informatique
    
  - Équipe Recherche
    
  - Équipe Standard
    
  - Équipe Marketing
    
  - Équipe Ventes
    
5. Cliquez sur **Sélectionner**, puis cliquez sur **affecter**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
Ensuite, vous vous [connectez au module PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Renseignez nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou Integrated Script Environment (ISE) pour créer des comptes d’utilisateurs et les ajouter à leurs groupes :
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> L’utilisation d’un mot de passe commun permet d’automatiser et de faciliter la configuration d’un environnement de développement/test. Il n’est pas recommandé de l’utiliser dans un environnement de production. 
  
Utilisez ces étapes pour vérifier que la gestion des licences basée sur un groupe fonctionne correctement.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Administration**.
    
2. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Utilisateurs**.
    
3. Dans la liste des utilisateurs, cliquez sur **PDG**.
    
4. Dans le volet qui affiche les propriétés du compte d’utilisateur **PDG**, vérifiez que les licences **Enterprise Mobility + Security E5** et **Office 365 Enterprise E5** lui ont été affectées (dans **Licences de produit**).
    
## <a name="phase-3-create-office-365-labels"></a>Phase 3 : Créer des étiquettes Office 365

Dans cette phase, vous créez les étiquettes pour les différents niveaux de sécurité des dossiers de documents du site d’équipe SharePoint Online.
  
1. Si nécessaire, utilisez une instance privée de votre navigateur Internet et connectez-vous au portail Office 365 avec le compte d’administrateur global de votre abonnement d’évaluation Office 365 E5. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.
    
3. À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **centres d’administration > sécurité &amp; conformité**.
    
4. À partir du nouveau **Accueil - sécurité &amp; conformité** onglet de votre navigateur, cliquez sur **Classifications > étiquettes**.
    
5. Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.
    
6. Dans le volet de **l’étiquette de nom** , tapez **Public interne**, puis cliquez sur **suivant**.
    
7. Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.
    
8. Dans le volet **passez en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour ces étiquettes supplémentaires :
    
  - Privé
    
  - Sensible
    
  - Hautement confidentiel
    
10. Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.
    
11. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.
    
12. Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
13. Cliquez sur **Terminé**.
    
14. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
15. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
16. Dans le volet **nom de votre stratégie** , tapez **exemple d’entreprise** dans **nom**, puis cliquez sur **suivant**.
    
17. Dans le volet **passez en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Phase 4 : Créer vos sites d’équipe SharePoint Online

Dans cette phase, vous créez et vous configurez les quatre types de sites d’équipe SharePoint Online pour votre exemple d’organisation.
  
### <a name="organization-wide-team-site"></a>Site d’équipe au niveau de l’organisation

Pour créer une base de référence de site d’équipe SharePoint Online public, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, tapez **Toute l’organisation**. 
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour toute l’organisation**.
    
7. Dans **les paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation permettre accéder à ce site**, puis cliquez sur **suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe Toute l’organisation pour l’étiquette Publique interne.
  
1. Dans l’onglet **Organisation wide-d’accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **Public interne**, puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online consultable par les membres de l’organisation.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Site d’équipe Projet 1

Pour créer un site d’équipe SharePoint Online privé de base de référence pour un projet au sein de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, tapez **Projet 1**. 
    
6. Dans la **description du site d’équipe,** tapez **le site SharePoint pour le projet 1**.
    
7. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe Projet 1 pour l’étiquette Privé.
  
1. Sous l’onglet **Projet 1 - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **privée**, puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online privé concernant Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Site d’équipe des campagnes marketing

Pour créer un site d’équipe SharePoint Online isolé de niveau sensible pour les ressources des campagnes marketing, procédez comme suit :
  
1. À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 à l’aide de votre compte d’administrateur global. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, tapez **Campagnes marketing**.
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour les ressources des campagnes marketing (sensible)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Sous l’onglet Nouveau de **campagnes Marketing** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **autorisations de Site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @**\<votre nom de l’organisation >**. onmicrosoft.com** dans **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.
    
13. Cliquez sur **Membres de Campagnes marketing** dans la liste.
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **partager** , tapez **équipe Marketing**, sélectionnez-le, puis cliquez sur **partager**.
    
16. Répétez les étapes 14 et 15 pour le compte d’utilisateur **Researcher1** .
    
17. Cliquez sur le bouton de retour de votre navigateur.
    
18. Dans la liste, cliquez sur **campagnes Marketing propriétaires** .
    
19. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
20. Dans la boîte de dialogue **partager** , tapez **personnel informatique**, sélectionnez-le, puis cliquez sur **partager**.
    
21. Cliquez sur le bouton de retour de votre navigateur.
    
22. Fermez l’onglet **personnes et groupes** dans votre navigateur, cliquez sur l’onglet **accueil-campagnes de Marketing** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Campagnes marketing - Membres** contient seulement le groupe **Campagnes marketing** (qui contient le compte d’utilisateur Administrateur global), le groupe **Équipe Marketing** (qui contient les comptes d’utilisateur Marketing1 et Marketing2) et le compte d’utilisateur **Chercheur1**.
    
- Le groupe SharePoint **Campagnes marketing - Propriétaires** contient seulement le groupe **Équipe Informatique** (qui contient seulement les comptes d’utilisateur ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Campagnes marketing - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Campagnes marketing - Propriétaires**).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.
    
Ensuite, configurez le dossier des documents du site d’équipe Campagnes marketing pour l’étiquette Sensible.
  
1. Sous l’onglet **Campagne marketing - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Sensible, qui inclut le site Campagnes marketing.
  
1. Sous l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; conformité** mosaïque.
    
2. Sur la nouvelle **sécurité &amp; conformité** dans votre navigateur, cliquez sur **prévention des pertes de données > stratégie**.
    
3. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
4. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisé**, puis cliquez sur **suivant**.
    
5. Dans le volet **nom de votre stratégie** , tapez les **sites d’équipe SharePoint Online étiquette sensibles** dans **nom**, puis cliquez sur **suivant**.
    
6. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
7. Dans la liste des emplacements, désactiver les emplacements des **comptes de OneDrive** et de **messagerie Exchange** , puis cliquez sur **suivant**.
    
8. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.
    
9. Dans le volet **Sélectionner les types de contenu pour protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.
    
10. Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **sensibles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.
    
13. Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
14. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
15. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager avec un utilisateur à l’extérieur de l’organisation, téléchargez le fichier, puis ouvrez-le. Cliquez sur Fichier, sur Protéger le document et sur Chiffrer avec mot de passe, puis spécifiez un mot de passe fort. Envoyez le mot de passe dans un e-mail distinct ou via un autre moyen de communication.
    
16. Cliquez sur **OK**.
    
17. Dans la **que voulez-vous faire si nous détecter des informations sensibles ?** volet, désactivez la case à cocher **bloquer les personnes de partager et restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.
    
18. Dans la **vous souhaitez activer les opérations de test ou de stratégie extraire au préalable ?** volet, cliquez sur **Oui, activer immédiatement**, puis cliquez sur **suivant**.
    
19. Dans le volet **passez en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Voici la configuration finale.
  
![Protection des données sensibles pour les sites d’équipe SharePoint Online isolés des campagnes marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Site d’équipe Stratégie d’entreprise

Pour créer un site d’équipe SharePoint Online isolé au niveau Hautement confidentiel pour les ressources d’entreprise stratégiques des dirigeants de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, tapez **Stratégie de l’entreprise**.
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour la stratégie de l’entreprise (Hautement confidentiel)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Sous l’onglet **stratégie de la société** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **autorisations de Site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les cases à cocher trois sont désactivées), puis cliquez sur ** OK**.
    
13. Dans la liste, cliquez sur **stratégie d’entreprise membres** .
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **partager** , tapez **C-Suite**, sélectionnez-le, puis cliquez sur **partager**.
    
16. Dans la liste, cliquez sur **stratégie d’entreprise propriétaires** .
    
17. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
18. Dans la boîte de dialogue **partager** , tapez **personnel informatique**, sélectionnez-le, puis cliquez sur **partager**.
    
19. Cliquez sur le bouton de retour de votre navigateur.
    
20. Fermez l’onglet **personnes et groupes** dans votre navigateur, cliquez sur l’onglet **Accueil stratégie de la société** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Stratégie de l’entreprise - Membres** contient seulement le groupe **C-Suite** (qui contient uniquement les comptes d’utilisateur PDG, Directeur financier et Directeur informatique) et le groupe **Stratégie de l’entreprise** (qui contient uniquement le compte d’utilisateur de l’administrateur général).
    
- Le groupe SharePoint **Propriétaires de stratégie de sociétés** contient uniquement le groupe de **personnel informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Stratégie de l’entreprise - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Stratégie de l’entreprise - Propriétaires**).
    
- Les autres comptes d’utilisateur ne peuvent ni accéder au site ou à ses ressources, ni demander l’accès au site. Des autorisations supplémentaires pour le site doivent être octroyées par l’administrateur général ou un membre du groupe **Stratégie de l’entreprise - Propriétaires**.
    
Ensuite, configurez le dossier des documents du site d’équipe Stratégie de l’entreprise pour l’étiquette Hautement confidentiel.
  
1. Sous l’onglet **Stratégie de l’entreprise - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **Hautement confidentielles**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de protection contre la perte de données qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Hautement confidentiel, qui inclut le site Stratégie de l’entreprise.
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 avec un compte qui dispose du rôle d’administrateur de sécurité ou administrateur d’entreprise. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; conformité** mosaïque.
    
3. Sur la nouvelle **sécurité &amp; conformité** dans votre navigateur, cliquez sur **prévention des pertes de données > stratégie**.
    
4. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
5. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisé**, puis cliquez sur **suivant**.
    
6. Dans le volet **nom de votre stratégie** , tapez les **sites d’équipe SharePoint Online hautement confidentielles étiquette** dans **nom**, puis cliquez sur **suivant**.
    
7. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
8. Dans la liste des emplacements, désactiver les emplacements des **comptes de OneDrive** et de **messagerie Exchange** , puis cliquez sur **suivant**.
    
9. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.
    
10. Dans le volet **Sélectionner les types de contenu pour protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.
    
11. Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.
    
12. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
13. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.
    
14. Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
15. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
16. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager avec un utilisateur à l’extérieur de l’organisation, téléchargez le fichier, puis ouvrez-le. Cliquez sur Fichier, sur Protéger le document et sur Chiffrer avec mot de passe, puis spécifiez un mot de passe fort. Envoyez le mot de passe dans un e-mail distinct ou via un autre moyen de communication.
    
17. Cliquez sur **OK**.
    
18. Dans la **que voulez-vous faire si nous détecter des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.
    
19. Dans la **vous souhaitez activer les opérations de test ou de stratégie extraire au préalable ?** volet, cliquez sur **Oui, activer immédiatement**, puis cliquez sur **suivant**.
    
20. Dans le volet **passez en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Suivez ensuite les instructions contenues dans [Comment activer Azure Rights Management à partir du centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Ensuite, configurez Azure Information Protection avec une nouvelle stratégie délimitée et une sous-étiquette pour la protection et les autorisations en suivant ces étapes :
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un onglet séparé de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
5. Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.
    
6. Tapez **CompanyStrategy** dans **Nom de la stratégie** et **Étiquette pour les documents dans le site d’équipe Stratégie d’entreprise** dans **Description**.
    
7. Cliquez sur **Sélectionner les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateurs/Groupes**, puis sélectionnez **C-Suite**.
    
8. Cliquez sur **Sélectionner > OK**.
    
9. Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.
    
10. Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.
    
11. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
12. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
13. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **DAS utilisateurs et groupes** , sélectionnez **C-Suite**, puis cliquez sur **Sélectionner**.
    
16. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.
    
17. Cliquez deux fois sur **OK**.
    
18. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Sur le serveur lame **Azure Information protection - stratégies d’étendue** , cliquez sur **Publier**, puis cliquez sur **Oui**.
    
Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client Azure la Protection des informations](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis se connecter à partir de Microsoft Word avec un compte dans le ** C-Suite** groupe de votre abonnement d’évaluation.
  
Voici la configuration finale.
  
![Protection avec un niveau de confidentialité élevé pour le site d’équipe SharePoint Online isolé de la stratégie d’entreprise.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Vous êtes maintenant prêt à créer des documents dans ces quatre sites et à tester l’accès à ceux-ci avec différents comptes d’utilisateur de votre abonnement d’essai.
  
Voici la configuration globale pour les quatre sites d’équipe SharePoint Online.
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Étape suivante

Quand vous êtes prêt à effectuer le déploiement en production de sites SharePoint Online sécurisés, consultez [Sécuriser des sites et des fichiers SharePoint Online](secure-sharepoint-online-sites-and-files.md) pour obtenir des informations détaillées et des liens vers des articles sur le déploiement étape par étape.
  
## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Solutions de sécurité](security-solutions.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




