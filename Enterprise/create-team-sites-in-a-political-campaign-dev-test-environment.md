---
title: "Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale"
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
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Résumé : Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans votre environnement de développement/test de campagne politique."
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Création de sites d’équipe dans un environnement de développement/test dans le cadre d’une campagne électorale

 **Résumé :** Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans votre environnement de développement/test de campagne politique. 
  
Suivez les instructions de cet article pour créer un environnement de développement/test qui inclut les quatre types différents de sites d’équipe SharePoint Online pour connaître les [Conseils Microsoft sur la sécurité pour les campagnes politiques, les organismes sans but lucratif et les autres organisations Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. Ces sites sont décrites en détail dans la rubrique 10, intitulé **SharePoint et OneDrive pour les entreprises**.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test dans le cadre d’une campagne électorale

Tout d’abord, suivez les instructions de [configurer les groupes et les utilisateurs d’un environnement de développement/test de campagne politique](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) pour créer des abonnements, des utilisateurs et des groupes.
  
## <a name="phase-2-create-office-365-labels"></a>Phase 2 : Création d’étiquettes Office 365

Dans cette phase, vous créez les étiquettes pour les différents niveaux de sécurité pour les dossiers du document site d’équipe SharePoint Online.
  
1. Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **Centre d’administration > sécurité &amp; la conformité**.
    
4. À partir du nouveau **maison - sécurité &amp; la conformité** onglet de votre navigateur, cliquez sur **les Classifications > étiquettes**.
    
5. À partir de le **Accueil > étiquettes** volet, cliquez sur **créer une étiquette**.
    
6. Dans le volet **nom de votre étiquette** , type **interne**, puis cliquez sur **suivant**.
    
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
    
16. Dans le volet **nom de votre stratégie** , type de **campagne** dans la zone **nom**, puis cliquez sur **suivant**.
    
17. Dans le volet de **passer en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Phase 3 : Créer vos sites d’équipe SharePoint Online

Lors de cette phase, vous allez créer et configurer des sites d’équipe SharePoint Online pour votre campagne électorale correspondant aux quatre types de sites d’équipe SharePoint Online.
  
### <a name="campaign-wide-team-site"></a>Site d’équipe de la campagne

Pour créer un site d’équipe SharePoint Online public de référence, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du Site**, tapez **campagne large**. 
    
6. Dans la **description de site d’équipe**, tapez le **site SharePoint pour toute la campagne**.
    
7. Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier de documents du site d’équipe de la campagne pour l’étiquette Interne.
  
1. Dans l’onglet **campagne wide-accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres à appliquer une étiquette**, sélectionnez **interne**, puis cliquez sur **Enregistrer**.
    
### <a name="campaign-project-1-team-site"></a>Site d’équipe 1 du projet Campagne

Pour créer un site d’équipe SharePoint Online privé de référence pour un projet dans la campagne, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du Site**, tapez **projet de campagne 1**. 
    
6. Dans la **description de site d’équipe,** tapez le **site SharePoint pour le projet de campagne 1**.
    
7. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier de documents du site d’équipe Projet Campagne 1 pour l’étiquette Privé.
  
1. Dans l’onglet **campagne projet 1-accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres à appliquer une étiquette**, sélectionnez **privé**, puis cliquez sur **Enregistrer**.
    
### <a name="campaign-marketing-team-site"></a>Site d’équipe marketing de campagne

Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources marketing de la campagne, procédez comme suit :
  
1. À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du site d’équipe**, tapez la **campagne marketing**.
    
6. Dans la **description de site d’équipe**, tapez le **site SharePoint pour la campagne de commercialisation (la casse)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
9. Dans l’onglet Nouveau de la **campagne marketing** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
10. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
11. Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @** <your organization name> **. onmicrosoft.com** dans la zone **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.
    
13. Dans la liste, cliquez sur **campagne marketing des membres** .
    
14. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue de **partage** , tapez **Senior et personnel stratégique**, sélectionnez-le, puis cliquez sur **partage**.
    
16. Répétez les étapes 14 et 15 pour le groupe **personnel d’Analytique** et le compte d’utilisateur **Regular1** .
    
17. Cliquez sur le bouton de retour de votre navigateur.
    
18. Dans la liste, cliquez sur **campagne marketing propriétaires** .
    
19. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
20. Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.
    
21. Cliquez sur le bouton de retour de votre navigateur.
    
22. Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **Campagne marketing-Accueil** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint des **Membres de campagne marketing** contient uniquement le **personnel d’encadrement et personnel stratégique** groupe (qui contienne les comptes d’utilisateurs candidats, ChiefOfStaff et Strategic1), le groupe de **campagne marketing** (qui contient le compte d’utilisateur administrateur global), le groupe **personnel d’Analytique** (qui contient le compte d’utilisateur DataScientist1) et le compte d’utilisateur **Regular1** .
    
- Le groupe SharePoint **Propriétaires de marketing de campagne** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint de **Campagne marketing-les visiteurs** ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe de **Campagnes marketing-propriétaires** ).
    
- Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.
    
Ensuite, configurez le dossier de documents du site d’équipe Marketing campagne pour l’étiquette Sensible.
  
1. Dans l’onglet **Campagne marketing-Accueil** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres à appliquer une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.
    
Ensuite, configurez une stratégie de prévention contre la perte données qui avertit les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette sensible à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources dans le site de campagne marketing.
  
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
    
### <a name="campaign-strategy-team-site"></a>Site d’équipe Stratégie de campagne

Pour créer un site d’équipe SharePoint Online isolé hautement confidentiel pour les ressources de stratégie de campagne, procédez comme suit :
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide de votre compte d’administrateur global.
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du site d’équipe**, tapez **stratégie de campagne**.
    
6. Dans la **description de site d’équipe**, tapez le **site SharePoint pour la stratégie de campagne (hautement confidentiel)**.
    
7.  Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
9. Dans l’onglet **stratégie de campagne** nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
10. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
11. Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
12. Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur ** OK**.
    
13. Dans la liste, cliquez sur **stratégie de campagne membres** .
    
14. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue de **partage** , tapez **Senior et personnel stratégique**, sélectionnez-le, puis cliquez sur **partage**.
    
16. Dans la liste, cliquez sur **stratégie de campagne propriétaires** .
    
17. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
18. Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.
    
19. Cliquez sur le bouton de retour de votre navigateur.
    
20. Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **accueil de la stratégie de la campagne** dans votre navigateur, puis fermez le volet **autorisations de Site** .
    
Voici les résultats de la configuration des autorisations :
  
- Le groupe SharePoint des **Membres de stratégie de campagne** contient uniquement le groupe **Senior et personnel stratégique** (qui contienne uniquement les comptes d’utilisateurs candidats, ChiefOfStaff et Strategic1) et le groupe de la **stratégie de campagne** (qui contient seul le compte d’administrateur global).
    
- Le groupe SharePoint **Propriétaires de stratégie de campagne** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).
    
- Le groupe SharePoint **Visiteurs de stratégie de campagne** ne contient aucun groupe ou compte d’utilisateur.
    
- Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de stratégie de campagne** ).
    
- Autres comptes d’utilisateur ne peut pas accéder au site ou ses ressources ou demander l’accès au site. Des autorisations supplémentaires sur le site doivent être effectuées par l’administrateur global ou par un membre du groupe de **Propriétaires de stratégie de campagne** .
    
Ensuite, configurez le dossier de documents du site d’équipe Stratégie de campagne pour l’étiquette Hautement confidentiel.
  
1. Dans l’onglet **accueil de la stratégie de la campagne** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
4. Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Hautement confidentielles**et puis cliquez sur **Enregistrer**.
    
Configurez ensuite une stratégie DLP qui empêche les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette hautement confidentielles à l’extérieur de l’organisation. Cette stratégie DLP s’applique aux ressources du site stratégie de campagne.
  
1. Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société.
    
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
    
Suivez les instructions de [RMS d’Azure activer avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Ensuite, configurez la Protection des informations Azure avec une nouvelle stratégie étendue et une étiquette secondaire pour la protection et d’autorisations avec les étapes suivantes :
  
1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.
    
5. Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.
    
6. Dans **nom de la stratégie** et l' **étiquette pour les documents dans le site de l’équipe stratégie campagne** dans la zone **Description**, tapez **CampaignStrategy** .
    
7. Cliquez sur **Sélectionner les utilisateurs ou les groupes d’obtiennent cette stratégie > groupes d’utilisateurs**, puis sélectionnez **Senior et personnel stratégique**.
    
8. Cliquez sur **Sélectionner > OK**.
    
9. Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.
    
10. Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.
    
11. Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.
    
12. Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.
    
13. Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.
    
14. Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.
    
15. Dans le volet **DAS utilisateurs et des groupes** , sélectionnez **Senior et stratégique personnel**, puis cliquez sur **Sélectionner**.
    
16. Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.
    
17. Cliquez deux fois sur **OK**.
    
18. Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.
    
19. Fermez le panneau de la nouvelle stratégie étendue.
    
20. Sur la lame de **protection des informations de Azure - stratégies étendues** , cliquez sur **Publier**, puis cliquez sur **Oui**.
    
Vous êtes désormais prêt à créer des documents dans ces quatre sites et à tester l’accès à ces sites avec divers comptes d’utilisateurs disponibles avec votre abonnement à la version d’évaluation. 
  
Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis vous connecter à partir de Microsoft Word avec un compte dans le ** Personnel d’encadrement et personnel stratégique** groupe de votre abonnement d’évaluation.
  
## <a name="see-also"></a>Voir aussi

[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Configurer des groupes et des utilisateurs pour un environnement de développement/test de campagne politique](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)




