---
title: Protéger les fichiers SharePoint Online avec des étiquettes Office 365 et la protection contre la perte de données
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Résumé : Appliquez des étiquettes Office 365 et des stratégies de protection contre la perte de données pour des sites d’équipe SharePoint Online, avec différents niveaux de protection des informations.'
ms.openlocfilehash: 52617e43f5c1bcb2ab958e751734a2f948ceba37
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Protéger les fichiers SharePoint Online avec des étiquettes Office 365 et la protection contre la perte de données

 **Résumé :** Appliquez des étiquettes Office 365 et des stratégies de protection contre la perte de données pour des sites d’équipe SharePoint Online, avec différents niveaux de protection des informations.
  
Suivez les étapes décrites dans cet article pour créer et déployer des étiquettes Office 365 et des stratégies DLP pour des sites d’équipe SharePoint Online de référence, sensibles et hautement confidentiels. Pour en savoir plus sur ces trois niveaux de protection, consultez la rubrique [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Étiquettes Office 365 pour vos sites SharePoint Online

Il existe trois phases pour créer et attribuer des étiquettes Office 365 à des sites d’équipe SharePoint Online.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>Phase 1 : Déterminer les noms des étiquettes Office 365

Dans cette phase, vous déterminez les noms de vos étiquettes Office 365 pour les quatre niveaux de protection des informations appliqués aux sites d’équipe SharePoint Online. Le tableau suivant répertorie les noms recommandés pour chaque niveau.
  
|**Niveau de protection du site d’équipe SharePoint Online**|**Nom de l’étiquette**|
|:-----|:-----|
|Base de référence - Public  <br/> |Public interne  <br/> |
|Base de référence - Privé  <br/> |Private  <br/> |
|Sensible  <br/> |Sensible  <br/> |
|Hautement confidentiel  <br/> |Hautement confidentiel  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>Phase 2 : Créer les étiquettes Office 365

Dans cette phase, vous créez puis vous publiez vos étiquettes déterminées pour les différents niveaux de protection des informations.
  
Pour créer les étiquettes, vous pouvez utiliser le Centre d’administration Office 365 ou Microsoft PowerShell.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Créer des étiquettes Office 365 avec le Centre d’administration Office 365

1. Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.
    
3. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration > Sécurité &amp; conformité**.
    
4. Sous le nouvel onglet **Accueil - Sécurité &amp; conformité de votre navigateur**, cliquez sur **Classifications > Étiquettes**.
    
5. Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.
    
6. Dans le volet **Nom de l’étiquette**, entrez le nom de l’étiquette, puis cliquez sur **Suivant**.
    
7. Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.
    
8. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour les autres étiquettes.
    
### <a name="create-office-365-labels-with-powershell"></a>Créer des étiquettes Office 365 avec PowerShell

1. [Connectez-vous au Centre Sécurité &amp; conformité d’Office 365 en utilisant PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) à distance, et spécifiez les informations d’identification d’un compte disposant du rôle Administrateur de la sécurité ou Administrateur de la société.
    
2. Complétez la liste des noms d’étiquette, puis exécutez ces commandes à l’invite de commandes PowerShell :
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Ensuite, procédez comme suit pour publier les nouvelles étiquettes Office 365.
  
1. Dans le volet **Accueil > Étiquettes** du Centre de sécurité &amp; conformité, cliquez sur **Publier les étiquettes**.
    
2. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.
    
3. Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
4. Cliquez sur **Terminé**.
    
5. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
6. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
7. Dans le volet **Nom de votre stratégie**, entrez un nom pour désigner l’ensemble des étiquettes dans **Nom**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis sur **Fermer**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Phase 3 : Appliquer les étiquettes Office 365 à vos sites SharePoint Online

Utilisez ces étapes pour appliquer les étiquettes Office 365 aux dossiers de documents de vos sites d’équipe SharePoint Online.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **SharePoint**.
    
2. Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur un site auquel vous devez affecter une étiquette Office 365.
    
3. Sous le nouvel onglet du Site SharePoint de votre navigateur, cliquez sur **Documents**.
    
4. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
5. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
6. Dans **Paramètres-Appliquer une étiquette**, sélectionnez l’étiquette de votre choix, puis cliquez sur **Enregistrer**.
    
7. Fermez l’onglet du site SharePoint Online.
    
8. Répétez les étapes 3 à 8 pour affecter des étiquettes Office 365 à vos autres sites SharePoint Online.
    
Voici la configuration finale.
  
![Étiquettes Office 365 pour les quatre types de sites d’équipe SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Stratégies de protection contre la perte de données pour vos sites SharePoint Online

Utilisez ces étapes pour configurer une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document sur un site d’équipe sensible SharePoint Online à l’extérieur de l’organisation.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.
    
2. Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.
    
3. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
4. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
5. Dans le volet **Nom de votre stratégie**, entrez le nom de la stratégie DLP sensible dans **Nom**, puis cliquez sur **Suivant**.
    
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
    
    Vous pouvez également saisir ou coller votre propre conseil de stratégie pour expliquer aux utilisateurs comment partager un fichier en dehors de votre organisation.
    
16. Cliquez sur **OK**.
    
17. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, désélectionnez la case **Empêcher les utilisateurs de partager un fichier et restreindre l’accès au contenu partagé**, puis cliquez sur **Suivant**.
    
18. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.
    
Voici le résultat de votre configuration pour les sites d’équipe SharePoint Online sensibles.
  
![Stratégie DLP pour un site d’équipe SharePoint Online isolé utilisant l’étiquette Office 365 Données sensibles.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Utilisez ces étapes pour configurer une stratégie de protection contre la perte de données qui bloque les utilisateurs quand ils partagent un document sur un site d’équipe SharePoint Online hautement confidentiel à l’extérieur de l’organisation.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Sécurité &amp; conformité**.
    
2. Sous le nouvel onglet **Sécurité &amp; conformité** de votre navigateur, cliquez sur **Protection contre la perte de données > Stratégie**.
    
3. Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.
    
4. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
5. Dans le volet **Nom de votre stratégie**, entrez le nom de la stratégie DLP hautement sensible dans **Nom**, puis cliquez sur **Suivant**.
    
6. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **Messagerie Exchange** et **Comptes OneDrive**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.
    
9. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **Étiquettes**.
    
10. Dans le volet **Étiquettes**, cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentiel**, cliquez sur **Ajouter**, puis sur **Terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.
    
13. Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
14. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
15. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
    Vous pouvez également saisir ou coller votre propre conseil de stratégie pour expliquer aux utilisateurs comment partager un fichier en dehors de votre organisation.
    
16. Cliquez sur **OK**.
    
17. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, sélectionnez **Exiger une justification professionnelle pour le remplacement**, puis cliquez sur **Suivant**.
    
18. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.
    
Voici le résultat de votre configuration pour les sites d’équipe SharePoint Online hautement confidentiels.
  
![Stratégie DLP pour un site d’équipe SharePoint Online isolé utilisant l’étiquette Office 365 Hautement confidentiel.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Étape suivante

[Protéger les fichiers SharePoint Online avec Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sécuriser les sites SharePoint Online dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


