---
title: Sécuriser des sites SharePoint Online dans un environnement de développement et de test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/17/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Résumé : Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans un environnement de développement/test.'
ms.openlocfilehash: 49153a5c4256e7aa0e5ba5f6d2ac53c4e56b5bdc
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915769"
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Sécuriser des sites SharePoint Online dans un environnement de développement et de test

 **Résumé :** Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans un environnement de développement/test.
  
Cet article fournit des instructions pas à pas pour créer un environnement de développement et de test qui inclut les quatre types différents de sites d’équipe SharePoint Online pour la solution de [sécurisation des sites et des fichiers SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](media/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Utilisez cet environnement de développement/test pour expérimenter les comportements de protection des informations et optimiser les paramètres en fonction de vos besoins avant de déployer des sites d’équipe SharePoint Online en production.
  
## <a name="phase-1-create-your-devtest-environment"></a>Phase 1 : Créer votre environnement de développement et de test

Dans cette phase, vous obtenez des abonnements d’essai pour Office 365 et Enterprise Mobility + Security pour une entreprise fictive.
  
Suivez d’abord les instructions de la **Phase 2** de l’[environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur général de votre abonnement d’essai. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la vignette **Administration**.
    
3. Sous l’onglet **Centre d’administration Office** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Enterprise Mobility + Security E5**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
Ensuite, activez la licence Enterprise Mobility + Security E5 pour votre compte d’administrateur général.
  
1. Sous l’onglet **Centre d’administration Office 365** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Cliquez sur votre compte Administrateur général, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet **Licences de produit**, activez la licence de produit pour **Enterprise Mobility + Security E5** en sélectionnant **Activer**, cliquez sur **Enregistrer**, cliquez deux fois sur **Fermer**.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2 : Création et configuration de vos groupes et utilisateurs Azure Active Directory (AD)

Dans cette phase, vous créez et vous configurez les groupes et les utilisateurs Azure AD de votre organisation fictive.
  
Commencez par créer un ensemble de groupes pour une organisation standard avec le portail Azure.
  
1. Créez un onglet distinct dans votre navigateur, puis accédez au portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous avec les informations d’identification du compte Administrateur général de votre abonnement d’essai Office 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Groupes**.
    
3. Dans le panneau **Groupes - Tous les groupes**, cliquez sur **+ Nouveau groupe**.
    
4. Dans le panneau **Groupe** :
    
  - Sélectionnez **Office 365** dans **Type de groupe**.
    
  - Tapez **C-Suite** dans le champ **Nom**.
    
  - Sélectionnez **Affecté** dans le champ **Type d’appartenance**.
      
5. Cliquez sur **Créer** et fermez le panneau **Groupe**.
    
6. Répétez les étapes 3 à 5 pour les noms de groupe suivants :
    
  - Équipe Informatique
    
  - Équipe Recherche
    
  - Équipe Standard
    
  - Équipe Marketing
    
  - Équipe Ventes
    
7. Gardez l’onglet du portail Azure ouvert dans votre navigateur.
    
Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > Licences > Tous les produits**.
    
2. Dans la liste, sélectionnez **Enterprise Mobility + Security E5** et **Office 365 Entreprise E5**, puis cliquez sur **Affecter**.
    
3. Dans le panneau **Affecter une licence**, cliquez sur **Utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - C-Suite
    
  - Équipe Informatique
    
  - Équipe Recherche
    
  - Équipe Standard
    
  - Équipe Marketing
    
  - Équipe de vente
    
5. Cliquez sur **Sélectionner**, puis sur **Affecter**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
Ensuite, vous vous [connectez au module PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Renseignez le nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou de l’environnement de script intégré (ISE) pour créer des comptes d’utilisateur et les ajouter à leurs groupes :
  
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

Dans cette phase, vous allez créer les étiquettes correspondant aux différents niveaux de sécurité pour les dossiers de documents du site d’équipe SharePoint Online.
  
1. Si nécessaire, utilisez une instance privée de votre navigateur Internet et connectez-vous au portail Office 365 avec le compte d’administrateur général de votre abonnement d’essai Office 365 E5. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.
    
3. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration > Sécurité &amp; conformité**.
    
4. Sous le nouvel onglet **Accueil - Sécurité &amp; conformité de votre navigateur**, cliquez sur **Classifications > Étiquettes**.
    
5. Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.
    
6. Dans le volet **Nom de l’étiquette**, saisissez **Interne public** et cliquez sur **Suivant**.
    
7. Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.
    
8. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :
    
  - Privé
    
  - Sensible
    
  - Hautement confidentiel
    
10. Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.
    
11. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.
    
12. Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
13. Cliquez sur **Terminé**.
    
14. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
15. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
16. Dans le volet **Nom de votre stratégie**, saisissez **Exemple d’organisation** sous **Nom**, puis cliquez sur **Suivant**.
    
17. Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis sur **Fermer**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Phase 4 : Création de vos sites d’équipe SharePoint Online

Dans cette phase, vous créez et vous configurez les quatre types de sites d’équipe SharePoint Online pour votre exemple d’organisation.
  
### <a name="organization-wide-team-site"></a>Site d’équipe au niveau de l’organisation

Pour créer une base de référence de site d’équipe SharePoint Online public, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, tapez **Toute l’organisation**. 
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour toute l’organisation**.
    
7. Dans **Paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe Toute l’organisation pour l’étiquette Publique interne.
  
1. Sous l’onglet **Toute l’organisation - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer une étiquette**, sélectionnez **Interne public**, puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online consultable par les membres de l’organisation.](media/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Site d’équipe Projet 1

Pour créer un site d’équipe SharePoint Online privé de base de référence pour un projet au sein de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, tapez **Projet 1**. 
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour Projet 1**.
    
7. Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe Projet 1 pour l’étiquette Privé.
  
1. Sous l’onglet **Projet 1 - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Privé**, puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online privé concernant Project1.](media/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Site d’équipe des campagnes marketing

Pour créer un site d’équipe SharePoint Online isolé de niveau sensible pour les ressources des campagnes marketing, procédez comme suit :
  
1. En utilisant un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 avec votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, tapez **Campagnes marketing**.
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour les ressources des campagnes marketing (sensible)**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Dans le nouvel onglet **Campagnes marketing** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site, ainsi que des fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site**, saisissez **ITAdmin1@**\<nom de votre organisation>**.onmicrosoft.com** dans le champ **Envoyer toutes les demandes d’accès à**, puis cliquez sur **OK**.
    
13. Cliquez sur **Membres de Campagnes marketing** dans la liste.
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **Partager**, saisissez **Personnel marketing**, sélectionnez-le, puis cliquez sur **Partager**.
    
16. Répétez les étapes 14 et 15 pour le compte utilisateur **Researcher1**.
    
17. Cliquez sur le bouton de retour de votre navigateur.
    
18. Cliquez sur **Propriétaires de campagnes marketing** dans la liste.
    
19. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
20. Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.
    
21. Cliquez sur le bouton de retour de votre navigateur.
    
22. Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Campagnes marketing - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Campagnes marketing - Membres** contient seulement le groupe **Campagnes marketing** (qui contient le compte d’utilisateur Administrateur global), le groupe **Équipe Marketing** (qui contient les comptes d’utilisateur Marketing1 et Marketing2) et le compte d’utilisateur **Chercheur1**.
    
- Le groupe SharePoint **Campagnes marketing - Propriétaires** contient seulement le groupe **Équipe Informatique** (qui contient seulement les comptes d’utilisateur ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Campagnes marketing - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Campagnes marketing - Propriétaires**).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.
    
Ensuite, configurez le dossier de documents du site d’équipe Campagnes marketing pour l’étiquette Sensible.
  
1. Sous l’onglet **Campagne marketing - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Sensible**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Sensible, qui inclut le site Campagnes marketing.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.
    
2. Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.
    
3. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
4. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
5. Dans le volet **Nom de votre stratégie**, saisissez les **sites d’équipe SharePoint Online avec étiquette Sensible** sous **Nom**, puis cliquez sur **Suivant**.
    
6. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **Messagerie Exchange** et **Comptes OneDrive**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.
    
9. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **Étiquettes**.
    
10. Dans le volet **Étiquettes**, cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Sensible**, cliquez sur **Ajouter**, puis sur **Terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.
    
13. Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
14. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
15. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
16. Cliquez sur **OK**.
    
17. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, désélectionnez la case **Empêcher les utilisateurs de partager un fichier et restreindre l’accès au contenu partagé**, puis cliquez sur **Suivant**.
    
18. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.
    
Voici la configuration finale.
  
![Protection des données sensibles pour les sites d’équipe SharePoint Online isolés des campagnes marketing.](media/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Site d’équipe Stratégie d’entreprise

Pour créer un site d’équipe SharePoint Online isolé au niveau Hautement confidentiel pour les ressources d’entreprise stratégiques des dirigeants de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, tapez **Stratégie de l’entreprise**.
    
6. Dans **Description du site d’équipe**, tapez **Site SharePoint pour la stratégie de l’entreprise (Hautement confidentiel)**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Dans le nouvel onglet **Stratégie d’entreprise** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site** (afin que les trois cases à cocher soient désactivées), puis cliquez sur **OK**.
    
13. Cliquez sur les **Membres de l’équipe Stratégie d’entreprise** dans la liste.
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **Partager**, saisissez **C-Suite**, sélectionnez-le, puis cliquez sur **Partager**.
    
16. Cliquez sur les **Propriétaires de la stratégie d’entreprise** dans la liste.
    
17. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
18. Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.
    
19. Cliquez sur le bouton de retour de votre navigateur.
    
20. Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Stratégie d’entreprise - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Stratégie de l’entreprise - Membres** contient seulement le groupe **C-Suite** (qui contient uniquement les comptes d’utilisateur PDG, Directeur financier et Directeur informatique) et le groupe **Stratégie de l’entreprise** (qui contient uniquement le compte d’utilisateur de l’administrateur général).
    
- Le groupe SharePoint **Stratégie de l’entreprise - Propriétaires** contient seulement le groupe **Équipe Informatique** (qui contient seulement les comptes d’utilisateur ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Stratégie de l’entreprise - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Stratégie de l’entreprise - Propriétaires**).
    
- Les autres comptes d’utilisateur ne peuvent ni accéder au site ou à ses ressources, ni demander l’accès au site. Des autorisations supplémentaires pour le site doivent être octroyées par l’administrateur général ou un membre du groupe **Stratégie de l’entreprise - Propriétaires**.
    
Ensuite, configurez le dossier de documents du site d’équipe Stratégie d’entreprise pour l’étiquette Hautement confidentiel.
  
1. Sous l’onglet **Stratégie de l’entreprise - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer une étiquette**, sélectionnez **Hautement confidentiel**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de protection contre la perte de données qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Hautement confidentiel, qui inclut le site Stratégie de l’entreprise.
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur de la société. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.
    
3. Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.
    
4. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
5. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
6. Dans le volet **Nom de votre stratégie**, saisissez les **sites d’équipe SharePoint Online avec étiquette Hautement confidentiel** sous **Nom**, puis cliquez sur **Suivant**.
    
7. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
8. Dans la liste des emplacements, désactivez les emplacements **Messagerie Exchange** et **Comptes OneDrive**, puis cliquez sur **Suivant**.
    
9. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.
    
10. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **Étiquettes**.
    
11. Dans le volet **Étiquettes**, cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentiel**, cliquez sur **Ajouter**, puis sur **Terminé**.
    
12. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
13. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.
    
14. Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
15. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
16. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
17. Cliquez sur **OK**.
    
18. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, sélectionnez **Exiger une justification professionnelle pour le remplacement**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
20. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.
    
Suivez ensuite les instructions contenues dans [Comment activer Azure Rights Management à partir du centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Ensuite, configurez Azure Information Protection avec une nouvelle stratégie et une sous-étiquette délimitée pour le groupe C-Suite pour la protection et les autorisations en suivant ces étapes :
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Tous les services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.

5. Cliquez sur **Étiquettes**.
    
6. Cliquez avec le bouton droit de la souris sur l’étiquette **Hautement confidentiel**, puis sur **Ajouter une sous-étiquette**.
    
7. Saisissez **Membres C-Suite** dans **Nom** et **Description**.
    
8. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
9. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
10. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
11. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
12. Dans le volet **Utilisateurs et groupes AAD**, sélectionnez **C-Suite**, puis cliquez sur **Sélectionner**.
    
13. Sous **Choisir les autorisations parmi les autorisations personnalisées prédéfinies ou définies**, cliquez sur **Personnalisé**, puis sur les cases à cocher **Afficher les droits**, **Modifier le contenu**, **Enregistrer**, **Répondre**, et **Répondre à tous**.
    
14. Cliquez deux fois sur **OK**.
    
15. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**, puis sur **OK**.

16. Dans le panneau **Azure Information Protection**, cliquez sur **Stratégies > + Ajouter une nouvelle stratégie**.
    
17. Tapez **CompanyStrategy** dans **Nom de la stratégie** et **Étiquette pour les documents dans le site d’équipe Stratégie d’entreprise** dans **Description**.
    
18. Cliquez sur**Sélectionner les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateurs/Groupes**, puis sélectionnez **C-Suite**.
    
19. Cliquez sur **Sélectionner > OK**.

20. Cliquez sur **Ajouter ou supprimer des étiquettes**. Dans le volet **Stratégie : Ajouter ou supprimer des étiquettes**, cliquez sur **C-Suite**, puis sur **OK**.   

21. Cliquez sur **Enregistrer**, puis sur **OK**.
    
Pour protéger un document avec Azure Information Protection et cette nouvelle étiquette, vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur une machine de test, installer Office à partir du portail Office 365, puis vous connecter à partir de Microsoft Word avec un compte du groupe **C-Suite** de votre abonnement d’essai.
  
Voici la configuration finale.
  
![Protection avec un niveau de confidentialité élevé pour le site d’équipe SharePoint Online isolé de la stratégie d’entreprise.](media/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Vous êtes maintenant prêt à créer des documents dans ces quatre sites et à tester l’accès à ceux-ci avec différents comptes d’utilisateur de votre abonnement d’essai.
  
Voici la configuration globale pour les quatre sites d’équipe SharePoint Online.
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](media/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Étape suivante

Quand vous êtes prêt à effectuer le déploiement en production de sites SharePoint Online sécurisés, consultez [Sécuriser des sites et des fichiers SharePoint Online](secure-sharepoint-online-sites-and-files.md) pour obtenir des informations détaillées et des liens vers des articles sur le déploiement étape par étape.
  
## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Solutions de sécurité](security-solutions.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




