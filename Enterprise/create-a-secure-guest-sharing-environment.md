---
title: Créer un environnement de partage d’invités sécurisé
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Priority
f1.keywords: NOCSH
description: Découvrir comment créer un environnement de partage d’invités sécurisé avec Microsoft 365.
ms.openlocfilehash: 4c77ae6905341ba7cde974b2fc3966009a38d512
ms.sourcegitcommit: 27172140051c31f5cd3f28ffb4282669d561549a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42155573"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Créer un environnement de partage d’invités sécurisé

Dans cet article, nous allons découvrir de nombreuses options permettant de créer un environnement de partage d’invités sécurisé dans Microsoft 365. Il s’agit d’un exemple de scénario qui vous donne une idée des options disponibles. Vous pouvez utiliser ces procédures dans différentes combinaisons pour répondre aux besoins de sécurité et de conformité de votre organisation. À la fin de cet article, nous allons passer en revue un cas type afin de découvrir comment certaines de ces options fonctionnent ensemble.

Ce scénario comprend les points suivants :

- Configuration de l'authentification multifacteur pour les invités.
- Configuration des conditions d’utilisation pour les invités.
- Configuration des révisions trimestrielles d’accès invité pour vérifier régulièrement si les invités ont toujours besoin d’autorisations pour les équipes et les sites.
- Limitation de l’accès des invités au Web uniquement pour les appareils non gérés.
- Configuration d’une stratégie de délai d’expiration de session pour assurer l’authentification quotidienne des invités.
- Création et publication des étiquettes de sensibilité pour classifier le contenu.
- Création d’un type d’informations sensibles pour un projet hautement confidentiel.
- Attribution automatique d’une étiquette *hautement confidentielle* aux documents contenant le type d’informations sensibles.
- Suppression automatique de l’accès invité des fichiers étiquetés comme *hautement confidentiels*.

Certaines des options décrites dans cet article exigent que les invités disposent d’un compte dans Azure Active Directory. Pour vous assurer que les invités sont bien inclus dans le répertoire lorsque vous partagez des fichiers et des dossiers avec eux, utilisez l’[intégration de SharePoint et OneDrive avec Azure AD B2B Préversion](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).

