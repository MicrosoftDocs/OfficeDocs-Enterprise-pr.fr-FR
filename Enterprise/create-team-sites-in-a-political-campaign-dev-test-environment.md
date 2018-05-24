---
title: Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale
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
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Résumé : Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans votre environnement de développement/test dans le cadre d’une campagne électorale.'
ms.openlocfilehash: 146632ede567be4bf412304960605e6d87de7657
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale

 **Résumé :** Créez des sites d’équipe SharePoint Online publics, privés, sensibles et hautement confidentiels dans votre environnement de développement/test dans le cadre d’une campagne électorale. 
  
Utilisez les instructions fournies dans cet article pour créer un environnement de développement/test qui inclut les quatre différents types de sites d’équipe SharePoint Online pour la solution des [conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et autres organisations souples](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md). Ces sites sont décrits en détail dans la Rubrique 10 intitulée **SharePoint et OneDrive Entreprise**.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test dans le cadre d’une campagne électorale

Tout d’abord, suivez les instructions de [Configurer de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne électorale](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) pour créer vos abonnements, utilisateurs et groupes.
  
## <a name="phase-2-create-office-365-labels"></a>Phase 2 : Création d’étiquettes Office 365

Dans cette phase, vous allez créer les étiquettes correspondant aux différents niveaux de sécurité pour les dossiers de document du site d’équipe SharePoint Online.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur général de votre abonnement d’essai. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.
    
3. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration > Sécurité &amp; conformité**.
    
4. Sous le nouvel onglet **Accueil - Sécurité &amp; conformité** de votre navigateur, cliquez sur **Classifications > Étiquettes**.
    
5. Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.
    
6. Dans le volet **Nom de l’étiquette**, saisissez **Interne** et cliquez sur **Suivant**.
    
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
    
16. Dans le volet **Nom de votre stratégie**, saisissez **Campagne** dans **Nom**, puis cliquez sur **Suivant**.
    
17. Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis cliquez sur **Fermer**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Phase 3 : Créer vos sites d’équipe SharePoint Online

Lors de cette phase, vous allez créer et configurer des sites d’équipe SharePoint Online pour votre campagne électorale correspondant aux quatre types de sites d’équipe SharePoint Online.
  
### <a name="campaign-wide-team-site"></a>Site d’équipe de la campagne

Pour créer une base de référence de site d’équipe SharePoint Online public, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, saisissez **Campagne**. 
    
6. Dans **Description du site d’équipe**, saisissez **Site SharePoint pour l’ensemble de la campagne**.
    
7. Dans **Paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier de documents du site d’équipe de la campagne pour l’étiquette Interne.
  
1. Dans l’onglet **Campagne - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Interne**, puis cliquez sur **Enregistrer**.
    
### <a name="campaign-project-1-team-site"></a>Site d’équipe 1 du projet Campagne

Pour créer un site d’équipe SharePoint Online privé de référence pour un projet dans la campagne, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site**, saisissez **Projet de campagne 1**. 
    
6. Dans **Description du site d’équipe**, saisissez **Site SharePoint pour le projet de campagne 1**.
    
7. Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier de documents du site d’équipe Projet Campagne 1 pour l’étiquette Privé.
  
1. Dans l’onglet **Projet Campagne 1 - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Privé**, puis cliquez sur **Enregistrer**.
    
### <a name="campaign-marketing-team-site"></a>Site d’équipe marketing de campagne

Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources marketing de la campagne, procédez comme suit :
  
1. En utilisant un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec votre compte d’administrateur général.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, saisissez **Ressources marketing de la campagne**.
    
6. Dans **Description du site d’équipe**, saisissez **Site SharePoint pour les ressources marketing de la campagne (données sensibles)**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Dans le nouvel onglet **Marketing campagne** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site, ainsi que des fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site**, saisissez **ITAdmin1@**<your organization name> **.onmicrosoft.com** dans le champ **Envoyer toutes les demandes d’accès à**, puis cliquez sur **OK**.
    
13. Cliquez sur les **membres de l’équipe marketing de la campagne** dans la liste.
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **Partager**, saisissez **Personnel senior et stratégique**, sélectionnez-le, puis cliquez sur **Partager**.
    
16. Répétez les étapes 14 et 15 pour le groupe **Analytics staff** et le compte d’utilisateur **Standard1**.
    
17. Cliquez sur le bouton de retour de votre navigateur.
    
18. Cliquez sur **Marketing campagne - Propriétaires** dans la liste.
    
19. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
20. Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.
    
21. Cliquez sur le bouton de retour de votre navigateur.
    
22. Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Marketing campagne - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Marketing campagne - Membres** contient uniquement le groupe **Senior and strategic staff** (qui contient les comptes d’utilisateurs Candidate, ChiefOfStaff et Strategic1), le groupe **Marketing campagne ** (qui contient le compte d’administrateur général), le groupe **Analytics staff** (qui contient le compte d’utilisateur DataScientist1) et le compte d’utilisateur **Regular1**.
    
