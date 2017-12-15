---
title: "Protéger les fichiers SharePoint Online avec les étiquettes d’Office 365 et DLP"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: "Synthèse : S’applique à Office 365 stratégies de prevention (DLP) de perte de données et les étiquettes pour les sites d’équipe SharePoint Online avec différents niveaux de protection des informations."
ms.openlocfilehash: 502a899c586114644bb59a2d55ca388c819f7777
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Protéger les fichiers SharePoint Online avec les étiquettes d’Office 365 et DLP

 **Résumé :** Appliquer à Office 365 stratégies de prevention (DLP) de perte de données et les étiquettes pour les sites d’équipe SharePoint Online avec différents niveaux de protection des informations.
  
Utilisez les étapes de cet article pour concevoir et déployer des stratégies DLP planifié, sensibles et hautement confidentielles SharePoint Online sites d’équipe et des étiquettes d’Office 365. Pour plus d’informations sur ces trois niveaux de protection, voir les [fichiers et les sites SharePoint Online de la sécuriser](secure-sharepoint-online-sites-and-files.md).
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>Étiquettes Office 365 destinées aux sites SharePoint Online

Il existe trois phases pour créer et attribuer des étiquettes Office 365 à des sites d’équipe SharePoint Online.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>Phase 1 : choix d’un nom pour vos étiquettes Office 365

Au cours de cette phase, vous devez attribuer un nom à vos étiquettes Office 365, qui correspondent aux quatre niveaux de protection des informations appliqués aux sites d’équipe SharePoint Online. Le tableau suivant répertorie les noms recommandés pour chaque niveau.
  
|**SharePoint Online niveau de protection de site d’équipe**|**Nom de l’étiquette**|
|:-----|:-----|
|Référence-Public  <br/> |Public interne  <br/> |
|Référence-Privé  <br/> |Privé  <br/> |
|Sensible  <br/> |Sensible  <br/> |
|Hautement confidentiel  <br/> |Hautement confidentiel  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>Phase 2 : création des étiquettes Office 365

Au cours de cette phase, vous créez et publiez vos étiquettes correspondant aux différents niveaux de protection des informations.
  
Pour créer les étiquettes, vous pouvez utiliser le Centre d’administration Office 365 ou Microsoft PowerShell.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Créer des étiquettes Office 365 avec le Centre d’administration Office 365

1. Connectez-vous au portail Office 365 avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **Centre d’administration > sécurité &amp; la conformité**.
    
4. À partir du nouveau **maison - sécurité &amp; la conformité** onglet de votre navigateur, cliquez sur **les Classifications > étiquettes**.
    
5. À partir de le **Accueil > étiquettes** volet, cliquez sur **créer une étiquette**.
    
6. Dans le volet **nom de votre étiquette** , tapez le nom de l’étiquette, puis cliquez sur **suivant**.
    
7. Dans le volet **paramètres d’étiquette** , cliquez sur **suivant**.
    
8. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour les autres étiquettes.
    
### <a name="create-office-365-labels-with-powershell"></a>Créer des étiquettes Office 365 avec PowerShell

1. [Se connecter à la sécurité pour Microsoft Office 365 &amp; centre de conformité à l’aide du PowerShell distant](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) et spécifiez les informations d’identification d’un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société.
    
2. Complétez la liste des noms d’étiquettes, puis exécutez ces commandes à l’invite de commandes PowerShell :
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

Ensuite, suivez ces étapes pour publier les nouvelles étiquettes Office 365.
  
1. À partir de le **Accueil > étiquettes** volet de la sécurité &amp; centre de conformité, cliquez sur **publier les étiquettes**.
    
2. Dans le volet **Choisir les étiquettes à publier** , cliquez sur **Choisir les étiquettes à publier**.
    
3. Dans le volet **Choisir étiquettes** , cliquez sur **Ajouter** et sélectionner toutes les étiquettes de quatre.
    
