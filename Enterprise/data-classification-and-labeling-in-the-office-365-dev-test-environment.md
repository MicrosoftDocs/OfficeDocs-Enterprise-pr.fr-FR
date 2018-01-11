---
title: "Classification et étiquetage des données dans l’environnement de développement/test Office 365"
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "Résumé : Configurer et montrez la classification des données et des étiquettes à l’aide du client de Protection d’informations Azure (AIP) dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: a2db6817bea879caeb52ed9b11b40c6c317ea171
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classification et étiquetage des données dans l’environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer le d’étiquetage à l’aide du client de Protection d’informations Azure (AIP) dans votre environnement de développement/test d’Office 365 et de classification des données.
  
Le client de Protection d’informations Azure vous permet de classer un document avant de le télécharger vers un dossier SharePoint Online dans Office 365. Avec les instructions de cet article, vous installez le client de Protection d’informations Azure et montrez la classification des données. Pour plus d’informations, reportez-vous à la section [Protection des informations Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1 : créer votre environnement de développement/test Office 365

Suivez les instructions dans [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Phase 2 : ajouter l’abonnement à la version d’évaluation Azure Information Protection

Dans cette phase, vous ajoutez Azure la Protection des informations à votre environnement de développement/test d’Office 365 et l’activer pour vos comptes d’utilisateur. Si vous avez configuré l' [Office 365 et environnement de développement/test EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorez cette phase. L’abonnement d’évaluation de la Suite Enterprise mobilité inclut des licences de la Protection des informations Azure.
  
Tout d’abord, souscrivez un abonnement à la version d’évaluation Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Souscrire à un abonnement à la version d’évaluation Azure Information Protection

1. Dans Internet Explorer ou votre navigateur, accédez à [http://portal.office.com](http://portal.office.com) et connectez-vous à votre compte d’administrateur global de Office 365.
    
2. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet administration d’Office 365, la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver la **Azure informations Protection Premium P2** . Faites glisser votre souris sur celui-ci, puis cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
Ensuite, vous activez la licence de Azure Information Protection pour tous les comptes d’utilisateur.
  
1. Dans l’onglet Centre d’administrateur Office 365, cliquez sur **utilisateurs**.
    
2.  Dans la liste des comptes d’utilisateurs, sélectionnez votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Activer la licence produit pour **Azure informations Protection Premium P2** sur **On**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
4. Répétez les étapes 2 et 3 pour d’autres comptes d’utilisateur (Utilisateur 1 à Utilisateur 5).
    
Votre environnement de développement/test Office 365 comprend désormais :
  
- Abonnements à la version d’évaluation d’Office 365 E5 Entreprise et Azure Information Protection.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Phase 3 : démontrer la classification des données

Lors de cette phase, vous démontrez la classification des données à l’aide du client Azure Information Protection et de la stratégie Azure Information Protection par défaut.
  
Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, vous devez tout d’abord installer Office 2016 sur CLIENT1.
  
1. Utilisez votre navigateur et accédez au [portail Azure](http://portal.azure.com).
    
2. Cliquez sur **les groupes de ressources >** [nom de votre groupe de ressources] **> CLIENT1 > Connect**.
    
3. À partir de CLIENT1, exécutez Internet Explorer, accédez au portail Office à [http://portal.office.com](http://portal.office.com)et puis connectez-vous avec le nom User5 et le mot de passe.
    
4. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **installer un 2016 Office**.
    
5. Exécuter le téléchargement lorsque vous y êtes invité, puis cliquez sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur. Attente de Office à installer. Lorsque vous avez terminé, cliquez sur **Fermer** deux fois.
    
Ensuite, installez le client Azure Information Protection.
  
1. Dans votre navigateur ou dans Internet Explorer, accédez à la [page de téléchargement de Microsoft Azure la Protection des informations](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Si vous utilisez la version légère de l’environnement de développement/test Office 365, utilisez le navigateur sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, exécutez Internet Explorer à partir de CLIENT1.
    
2. Sur la page de téléchargement de **Microsoft Azure la Protection des informations** , cliquez sur **Télécharger**, cliquez sur **AzInfoProtection.exe**, puis cliquez sur **suivant**.
    
3. Lorsque vous y êtes invité, exécutez AzInfoProtection.exe.
    
4. Dans la zone client **installer la Protection des informations Azure** , cliquez sur **J’accepte**, puis cliquez sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.
    
5. Dans la zone **terminé** , cliquez sur **Fermer.**
    
Ensuite, démontrez la classification des documents.
  
1. Cliquez sur l’icône **Word** dans la barre des tâches.
    
2. Lorsque vous y êtes invité, connectez-vous avec le nom de compte Utilisateur 5 et le mot de passe associé.
    
3. Si vous avez installé 2016 Office sur CLIENT1, à le **Premièrement premier** , cliquez sur **Accepter**.
    
4. Cliquez sur **document vierge**. 
    
    Notez la section **Protection** du ruban de l’onglet **accueil** et de la ligne de classifications de document.
    
5. Dans le document vierge, tapez du texte.
    
6. Cliquez sur **fichier > Enregistrer**, tapez le nom **BeforeAIP**, puis cliquez sur **OK**. 
    
7. Dans la ligne des classes de documents, cliquez sur la flèche vers le bas pour le **Secret**, puis cliquez sur **Toutes les société**.
    
8. Cliquez sur **fichier > Enregistrer sous**, tapez le nom **AfterAIP**, puis cliquez sur **OK**.
    
9. Cliquez sur **Explorateur de fichiers** dans la barre des tâches et ouvrez le dossier **Documents** .
    
    Notez les tailles de fichier différentes des documents **BeforeAIP** et **AfterAIP** . Le document AfterAIP est plus grand, car il contient les informations de classification.
    
Ensuite, autorisez tout le monde à accéder à la collection de sites Prise en charge.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **SharePoint**.
    
2. À partir de l’onglet de **SharePoint** , cliquez sur **collection de site de prise en charge**.
    
3. Dans le coin supérieur droit, cliquez sur l’icône de **paramètres** , puis cliquez sur **partagé avec**.
    
4. Dans **partage « Collection de sites de Support »**, cliquez sur **Avancé**.
    
5. Dans la liste des groupes SharePoint, cliquez sur **collection de site de prise en charge des membres**.
    
6. Dans la page **personnes et groupes** , cliquez sur **Nouveau**.
    
7. Dans **partage « Collection de sites de Support »**, tapez **tout le monde**et cliquez sur **tout le monde excepté les utilisateurs externes**, puis cliquez sur **partage.**
    
8. Fermez l’onglet **personnes et groupes** .
    
Ensuite, connectez-vous avec votre compte Utilisateur 5 et chargez le document protégé par AIP dans le dossier Documents de la collection de sites Prise en charge.
  
1. Sous l’onglet **Accueil de Microsoft Office** , dans le coin supérieur droit, cliquez sur l’icône de l’utilisateur, puis cliquez sur **se déconnecter**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Sur la ** Office 365 se connecter ** page, cliquez sur le nom du compte User5 et reconnectez-vous.
    
4. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **SharePoint > prend en charge la collection de sites**.
    
5. Cliquez sur **Documents**et cliquez sur **Télécharger**, cliquez sur le document **AfterAIP** , puis cliquez sur **Ouvrir**.
    
    Vous devriez voir AfterAIP.docx dans le dossier Documents de la collection de sites Prise en charge.
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 et environnement de développement/test EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Protection des informations Azure](https://www.microsoft.com/cloud-platform/azure-information-protection)


