---
title: Classification et étiquetage des données dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Résumé: configurez et démontrez la classification et l’étiquetage des données à l’aide du client Azure information protection (AIP) dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: cf369894eb87381e3837a52946a0ba2b9705bf70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067932"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classification et étiquetage des données dans l’environnement de développement/test Office 365

 **Résumé:** Configurez et démontrez la classification et l’étiquetage des données à l’aide du client Azure information protection (AIP) dans votre environnement de développement/test Office 365.
  
Le client Azure information protection vous permet de classer un document avant de le télécharger dans un dossier SharePoint Online dans Office 365. Avec les instructions de cet article, vous installez le client Azure information protection et démontrez la classification des données. Pour plus d’informations, reportez-vous à [Azure information protection](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Cliquez sur[ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: créer votre environnement de développement/test Office 365

Suivez les instructions de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Phase 2: ajouter l’abonnement à la version d’évaluation d’Azure information protection

Dans cette phase, vous allez ajouter Azure information protection à votre environnement de développement/test Office 365 et l’activer pour vos comptes d’utilisateur. Si vous avez configuré l' [environnement de développement/test Office 365 et EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorez cette phase. L’abonnement à la version d’évaluation de Enterprise Mobility suite inclut des licences Azure information protection.
  
Tout d’abord, inscrivez-vous pour obtenir un abonnement à la version d’évaluation d’Azure information protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Inscription à un abonnement à la version d’évaluation d’Azure information protection

1. Dans Internet Explorer ou votre navigateur, accédez à [http://admin.microsoft.com](http://admin.microsoft.com) et connectez-vous à l’aide de votre compte d’administrateur général Office 365.
    
2. Dans l’onglet **Accueil Microsoft Office** , cliquez sur la vignette **administrateur** .
    
3. Dans l’onglet Office 365 admin, dans le volet de navigation de gauche, cliquez sur **facturation _GT_ acheter des services**.
    
4. Sur la page **acheter des services** , recherchez l’élément **Azure information protection Premium P2** . Placez le pointeur de la souris dessus, puis cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
Ensuite, vous activez la licence Azure information protection pour tous les comptes d’utilisateur.
  
1. Sous l’onglet Centre d’administration Microsoft 365, cliquez sur **utilisateurs**.
    
2.  Dans la liste des comptes d’utilisateur, sélectionnez votre compte d’administrateur général, puis cliquez sur **modifier** pour **licences de produits**.
    
3. Activez la licence de produit pour **Azure information protection Premium P2** sur **activé**, cliquez sur **enregistrer,** puis cliquez deux fois sur **Fermer** .
    
4. Répétez les étapes 2 et 3 pour vos autres comptes d’utilisateur (utilisateur 1 à utilisateur 5).
    
Votre environnement de développement/test Office 365 dispose désormais des éléments suivants:
  
- Les abonnements à la version d’évaluation d’Office 365 E5 entreprise et Azure information protection.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 E5 entreprise et Azure information protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Phase 3: faire la démonstration de la classification des données

Dans cette phase, vous démontrez la classification des données à l’aide du client Azure information protection et de la stratégie Azure information protection par défaut.
  
Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, vous devez d’abord installer Office 2016 sur CLIENT1.
  
1. Utilisez votre navigateur et accédez au [portail Azure](http://portal.azure.com).
    
2. Cliquez sur **groupes de ressources >** [nom de votre groupe de ressources] **_GT_ CLIENT1 > connecter**.
    
3. À partir de CLIENT1, exécutez Internet Explorer, accédez au portail Office [http://admin.microsoft.com](http://admin.microsoft.com)à, puis connectez-vous avec le nom de compte utilisateur 5 et le mot de passe.
    
4. Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Installer Office 2016**.
    
5. Exécutez le téléchargement lorsque vous y êtes invité, puis cliquez sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur. Patientez pendant l’installation d’Office. Lorsque vous avez terminé, cliquez deux fois sur **Fermer** .
    
Ensuite, installez le client Azure information protection.
  
1. Dans votre navigateur ou Internet Explorer, accédez à la [page de téléchargement de Microsoft Azure information protection](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Si vous utilisez la version légère de l’environnement de développement/test Office 365, utilisez le navigateur sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, exécutez Internet Explorer à partir de CLIENT1.
    
2. Sur la page téléchargement de **Microsoft Azure information protection** , cliquez sur **Télécharger**, sur **AzInfoProtection. exe**, puis sur **suivant**.
    
3. Lorsque vous y êtes invité, exécutez AzInfoProtection. exe.
    
4. Dans la zone **installer le client Azure information protection** , cliquez sur **J’accepte**, puis sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.
    
5. Dans la zone **terminé** , cliquez sur **Fermer.**
    
Ensuite, vous démontrez la classification des documents.
  
1. Cliquez sur l’icône **Word** dans la barre des tâches.
    
2. Lorsque vous y êtes invité, connectez-vous avec le nom de compte utilisateur 5 et le mot de passe.
    
3. Si vous venez d’installer Office 2016 sur CLIENT1, dans **** la première zone, cliquez sur **accepter**.
    
4. Cliquez sur **document vierge**. 
    
    Notez la section **protection** du ruban sous l’onglet **Accueil** et la ligne de classifications de documents.
    
5. Dans le document vide, tapez du texte.
    
6. Cliquez sur **fichier _GT_ enregistrer**, tapez le nom **BeforeAIP**, puis cliquez sur **OK**. 
    
7. Dans la ligne de classes de documents, cliquez sur la flèche vers le bas correspondant à la **clé secrète**, puis cliquez sur **toutes les sociétés**.
    
8. Cliquez sur **fichier _GT_ enregistrer sous**, tapez le nom **AfterAIP**, puis cliquez sur **OK**.
    
9. Cliquez sur **Explorateur de fichiers** dans la barre des tâches, puis ouvrez le dossier **documents** .
    
    Notez les différentes tailles de fichier des documents **BeforeAIP** et **AfterAIP** . Le document AfterAIP est plus volumineux, car il contient les informations de classification.
    
Ensuite, vous autorisez tout le monde à accéder à la collection de sites de support technique.
  
1. Dans l’onglet **Accueil Microsoft Office** , cliquez sur **SharePoint**.
    
2. Dans l’onglet **SharePoint** , cliquez sur **collection de sites de support**.
    
3. Dans le coin supérieur droit, cliquez sur l’icône des **paramètres** , puis cliquez sur **partagé avec**.
    
4. Dans **partager «collection de sites prise en charge»**, cliquez sur **avancé**.
    
5. Dans la liste des groupes SharePoint, cliquez sur membres de la **collection de sites support**.
    
6. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
7. Dans **partager «collection de sites prise en charge»**, tapez **tout le monde**, cliquez sur **tout le monde sauf les utilisateurs externes**, puis cliquez sur **partager.**
    
8. Fermez l’onglet **personnes et groupes** .
    
Ensuite, connectez-vous avec votre compte utilisateur 5 et téléchargez le document protégé par AIP dans le dossier Documents de la collection de sites de support.
  
1. Dans l’onglet **Accueil Microsoft Office** , dans l’angle supérieur droit, cliquez sur l’icône de l’utilisateur ****, puis cliquez sur Déconnexion.
    
2. Accédez à [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Sur la page **de connexion à Office 365** , cliquez sur le nom de compte utilisateur 5 et connectez-vous.
    
4. Dans l’onglet **Accueil Microsoft Office** , cliquez sur **collection de sites prise en charge de SharePoint >**.
    
5. Cliquez sur **documents**, sur **Télécharger**, sur le document **AfterAIP** , puis sur **ouvrir**.
    
    Vous devriez voir AfterAIP. docx dans le dossier Documents de la collection de sites prise en charge.
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Environnement de développement/test Office 365 et EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


