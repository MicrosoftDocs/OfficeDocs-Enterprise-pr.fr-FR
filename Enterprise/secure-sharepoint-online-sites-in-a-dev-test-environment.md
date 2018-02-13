---
title: "Sécuriser les sites SharePoint Online dans un environnement de développement/test"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Résumé : Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans un environnement de développement/test."
ms.openlocfilehash: a0448cdbce570db748f8fcae784fd6f1beefc218
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Sécuriser les sites SharePoint Online dans un environnement de développement/test

 **Résumé :** Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans un environnement de développement/test.
  
Cet article fournit des instructions pas à pas pour créer un environnement de développement/test qui inclut les quatre types différents de sites d’équipe SharePoint Online pour la solution de [fichiers et des sites SharePoint Online de la sécuriser](secure-sharepoint-online-sites-and-files.md) .
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Cet environnement de développement/test permet de faire des essais avec les comportements de protection des informations et d’affiner les paramètres pour vos besoins avant de déployer des sites d’équipe SharePoint Online dans la production.
  
## <a name="phase-1-create-your-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test

Dans cette phase, vous obtenez des abonnements d’essai d’Office 365 et de mobilité d’entreprise + de sécurité pour une entreprise fictive.
  
Tout d’abord, suivez les instructions de la **Phase 2** de l' [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
Activez ensuite la licence Enterprise Mobility + Security E5 pour votre compte d’administrateur général.
  
1. Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.
    
2. Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2 : Créer et configurer des groupes d’Azure Active Directory (AD) et des utilisateurs

Dans cette phase, vous créez et configurez les groupes d’annonces Azure et les utilisateurs de votre organisation fictive.
  
Tout d’abord, créez un ensemble de groupes pour une organisation typique avec le portail Azure.
  
1. Créer un onglet distinct dans votre navigateur et passez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous en utilisant les informations d’identification du compte d’administrateur global pour votre abonnement d’évaluation d’Office 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > utilisateurs et groupes > tous les groupes de**.
    
3. Sur la lame de **tous les groupes** , cliquez sur **+ le nouveau groupe**.
    
4. Sur la lame de **groupe** :
    
  - Type **C-Suite** dans la zone **nom**.
    
  - Sélectionnez **affecté** dans **l’appartenance**.
    
  - Cliquez sur **Oui** pour **activer Office fonctionnalités**.
    
5. Cliquez sur **créer**, puis fermez la lame du **groupe** .
    
6. Répétez les étapes 3 à 5 pour les noms de groupe suivants :
    
  - IT staff
    
  - Personnel de recherche
    
  - Personnel normal
    
  - Équipe marketing
    
  - Équipe de vente
    
7. Conserver l’onglet portail Azure dans ouvert de votre navigateur.
    
Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > licences > tous les produits**.
    
2. Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**et puis cliquez sur **attribuer**.
    
3. De la lame **attribuer la licence** , cliquez sur **utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - C-Suite
    
  - IT staff
    
  - Personnel de recherche
    
  - Personnel normal
    
  - Équipe marketing
    
  - Équipe de vente
    