4. Cliquez sur **terminé**.
    
5. Dans le volet **Choisir les étiquettes à publier** , cliquez sur **suivant**.
    
6. Dans le volet **Choisir des emplacements** , cliquez sur **suivant**.
    
7. Dans le volet **nom de votre stratégie** , tapez un nom pour votre ensemble d’étiquettes dans la zone **nom**, puis cliquez sur **suivant**.
    
8. Dans le volet de **passer en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>Phase 3 : application des étiquettes Office 365 à vos sites SharePoint Online

Suivez ces étapes pour appliquer les étiquettes Office 365 aux dossiers de documents de vos sites d’équipe SharePoint Online.
  
1. À partir de l’onglet **Accueil de Microsoft Office** de votre navigateur, cliquez sur la mosaïque de **SharePoint** .
    
2. Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur un site nécessitant une étiquette affectée d’Office 365.
    
3. Dans le nouvel onglet de site SharePoint de votre navigateur, cliquez sur **Documents**.
    
4. Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.
    
5. Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.
    
6. Dans **Les paramètres à appliquer une étiquette**, sélectionnez l’étiquette appropriée, puis cliquez sur **Enregistrer**.
    
7. Fermez l’onglet du site SharePoint Online.
    
8. Répétez les étapes 3 à 8 pour attribuer des étiquettes Office 365 à vos autres sites SharePoint Online.
    
Voici la configuration finale.
  
![Étiquettes Office 365 pour les quatre types de sites d’équipe SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>Stratégies DLP destinées à vos sites SharePoint Online

Suivez ces étapes pour configurer une stratégie DLP qui avertit les utilisateurs lorsqu’ils partagent un document sur un site d’équipe sensibles SharePoint Online à l’extérieur de l’organisation.
  
1. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
2. Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.
    
3. Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.
    
4. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.
    
5. Dans le volet **nom de votre stratégie** , tapez le nom de la stratégie DLP sensible dans la zone **nom**, puis cliquez sur **suivant**.
    
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
    
    Vous pouvez également saisir ou coller votre propre conseil de stratégie pour expliquer aux utilisateurs comment partager un fichier en dehors de votre organisation.
    
16. Cliquez sur **OK**.
    
17. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, désactivez la case à cocher **bloquer le partage, des personnes et de restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.
    
18. Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.
    
19. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Voici la configuration finale de vos sites d’équipe SharePoint Online sensibles.
  
![Stratégie DLP pour un site d’équipe SharePoint Online isolé utilisant l’étiquette Office 365 Données sensibles.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
Ensuite, suivez ces étapes pour configurer une stratégie DLP qui empêche les utilisateurs de partager un document sur un site SharePoint Online hautement confidentiel externe à l’organisation.
  
1. À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
2. Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.
    
3. Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.
    
4. Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.
    
5. Dans le volet **nom de votre stratégie** , tapez le nom de la stratégie DLP de niveau très sensible dans la zone **nom**, puis cliquez sur **suivant**.
    
6. Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.
    
8. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.
    
9. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.
    
10. Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.
    
13. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.
    
14. Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.
    
15. Dans la zone de texte, tapez ou collez le texte suivant :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
    Vous pouvez également saisir ou coller votre propre conseil de stratégie pour expliquer aux utilisateurs comment partager un fichier en dehors de votre organisation.
    
16. Cliquez sur **OK**.
    
17. Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.
    
18. Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.
    
19. Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.
    
Voici la configuration finale de vos sites d’équipe SharePoint Online hautement confidentiels.
  
![Stratégie DLP pour un site d’équipe SharePoint Online isolé utilisant l’étiquette Office 365 Hautement confidentiel.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>Étape suivante

[Protéger les fichiers SharePoint Online avec Azure la Protection des informations](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>See Also

[Sécurisation des fichiers et sites SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Sites SharePoint en ligne sécurisés dans un environnement de développement/test](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d'autres organisations flexibles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