- Le groupe SharePoint **Marketing campagne - Propriétaires** contient uniquement le groupe **Équipe informatique** (qui contient uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Marketing campagne - Visiteurs** ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe **Marketing campagne - Propriétaires**).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.
    
Ensuite, configurez le dossier de documents du site d’équipe Marketing campagne pour l’étiquette Sensible.
  
1. Dans l’onglet **Marketing campagne - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Sensible**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette Sensible à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources du site Marketing campagne.
  
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
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis cliquez sur **Fermer**.
    
### <a name="campaign-strategy-team-site"></a>Site d’équipe Stratégie de campagne

Pour créer un site d’équipe SharePoint Online isolé hautement confidentiel pour les ressources de stratégie de campagne, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) en utilisant votre compte d’administrateur général.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **Nom du site d’équipe**, saisissez **Stratégie de campagne**.
    
6. Dans **Description du site d’équipe** saisissez **Site SharePoint pour la stratégie de campagne (hautement confidentiel)**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
9. Dans le nouvel onglet **Stratégie de campagne** de votre navigateur, cliquez sur l’icône des paramètres dans la barre d’outils, puis sur **Autorisations du site**.
    
10. Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.
    
11. Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès**, désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes sur le groupe de membres du site** (afin que les trois cases à cocher soient désactivées), puis cliquez sur **OK**.
    
13. Cliquez sur les **membres de l’équipe Stratégie de campagne** dans la liste.
    
14. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue **Partager**, saisissez **Personnel senior et stratégique**, sélectionnez-le, puis cliquez sur **Partager**.
    
16. Cliquez sur les **propriétaires de la stratégie de campagne** dans la liste.
    
17. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
18. Dans la boîte de dialogue **Partager**, saisissez **Équipe informatique**, sélectionnez-la, puis cliquez sur **Partager**.
    
19. Cliquez sur le bouton de retour de votre navigateur.
    
20. Fermez l’onglet **Personnes et groupes** de votre navigateur, cliquez sur l’onglet **Stratégie de campagne - Accueil** de votre navigateur, puis fermez le volet **Autorisations du site**.
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint **Stratégie de campagne - Membres** contient uniquement le groupe **Senior and strategic staff** (qui contient uniquement les comptes d’utilisateurs Candidate, ChiefOfStaff et Strategic1) et le groupe **Stratégie de campagne** (qui contient uniquement le compte d’administrateur général).

    
- Le groupe SharePoint **Stratégie de campagne - Propriétaires** contient uniquement le groupe **Équipe informatique** (qui contient uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Stratégie de campagne - Visiteurs** ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cette opération peut être uniquement effectuée par les membres du groupe **Stratégie de campagne - Propriétaires**).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, ni demander l’accès au site. Les autorisations supplémentaires doivent être accordées par l’administrateur général ou par un membre du groupe **Stratégie de campagne - Propriétaires**.
    
Ensuite, configurez le dossier de documents du site d’équipe Stratégie de campagne pour l’étiquette Hautement confidentiel.
  
1. Dans l’onglet **Stratégie de campagne - Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Paramètres - Appliquer une étiquette**, sélectionnez **Hautement confidentiel**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie DLP qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Hautement confidentiel. Cette stratégie DLP s’applique aux ressources du site Stratégie de campagne.
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec un compte disposant du rôle Administrateur de sécurité ou Administrateur de la société.
    
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
    
20. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis cliquez sur **Fermer**.
    
Suivez les instructions contenues dans [Comment activer Azure Rights Management à partir du centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Ensuite, configurez Azure Information Protection avec une nouvelle stratégie délimitée et une sous-étiquette pour la protection et les autorisations en suivant ces étapes :
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
5. Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.
    
6. Tapez **CampaignStrategy** dans **Nom de la stratégie** et **Étiquette pour les documents dans le site d’équipe Stratégie de campagne** dans **Description**.
    
7. Cliquez sur **Sélectionner les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateurs/Groupes**, puis sélectionnez **Personnel senior et stratégique**.
    
8. Cliquez sur **Sélectionner > OK**.
    
9. Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.
    
10. Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.
    
11. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
12. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
13. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **Utilisateurs et groupes AAD**, sélectionnez **Personnel senior et stratégique**, puis cliquez sur **Sélectionner**.
    
16. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.
    
17. Cliquez deux fois sur **OK**.
    
18. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Dans le panneau **Azure Information Protection – Stratégies délimitées**, cliquez sur **Publier** et sur **Oui**.
    
Vous êtes désormais prêt à créer des documents dans ces quatre sites et à tester l’accès à ces sites avec divers comptes d’utilisateurs disponibles avec votre abonnement à la version d’évaluation. 
  
Pour protéger un document avec Azure Information Protection et cette nouvelle étiquette, vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur une machine de test, installer Office à partir du portail Office 365, puis vous connecter à partir de Microsoft Word avec un compte du groupe **Personnel senior et stratégique** de votre abonnement d’essai.
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne électorale](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