5. Cliquez sur **Sélectionner**, puis cliquez sur **attribuer**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
Ensuite, vous [connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Renseignez le nom de votre organisation, votre emplacement et un mot de passe commun et puis exécuter ces commandes à partir de l’invite de commande PowerShell ou l’environnement de Script intégré (ISE) pour créer des comptes d’utilisateurs et de les ajouter à leurs groupes :
  
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
  
1. À partir de l’onglet **Accueil de Microsoft Office** de votre navigateur, cliquez sur la mosaïque de **l’Admin** .
    
2. À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **utilisateurs**.
    
3. Dans la liste des utilisateurs, cliquez sur **PDG**.
    
4. Dans le volet qui répertorie les propriétés du compte d’utilisateur **PDG** , vérifiez qu’il a été attribué les licences de **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5** (dans les **licences de produit**).
    
## <a name="phase-3-create-office-365-labels"></a>Phase 3 : Créer des étiquettes d’Office 365

Dans cette phase, vous allez créer les étiquettes correspondant aux différents niveaux de sécurité pour les dossiers de documents du site d’équipe SharePoint Online.
  
1. Si nécessaire, utilisez une instance privée de votre navigateur Internet et vous connecter au portail Office 365 avec le compte d’administrateur global de votre abonnement d’évaluation d’Office 365 E5. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **Centre d’administration > sécurité &amp; la conformité**.
    
4. À partir du nouveau **maison - sécurité &amp; la conformité** onglet de votre navigateur, cliquez sur **les Classifications > étiquettes**.
    
5. À partir de le **Accueil > étiquettes** volet, cliquez sur **créer une étiquette**.
    
6. Dans le volet **nom de votre étiquette** , tapez **Public interne**et puis cliquez sur **suivant**.
    
7. Dans le volet **paramètres d’étiquette** , cliquez sur **suivant**.
    
8. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :
    
  - Privé
    
  - Sensible
    
  - Hautement confidentiel
    
10. À partir de le **Accueil > étiquettes** volet, cliquez sur **publier les étiquettes**.
    
11. Dans le volet **Choisir les étiquettes à publier** , cliquez sur **Choisir les étiquettes à publier**.
    
12. Dans le volet **Choisir étiquettes** , cliquez sur **Ajouter** et sélectionner toutes les étiquettes de quatre.
    
13. Cliquez sur **terminé**.
    
14. Dans le volet **Choisir les étiquettes à publier** , cliquez sur **suivant**.
    
15. Dans le volet **Choisir des emplacements** , cliquez sur **suivant**.
    
16. Dans le volet **nom de votre stratégie** , tapez **exemple d’entreprise** dans la zone **nom**, puis cliquez sur **suivant**.
    
17. Dans le volet de **passer en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Phase 4 : Créez vos sites d’équipe SharePoint Online

Dans cette phase, vous créez et configurez les quatre types de sites d’équipe SharePoint Online pour votre exemple d’entreprise.
  
### <a name="organization-wide-team-site"></a>Site d’équipe à l’échelle de l’organisation

Pour créer un site d’équipe SharePoint Online public de référence, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du Site**, tapez **l’échelle de l’organisation**. 
    
6. Dans **description de site d’équipe**, tapez le **site SharePoint pour toute l’organisation**.
    
7. Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier documents du site d’équipe grande organisation pour l’étiquette publics internes.
  
1. Dans l’onglet de **L’échelle de l’entreprise - accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Public interne**et puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online consultable par les membres de l’organisation.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Site d’équipe 1 du projet

Pour créer un site d’équipe SharePoint Online privé de référence pour un projet au sein de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du Site**, tapez **1 du projet**. 
    
6. Dans la **description de site d’équipe,** tapez le **site SharePoint pour le projet 1**.
    
7. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier de documents du site d’équipe Projet 1 pour l’étiquette Privé.
  
1. Dans l’onglet **projet 1-accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres à appliquer une étiquette**, sélectionnez **privé**, puis cliquez sur **Enregistrer**.
    
Voici la configuration finale.
  
![Protection de base pour le site d’équipe SharePoint Online privé concernant Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Site d’équipe des campagnes marketing

Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources de campagne marketing, procédez comme suit :
  
1. À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du site d’équipe**, tapez **les campagnes Marketing**.
    
6. Dans la **description de site d’équipe**, tapez le **site SharePoint pour les ressources de campagne marketing (la casse)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
9. Dans l’onglet **campagnes de Marketing** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
10. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
11. Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @**\<votre nom de l’organisation >**. onmicrosoft.com** dans la zone **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.
    
13. Dans la liste, cliquez sur **campagnes de Marketing les membres** .
    
14. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue de **partage** , tapez **équipe Marketing**, sélectionnez-le, puis cliquez sur **partage**.
    
16. Répétez les étapes 14 et 15 pour le compte d’utilisateur **Researcher1** .
    
17. Cliquez sur le bouton de retour de votre navigateur.
    
18. Dans la liste, cliquez sur **campagnes de Marketing propriétaires** .
    
19. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
20. Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.
    
21. Cliquez sur le bouton de retour de votre navigateur.
    
22. Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **accueil-campagnes de Marketing** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint des **Membres de campagnes Marketing** contient uniquement le groupe de **campagnes de Marketing** (qui contient le compte d’utilisateur administrateur global), le groupe de **l’équipe Marketing** (qui contient l’utilisateur Marketing1 et Marketing2 comptes) et le compte d’utilisateur **Researcher1** .
    
- Le groupe de **Propriétaires de campagnes de Marketing** SharePoint contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe de **Campagnes de Marketing - les visiteurs** SharePoint ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de campagnes de Marketing** ).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.
    
Ensuite, configurez le dossier de documents du site d’équipe Campagnes marketing pour l’étiquette Sensible.
  
1. Dans l’onglet **accueil-campagnes de commercialisation** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres à appliquer une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de prévention des pertes de données qui avertit les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette Sensible, dont notamment le site Campagnes marketing, à l’extérieur de l’organisation.
  
1. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
2. Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.
    
3. Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.
    
4. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.
    
5. Dans le volet **nom de votre stratégie** , tapez des **sites d’équipe SharePoint Online étiquette sensibles** dans la zone **nom**, puis cliquez sur **suivant**.
    
6. Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.
    
8. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.
    
9. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.
    
10. Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **sensibles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.
    
13. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
14. Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.
    
15. Dans la zone de texte, tapez ou collez le texte suivant :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
16. Cliquez sur **OK**.
    
17. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, désactivez la case à cocher **bloquer le partage, des personnes et de restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.
    
18. Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.
    
19. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Voici la configuration finale.
  
![Protection des données sensibles pour les sites d’équipe SharePoint Online isolés des campagnes marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Site d’équipe de stratégie d’entreprise

Pour créer un site d’équipe SharePoint Online isolé au niveau hautement confidentiel pour les ressources stratégiques de l’entreprise des cadres dirigeants de l’organisation, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du site d’équipe**, tapez **stratégie de la société**.
    
6. Dans la **description de site d’équipe**, tapez le **site SharePoint pour la stratégie d’entreprise (hautement confidentielle)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
9. Dans l’onglet **stratégie de la société** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
10. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
11. Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur ** OK**.
    
13. Dans la liste, cliquez sur **stratégie membres de la société** .
    
14. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue de **partage** , tapez **C-Suite**, sélectionnez-le, puis cliquez sur **partage**.
    
16. Dans la liste, cliquez sur **stratégie d’entreprise propriétaires** .
    
17. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
18. Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.
    
19. Cliquez sur le bouton de retour de votre navigateur.
    
20. Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet de **Stratégie d’entreprise - accueil** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Membres de stratégie d’entreprise** contient uniquement le groupe **C-Suite** (qui contienne uniquement les comptes d’utilisateurs PDG, directeur financier et directeur de l’information) et le groupe de la **stratégie de la société** (qui contient uniquement le compte d’utilisateur administrateur global).
    
- Le groupe SharePoint **Propriétaires de stratégie de société** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Visiteurs-stratégie de société** ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de stratégie de société** ).
    
- Autres comptes d’utilisateur ne peut pas accéder au site ou ses ressources ou demander l’accès au site. Des autorisations supplémentaires sur le site doivent être effectuées par l’administrateur global ou par un membre du groupe **Stratégie-propriétaires de sociétés** .
    
Ensuite, configurez le dossier de documents du site d’équipe Stratégie d’entreprise pour l’étiquette Hautement confidentiel.
  
1. Dans l’onglet **Stratégie d’entreprise - accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Hautement confidentielles**et puis cliquez sur **Enregistrer**.
    
Configurez ensuite une stratégie DLP qui empêche les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette hautement confidentielles, ce qui inclut le site de stratégie d’entreprise, à l’extérieur de l’organisation.
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
3. Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.
    
4. Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.
    
5. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.
    
6. Dans le volet **nom de votre stratégie** , tapez **hautement confidentielles sites d’équipe SharePoint Online étiquette** dans la zone **nom**, puis cliquez sur **suivant**.
    
7. Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.
    
8. Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.
    
9. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.
    
10. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.
    
11. Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.
    
12. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.
    
13. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.
    
14. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
15. Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.
    
16. Dans la zone de texte, tapez ou collez le texte suivant :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
17. Cliquez sur **OK**.
    
18. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.
    
19. Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.
    
20. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Ensuite, suivez les instructions de [RMS d’Azure activer avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Ensuite, configurez la Protection des informations Azure avec une nouvelle stratégie étendue et une étiquette secondaire pour la protection et d’autorisations avec les étapes suivantes :
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
5. Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.
    
6. Dans **nom de la stratégie** et l' **étiquette pour les documents dans le site d’équipe stratégie société** dans la zone **Description**, tapez **CompanyStrategy** .
    
7. Cliquez sur **Sélectionner les utilisateurs ou les groupes d’obtiennent cette stratégie > groupes d’utilisateurs**, puis sélectionnez la **Suite de la C**.
    
8. Cliquez sur **Sélectionner > OK**.
    
9. Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.
    
10. Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.
    
11. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
12. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
13. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **DAS utilisateurs et des groupes** , sélectionnez **C-Suite**, puis cliquez sur **Sélectionner**.
    
16. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.
    
17. Cliquez deux fois sur **OK**.
    
18. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Sur la lame de **protection des informations de Azure - stratégies étendues** , cliquez sur **Publier**, puis cliquez sur **Oui**.
    
Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis vous connecter à partir de Microsoft Word avec un compte dans le ** C-Suite** groupe de votre abonnement d’évaluation.
  
Voici la configuration finale.
  
![Protection avec un niveau de confidentialité élevé pour le site d’équipe SharePoint Online isolé de la stratégie d’entreprise.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Vous êtes maintenant prêt à créer des documents dans ces quatre sites et tester l’accès pour les différents comptes d’utilisateur dans votre abonnement d’évaluation.
  
Voici la configuration globale pour tous les sites d’équipe SharePoint Online quatre.
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt pour le déploiement de production des sites SharePoint en ligne sécurisés, voir les [fichiers et les sites SharePoint sécurisé en ligne](secure-sharepoint-online-sites-and-files.md) pour obtenir des informations détaillées et des liens vers des articles de déploiement étape par étape.
  
## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Solutions de sécurité](security-solutions.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