Notez que nous n'aborderons pas l'activation des paramètres de partage des invités dans cet article. Consultez la rubrique [Collaborer avec des personnes extérieures à votre organisation](https://docs.microsoft.com/Office365/Enterprise/collaborating-with-people-outside-your-organization) pour plus d’informations sur l'activation du partage des invités pour différents scénarios.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Configurer l'authentification multifacteur pour les invités.

L’authentification multifacteur réduit considérablement les risques de compromission d’un compte. Étant donné que les utilisateurs invités peuvent utiliser des comptes de messagerie personnels qui ne sont soumis à aucune stratégie de gouvernance ou pratique exemplaire, il est particulièrement important d’exiger une authentification multifacteur pour les invités. En cas de vol du nom d'utilisateur et du mot de passe d'un utilisateur invité, la nécessité d'un second facteur d'authentification réduit considérablement les chances de voir des inconnus accéder à vos sites et fichiers.

Dans cet exemple, nous allons configurer l’authentification multifacteur pour les invités à l’aide d’une stratégie d’accès conditionnel dans Azure Active Directory.

Pour configurer l'authentification multifacteur pour les invités, procédez comme suit :
1. Dans Microsoft Azure, recherchez *Accès conditionnel*.
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans le champ **Nom**, tapez *Invité MFA*.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**, puis cliquez sur **Terminé**.
4. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
5. Dans le panneau **Accorder**, activez la case à cocher **Exiger une authentification multifacteur**, puis cliquez sur **Sélectionner**.
6. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

Les invités doivent maintenant s'inscrire à l'authentification multifacteur avant de pouvoir accéder au contenu, aux sites ou aux équipes partagés.

### <a name="more-information"></a>Plus d’informations

[Planifier le déploiement d’une authentification multifacteur Azure basée sur Cloud](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Configurer les conditions d’utilisation pour les invités

Il arrive souvent que des utilisateurs invités n'aient pas signé de contrat de non-divulgation ou autres accords juridiques avec votre organisation. Vous pouvez demander aux invités d’accepter les conditions d’utilisation avant d’accéder aux fichiers partagés avec eux. Les conditions d’utilisation peuvent s’afficher lors de la première tentative d’accès à un fichier ou à un site partagé.

Pour créer des conditions d’utilisation, vous devez commencer par créer le document dans Word ou dans un autre logiciel de création, puis l’enregistrer sous forme de fichier .pdf. Ce fichier peut ensuite être chargé sur Azure AD.

Pour créer des conditions d’utilisation d’Azure AD, procédez comme suit :
1. Connectez-vous à Azure en tant qu’administrateur général, administrateur de sécurité ou administrateur d’accès conditionnel.
2. Accédez aux [Conditions d’utilisation](https://aka.ms/catou).
3. Cliquez sur **Nouvelles conditions d’utilisation**.</br>
   ![Capture d'écran des paramètres des nouvelles conditions d'utilisation d'Azure AD](media/azure-ad-guest-terms-of-use.png)
4. Dans les zones **Nom** et **Afficher le nom**, tapez *Conditions d’utilisation de l’invité*.
6. Pour le **document Conditions d'utilisation**, accédez au fichier PDF que vous avez créé et sélectionnez-le.
7. Sélectionnez la langue de votre document Conditions d’utilisation.
8. Validez l'option **Demander aux utilisateurs d'étendre les conditions d'utilisation** en la définissant sur **ACTIVÉ**.
9. Sous **Accès conditionnel**, dans la liste **Appliquer le modèle de stratégie sur l'accès conditionnel**, choisissez **Créer une stratégie d'accès conditionnel ultérieurement**.
10. Cliquez sur **Créer**.

Une fois que vous avez créé les conditions d’utilisation, l’étape suivante consiste à créer une stratégie d’accès conditionnel qui affiche les conditions d’utilisation des utilisateurs invités.

Pour créer une stratégie d’accès conditionnel, procédez comme suit :
1. Dans Microsoft Azure, recherchez *Accès conditionnel*.
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans la zone **Nom**, tapez *Stratégie des conditions d’utilisation des utilisateurs invités*.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**, puis cliquez sur **Terminé**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, **Office 365 SharePoint Online** et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Dans le panneau **Actions ou applications Cloud**, cliquez sur **Terminé**.
10. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
11. Dans le panneau **Accorder**, sélectionnez **Conditions d’utilisation de l’invité**, puis cliquez sur **Sélectionner**.
12. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

À présent, la première fois qu’un utilisateur invité tente d’accéder au contenu, à une équipe ou à un site de votre organisation, il est tenu d’accepter les conditions d’utilisation.

### <a name="more-information"></a>Plus d’informations
[Conditions d’utilisation d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use).

## <a name="set-up-guest-access-reviews"></a>Configurer les révisions d’accès invité

Avec les révisions d’accès dans Azure AD, vous pouvez automatiser une révision périodique de l’accès des utilisateurs à plusieurs équipes et groupes. En exigeant spécifiquement une révision d’accès pour les invités, vous pouvez vous assurer que les utilisateurs invités ne conservent pas l’accès aux informations sensibles de votre organisation plus longtemps que nécessaire.

Les révisions d’accès peuvent être organisées en programmes. Un programme est un regroupement de révisions d’accès similaires qui peut être utilisé pour organiser des révisions d’accès à des fins de création de rapports et d’audit.

Dans cet exemple, vous allez créer un programme pour les révisions d’accès invité.

Pour créer un nouveau programme, procédez comme suit :
1. Connectez-vous au Portail Microsoft Azure et ouvrez l’onglet [Page de Gouvernance d’identité](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade).
2. Dans le menu de gauche, cliquez sur **Programmes**
3. Cliquez sur **Nouveau programme**.
4. Dans la zone **Nom**, tapez *Programme de révision d’accès invité*.
5. Dans la zone **Description**, tapez *Programme pour les révisions d’accès invité*.
6. Cliquez sur **Créer**.

Une fois le programme a été créé, nous pouvons créer une révision d’accès invité et l’associer au programme.

Pour configurer une révision d’accès des utilisateurs invités, procédez comme suit :
1. Sur la [Page de Gouvernance d’identité](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), dans le menu de gauche, cliquez sur **Révisions d’accès**.
2. Cliquez sur **Nouvelle révision d’accès**.</br>
   ![Capture d’écran des paramètres de révision d’accès d’Azure AD](media/azure-ad-create-access-review.png)
3. Dans la zone **Nom**, tapez *Révision trimestrielle d’accès invité*.
4. Pour **Fréquence**, choisissez **Trimestrielle**.
5. Pour **Fin**, choisissez **Jamais**.
6. Pour **Portée**, choisissez **Utilisateurs invités uniquement**.
7. Cliquez sur **Groupe**, sélectionnez les groupes que vous voulez inclure dans la révision Access, puis cliquez sur **Sélectionner**.
8. Sous **Programmes**, cliquez sur **Lier au programme**.
9. Dans le panneau **Sélectionner un programme**, choisissez **Programme de révision d’accès invité**
10. Cliquez sur **Démarrer**.

Une révision d’accès distincte est créée pour chaque groupe que vous spécifiez. Les propriétaires de groupe de chaque groupe recevront un e-mail trimestriel pour accepter ou refuser l'accès invité à leurs groupes.

Il est important de noter que les invités peuvent avoir accès à des équipes ou à des groupes, ou à des fichiers et dossiers individuels. Lorsque l'accès aux fichiers et dossiers leur est accordé, les invités ne peuvent pas être ajoutés à un groupe particulier. Si vous souhaitez effectuer des révisions d’accès sur des utilisateurs invités qui n'appartiennent ni à une équipe ni à un groupe, vous pouvez créer un groupe dynamique dans Azure AD pour contenir tous les invités, puis créer une révision d’accès pour ce groupe.

### <a name="more-information"></a>Plus d’informations
[Gérer l’accès invité avec les révisions d’accès Azure AD](https://docs.microsoft.com/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Créer une révision d'accès de groupes ou d'applications dans les révisions d'accès Azure AD](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guest-users"></a>Configurer l’accès Web uniquement pour les utilisateurs invités

Vous pouvez réduire votre surface d'attaque et simplifier l'administration en demandant aux utilisateurs invités d'accéder à vos équipes, sites et fichiers en utilisant uniquement un navigateur Web. Cette opération se réalise à l’aide d’une stratégie d’accès conditionnel Azure AD.

Pour limiter l'accès Web uniquement aux invités, procédez comme suit :
1. Dans Microsoft Azure, recherchez *Accès conditionnel*.
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans la zone **Nom**, tapez *Accès au navigateur de l'utilisateur invité*.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**, puis cliquez sur **Terminé**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, **Office 365 SharePoint Online** et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Dans le panneau **Actions ou applications Cloud**, cliquez sur **Terminé**.
10. Sous **Affectations**, cliquez sur **Conditions**.
11. Dans le panneau **Conditions**, cliquez sur **Applications clientes**.
12. Dans le panneau **Applications clientes**, cliquez sur **Oui** pour **configurer**, puis sélectionnez les paramètres **Applications mobiles et clients de bureau** et **Clients d’authentification modernes**.</br>
    ![Capture d'écran des paramètres des applications clientes à accès conditionnel d'Azure AD](media/azure-ad-conditional-access-client-mobile.png)
13. Cliquez sur **Terminé**, puis dans le panneau **Conditions**, cliquez de nouveau sur **Terminé**.
14. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
15. Sur le panneau **Accorder**, sélectionnez les options **Exige que l’appareil soit marqué comme conforme** et **Exige un appareil joint Azure AD Hybride**.
16. Sous **Pour plusieurs contrôles**, sélectionnez **Exige l’un des contrôles sélectionnés**, puis cliquez sur **Sélectionner**.
17. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

## <a name="configure-a-session-timeout-for-guest-users"></a>Configurer un délai d’expiration de session pour les utilisateurs invités

Exiger des invités qu'ils s'authentifient régulièrement peut réduire le risque que des utilisateurs inconnus accèdent au contenu de votre organisation si l'appareil d'un utilisateur invité n'est pas sécurisé. Vous pouvez configurer une stratégie d’accès conditionnel de délai d’expiration de session pour les utilisateurs invités dans Azure AD.

Pour configurer une stratégie de délai d’expiration de session d’invité, procédez comme suit :
1. Dans Microsoft Azure, recherchez *Accès conditionnel*.
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans la zone **Nom**, tapez *Délai d’expiration de session des invités*.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**, puis cliquez sur **Terminé**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, **Office 365 SharePoint Online** et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Dans le panneau **Actions ou applications Cloud**, cliquez sur **Terminé**.
10. Sous **Contrôles d’accès**, cliquez sur **Session**.
11. Dans le panneau **Session**, sélectionnez **Fréquence de connexion**.
12. Sélectionnez **1** et **Jours** pour la période, puis cliquez sur **Sélectionner**.
13. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

## <a name="create-sensitivity-labels"></a>Créer des étiquettes de sensibilité

Les étiquettes de sensibilité peuvent être utilisées de différentes manières pour classifier et protéger les informations de votre organisation. Dans cet exemple, vous allez examiner comment les étiquettes peuvent être utilisées pour vous aider à gérer l’accès invité aux fichiers et dossiers partagés.

Tout d’abord, vous allez créer trois étiquettes de sensibilité dans le Centre de conformité Microsoft 365 :

- Général
- Confidentiel
- Hautement confidentiel

Utilisez la procédure suivante pour créer les étiquettes *Général* et *Confidentiel*.

Pour créer une étiquette de classification (Général et Confidentiel), procédez comme suit :
1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), dans le volet de navigation gauche, développez **Classification**, puis cliquez sur **Étiquettes de sensibilité**.
2. Cliquez sur **Créer une étiquette**.
3. Dans **Nom d’étiquette**, tapez *Général* ou *Confidentiel*.
4. Dans **Infobulle**, tapez *Informations générales pouvant être partagées avec des employés, des invités et des partenaires* ou *Informations confidentielles. Partagez-les uniquement avec les employés et les invités*, puis cliquez sur **Suivant**.
5. Laissez l'option Chiffrement sur **Désactiver**, puis cliquez sur **Suivant**.
6. Laissez l’option Marquage de contenu sur **Désactiver**, puis cliquez sur **Suivant**.
7. Laissez l’option Prévention contre la perte de données sur **Désactiver**, puis cliquez sur **Suivant**.
8. Laissez l’option Étiquetage automatique sur **Désactiver**, puis cliquez sur **Suivant**.
9. Cliquez sur **Créer**.

Grâce à l'étiquette *Hautement confidentiel*, vous ajoutez le filigranage automatique des documents avec l'étiquette.

Pour créer une étiquette de classification (Hautement confidentiel), procédez comme suit :
1. Cliquez sur **Créer une étiquette**.
2. Dans **Nom d’étiquette**, tapez *Hautement confidentiel*.
3. Dans **Infobulle**, tapez *Informations hautement confidentielles. Ne les partagez pas avec les invités*, puis cliquez sur **Suivant**.
4. Laissez l'option Chiffrement sur **Désactiver**, puis cliquez sur **Suivant**.
5. Mettez l'option Marquage de contenu sur **Activer**, cochez la case **Ajouter un en-tête**, puis cliquez sur **Personnaliser le texte**.
6. Tapez *Hautement confidentiel* comme texte d'en-tête et cliquez sur **Enregistrer**.
7. Sur la page **Marquage de contenu**, mettez l'option Marquage de contenu sur **Activer**.
8. Activez la case à cocher **Ajouter un filigrane**, puis cliquez sur **Personnaliser le texte**.
9. Comme **texte de filigrane**, tapez *Hautement confidentiel*.
10. Tapez *24* comme **Taille de police**, puis cliquez sur **Enregistrer**.
11. Dans la page **Marque de contenu**, cliquez sur **Suivant**.
12. Laissez l’option Prévention contre la perte de données sur **Désactiver**, puis cliquez sur **Suivant**.
13. Laissez l’option Étiquetage automatique sur **Désactiver**, puis cliquez sur **Suivant**.
14. Cliquez sur **Créer**.

![Capture d’écran des étiquettes de sensibilité dans le Centre de conformité Microsoft 365](media/microsoft-365-sharing-sensitivity-labels.png)

Une fois les étiquettes créées, l'étape suivante consiste à les publier. 

Pour publier les étiquettes, procédez comme suit :
1. Dans la page **Étiquettes de sensibilité**, cliquez sur **Publier les étiquettes**.
2. Cliquez sur **Choisir les étiquettes à publier**.
3. Cliquez sur **Ajouter**, sélectionnez les étiquettes que vous avez créées, puis cliquez sur **Ajouter**.
4. Cliquez sur **Terminé**.
5. Cliquez sur **Suivant**.
6. Laissez l’option Utilisateurs et groupes définie sur **Tous**, puis cliquez sur **Suivant** .
7. Dans la liste **Appliquer cette étiquette par défaut aux documents et aux e-mails**, choisissez l’étiquette **Général**, puis cliquez sur **Suivant**.
8. Dans la page **Paramètres de stratégie**, tapez *Sensibilité du document* comme nom, puis cliquez sur **Suivant**.
9. Cliquez sur **Publier**.

Une fois les étiquettes publiées, celles-ci sont disponibles pour les utilisateurs des applications de bureau Office. Lorsque les utilisateurs appliquent l’étiquette **Hautement confidentiel**, un filigrane est automatiquement ajouté au document.

### <a name="more-information"></a>Plus d’informations
[Vue d’ensemble des étiquettes de sensibilité](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

## <a name="create-a-sensitive-information-type-for-a-highly-confidential-project"></a>Créer un type d’informations sensibles pour un projet hautement confidentiel.

Les types d’informations sensibles sont des chaînes prédéfinies qui peuvent être utilisées dans les flux de travail de stratégie afin d’appliquer les exigences de conformité. Le Centre de conformité Microsoft 365 est fourni avec plus d’une centaine de types d’informations sensibles, y compris les numéros de permis de conduire, les numéros de cartes de crédit, les numéros de comptes bancaires, etc.

Vous pouvez créer des types d'informations sensibles personnalisés pour vous aider à gérer le contenu propre à votre organisation. Dans cet exemple, vous allez créer un type d’informations sensibles personnalisé pour un projet hautement confidentiel. Vous pouvez ensuite utiliser ce type d’informations sensibles pour appliquer automatiquement une étiquette de classification.

Pour créer un type d’informations sensibles personnalisé, procédez comme suit :
1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), dans le volet de navigation gauche, développez **Classification**, puis cliquez sur **Types d’informations sensibles**.
2. Cliquez sur **Créer**.
3. Pour **Nom** et **Description**, tapez **Projet Saturne**, puis cliquez sur **Suivant**.
4. Cliquez sur **Ajouter un élément**.
5. Dans la liste **Détecter le contenu contenant**, sélectionnez **Mots clés**, puis tapez *Projet Saturne* dans la zone de mot clé.
6. Cliquez sur **Suivant**, puis sur **Terminer**.
7. Si vous êtes invité à tester le type d’informations sensibles, cliquez sur **Non**.

### <a name="more-information"></a>Plus d’informations
[Types d’informations sensibles personnalisés](https://docs.microsoft.com/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-a-policy-to-assign-a-label-based-on-a-sensitive-information-type"></a>Créer une stratégie pour attribuer une étiquette sur la base d’un type d’informations sensibles

Une fois le type d’informations sensibles créé, nous pouvons créer une stratégie de fichier dans Microsoft Cloud App Security pour appliquer automatiquement l’étiquette *Hautement confidentiel* aux documents qui contiennent la chaîne du *Projet Saturne*.

> [!NOTE]
> Il existe un processus de réplication qui rend les étiquettes de sensibilité disponibles dans Cloud App Security. Vous ne verrez peut-être pas l’étiquette disponible pour une stratégie immédiatement.

Pour créer une stratégie de fichier basée sur le type d'informations sensibles, procédez comme suit :
1. Ouvrez [Microsoft Cloud App Security](https://portal.cloudappsecurity.com).
2. Dans le volet de navigation gauche, développez **Contrôle**, puis cliquez sur **Stratégies**.
3. Cliquez sur **Créer une stratégie**, puis choisissez **Stratégie de fichier**.
4. Dans **Nom de stratégie**, tapez *Étiquetage du Projet Saturne*.
5. Sous **Créer un filtre pour les fichiers sur lesquels cette stratégie doit agir**, cliquez sur X à deux reprises pour supprimer les filtres par défaut.
7. Dans la liste **Sélectionner un filtre**, choisissez **Applications**, puis sélectionnez **Microsoft SharePoint Online** dans la liste **Sélectionner les applications...**.
8. Sous **Méthode d’inspection**, choisissez **Service de classification des données**.
9. Dans la liste **Choisir le type d’inspection**, choisissez **Type d’informations sensibles**.
10. Recherchez et sélectionnez l’étiquette de sensibilité du *Projet Saturne*, puis cliquez sur **Terminé**.</br>
   ![Capture d’écran des paramètres de la méthode d’inspection de Cloud App Security](media/mcas-sensitive-info-type-project-saturn.png)
11. Sous **Gouvernance**, développez **Microsoft SharePoint Online**.
12. Activez la case à cocher **Appliquer une étiquette de classification**, puis sélectionnez l’étiquette **Hautement confidentiel**.
13. Cliquez sur **Créer**.

Une fois la stratégie en place, lorsqu’un utilisateur tape « Projet Saturne » dans un document, Cloud App Security applique automatiquement l’étiquette *Hautement confidentiel* lors de l’analyse du fichier.

### <a name="more-information"></a>Plus d’informations
[Stratégies de fichier](https://docs.microsoft.com/cloud-app-security/data-protection-policies)

## <a name="create-a-policy-to-remove-guest-access-to-highly-confidential-files"></a>Créer une stratégie pour supprimer l’accès invité aux fichiers hautement confidentiels

Dans l’exemple de cet article, les fichiers comportant l’étiquette *Hautement confidentiel* ne doivent pas être partagés avec des invités. Nous pouvons créer une stratégie de fichier dans Cloud App Security qui supprime automatiquement l’accès invité aux fichiers comportant cette étiquette.

Notez que cela n’empêche pas les utilisateurs de partager ou de repartager ces fichiers. Vous êtes tout de même tributaire de vos utilisateurs pour suivre vos stratégies de gouvernance pour les fichiers stockés dans des sites qui autorisent le partage avec des invités. Toutefois, il peut s’agir d’un outil utile pour supprimer l’accès invité à partir de fichiers auxquels des informations confidentielles ont été ajoutées une fois qu’elles ont été partagées avec des invités.

Pour créer une stratégie de fichier sur la base d’étiquette, procédez comme suit :
1. Ouvrez [Microsoft Cloud App Security](https://portal.cloudappsecurity.com).
2. Dans le volet de navigation gauche, développez **Contrôle**, puis cliquez sur **Stratégies**.
3. Cliquez sur **Créer une stratégie**, puis choisissez **Stratégie de fichier**.
4. Comme **Nom de stratégie**, tapez *Projet Saturne – Supprimer l'accès invité*.
5. Sous **Créer un filtre pour les fichiers sur lesquels cette stratégie doit agir**, cliquez sur X à deux reprises pour supprimer les filtres par défaut.
6. Dans la liste **Sélectionner un filtre**, choisissez **Applications**, puis sélectionnez **Microsoft SharePoint Online** dans la liste **Sélectionner les applications...**.
7. Cliquez sur **Ajouter un filtre**.
8. Dans la liste **Sélectionner un filtre**, choisissez **Étiquette de classification**, puis sélectionnez l’option **Protection des informations Azure** dans la liste **Sélectionner un filtre...**.
9. Dans la liste **Sélectionner une étiquette de classification**, sélectionnez **Hautement confidentiel**.</br>
   ![Capture d’écran des paramètres de filtre de la stratégie de Cloud App Security](media/mcas-sharepoint-confidential-label-filter.png)
10. Sous **Gouvernance**, développez **Microsoft SharePoint Online**.
11. Activez les cases à cocher **Envoyer le résumé des correspondances de stratégie au propriétaire du fichier** et **Supprimer les utilisateurs externes**.
12. Comme message de notification personnalisé, tapez *Ce fichier est hautement confidentiel. La stratégie d’entreprise interdit de le partager avec des invités*.
13. Cliquez sur **Créer**.

Il est important de noter que cette politique supprime l'accès aux fichiers partagés à l'aide d'un lien de *Personnes spécifiques*. Elle ne supprime pas l'accès aux liens (*des personnes*) non authentifiés. Elle ne supprime pas non plus l’accès si l’invité est membre du site ou de l’équipe dans son ensemble. Si vous comptez utiliser des documents hautement confidentiels dans un site ou une équipe comptant des membres invités, envisagez d'utiliser des c[anaux privés dans Teams ](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9)et d'autoriser uniquement les membres de votre organisation dans les canaux privés.

## <a name="test-the-solution"></a>Tester la solution

Pour tester la solution décrite dans cet article, créez un document Word et enregistrez-le dans une bibliothèque de documents. Partagez le fichier avec un utilisateur invité. Lorsque l’invité tente d'accéder au document, il doit être tenu de s'inscrire à l'authentification multifacteur, puis d'accepter les conditions d'utilisation.

Une fois que l'invité a accès au document, tapez *Projet Saturne* dans le document et enregistrez-le. Une fois que Cloud App Security a analysé le document, l’étiquette *Hautement confidentiel* doit être appliquée et l’utilisateur invité ne doit plus y avoir accès.

Vous pouvez utiliser les outils décrits dans cet article dans diverses combinaisons pour aider à créer un environnement de partage d'invités productif mais sûr pour votre organisation.

## <a name="additional-options"></a>Options supplémentaires

D'autres options existent dans Microsoft 365 et Azure Active Directory vous permettant de sécuriser votre environnement de partage d'invités.

- Vous pouvez créer une liste de domaines de partage autorisés ou refusés pour limiter les personnes avec lesquelles les utilisateurs peuvent effectuer des partages. Pour plus d’informations, consultez [Restreindre le partage de contenu SharePoint et OneDrive par domaine](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) et [Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list).
- Vous pouvez également limiter d'autres locataires Azure Active Directory avec lesquels vos utilisateurs peuvent se connecter. Pour plus d'informations, voir [Utilisez les restrictions liées au locataire pour gérer l’accès aux applications cloud SaaS](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions).
- Vous pouvez créer un environnement géré dans lequel vos partenaires peuvent vous aider à gérer des comptes d'invités. Pour plus d’informations, voir [Créer un extranet B2B avec des invités gérés](https://docs.microsoft.com/Office365/Enterprise/b2b-extranet).

## <a name="see-also"></a>Voir aussi

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](sharing-limit-accidental-exposure.md)

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)
