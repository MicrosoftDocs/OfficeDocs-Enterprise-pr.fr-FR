---
title: Classification et étiquetage des données dans l’environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
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
description: Résumé :Configurer et démontrer la classification et l’étiquetage de données à l’aide du client Azure Information Protection (AIP) dans votre environnement de développement/test Office 365.
ms.openlocfilehash: 69526f8bf0ae0b6cc7509653cfaa72581e10dbfe
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897437"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classification et étiquetage des données dans l’environnement de développement/test Office 365

 **Résumé :** Configurer et démontrer la classification et l’étiquetage de données à l’aide du client Azure Information Protection (AIP) dans votre environnement de développement/test Office 365.
  
Le client de la Protection des informations Azure vous permet de classer un document avant de le télécharger vers un dossier SharePoint Online dans Office 365. Avec les instructions de cet article, vous installez le client de la Protection des informations Azure et démontrer la classification des données. Pour plus d’informations, voir [La Protection des informations Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1 : créer votre environnement de développement/test Office 365

Suivez les instructions de la rubrique [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Phase 2 : ajouter l’abonnement à la version d’évaluation Azure Information Protection

Dans cette phase, vous ajoutez Azure Information Protection à votre environnement de développement/test Office 365 et l’activez pour vos comptes d’utilisateurs. Si vous avez configuré l’[Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorez cette phase. L’abonnement à la version d’évaluation Enterprise Mobility Suite inclut des licences Azure Information Protection.
  
Tout d’abord, souscrivez un abonnement à la version d’évaluation Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Souscrire à un abonnement à la version d’évaluation Azure Information Protection

1. Dans Internet Explorer ou votre navigateur, accédez à [http://portal.office.com](http://portal.office.com) et connectez-vous avec votre compte d’administrateur général Office 365.
    
2. Dans l’onglet **Accueil Microsoft Office**, cliquez sur la mosaïque **Admin**.
    
3. Sous l’onglet Admin d’Office 365, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Azure Information Protection Premium P2**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
Ensuite, vous activez la licence de Azure Information Protection pour tous les comptes d’utilisateur.
  
1. 	Sous l’onglet Centre d’administrateur Office 365, cliquez sur **Utilisateurs**.
    
2.   Dans la liste des comptes d’utilisateur, sélectionnez votre compte d’administrateur global, puis cliquez sur **Modifier** pour **Licences de produits**.
    
3. 	Réglez la licence de produit pour **Azure Information Protection Premium P2** sur **Activé**, cliquez sur **Enregistrer**, puis sur **Fermer** à deux reprises.
    
4. Répétez les étapes 2 et 3 pour d’autres comptes d’utilisateur (Utilisateur 1 à Utilisateur 5).
    
Votre environnement de développement/test Office 365 comprend désormais :
  
- Abonnements à la version d’évaluation d’Office 365 E5 Entreprise et Azure Information Protection.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Phase 3 : démontrer la classification des données

Lors de cette phase, vous démontrez la classification des données à l’aide du client Azure Information Protection et de la stratégie Azure Information Protection par défaut.
  
Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, vous devez tout d’abord installer Office 2016 sur CLIENT1.
  
1. Utilisez votre navigateur et accédez au [portail Azure](http://portal.azure.com).
    
2. 	Cliquez sur **Groupes de ressources >** [nom de votre groupe de ressources] **> CLIENT1 > Se connecter**.
    
3. À partir de CLIENT1, exécutez Internet Explorer, accédez au portail Office à [http://portal.office.com](http://portal.office.com), puis connectez-vous avec le nom du compte User5 et le mot de passe.
    
4. Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Installer Office 2016**.
    
5. 	Exécutez le fichier téléchargé lorsque vous y êtes invité, puis cliquez sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur. Patientez pendant l’installation d’Office. Lorsque vous avez terminé, cliquez sur **Fermer** à deux reprises.
    
Ensuite, installez le client Azure Information Protection.
  
1. Dans votre navigateur ou Internet Explorer, accédez à la [page de téléchargement Microsoft Azure la Protection des informations](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Si vous utilisez la version légère de l’environnement de développement/test Office 365, utilisez le navigateur sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 de l’entreprise simulée, exécutez Internet Explorer à partir de CLIENT1.
    
2. Sur la page de téléchargement **Microsoft Azure Information Protection**, cliquez sur **Télécharger**, sur **AzInfoProtection.exe**, puis sur **Suivant**.
    
3. Lorsque vous y êtes invité, exécutez AzInfoProtection.exe.
    
4. Dans la zone client **Installer Azure Information Protection**, cliquez sur **J’accepte**, puis sur **Oui** lorsque vous y êtes invité par le contrôle de compte d’utilisateur.
    
5. Dans la zone **Terminé avec succès** , cliquez sur **Fermer.**
    
Ensuite, démontrez la classification des documents.
  
1. Cliquez sur l’icône **Word** dans la barre des tâches.
    
2. Lorsque vous y êtes invité, connectez-vous avec le nom de compte Utilisateur 5 et le mot de passe associé.
    
3. Si vous venez d’installer Office 2016 sur CLIENT1, dans la zone **Commençons par le début** , cliquez sur **Accepter**.
    
4. Cliquez sur **Document vierge**.  
    
    Notez la section **Protection** du ruban dans l’onglet **Accueil** et la ligne des classifications de document.
    
5. Dans le document vierge, tapez du texte.
    
6. Cliquez sur **Fichier > Enregistrer**, tapez le nom **BeforeAIP**, puis cliquez sur **OK**.  
    
7. Sur la ligne de classes de documents, cliquez sur la flèche vers le bas pour **Secret**, puis cliquez sur **Toute l’entreprise**.
    
8. Cliquez sur **Fichier > Enregistrer sous**, tapez le nom **AfterAIP**, puis cliquez sur **OK**.
    
9. Cliquez sur l’**Explorateur de fichiers** dans la barre des tâches, puis ouvrez le dossier **Documents**.
    
    Notez les tailles de fichier différent des documents **BeforeAIP** et **AfterAIP** . Le document AfterAIP est plus importante car elle contient les informations de classification.
    
Ensuite, autorisez tout le monde à accéder à la collection de sites Prise en charge.
  
1. 	Dans l’onglet **Accueil Microsoft Office**, cliquez sur **SharePoint**.
    
2. Dans l’onglet **SharePoint**, cliquez sur **Collection de sites Prise en charge**.
    
3. Dans le coin supérieur droit, cliquez sur l’icône **Paramètres**, puis cliquez sur **Partagé avec**.
    
4. Dans **partage de « Collection de sites de prise en charge »**, cliquez sur **Avancé**.
    
5. Dans la liste des groupes SharePoint, cliquez sur **Membres de la collection de sites Prise en charge**.
    
6. Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.
    
7. Dans **partage de « Collection de sites de prise en charge »**, tapez **tout le monde**, cliquez sur **tout le monde, à l’exception des utilisateurs externes**, puis cliquez sur **partager.**
    
8. Fermez l’onglet **Personnes et groupes**.
    
Ensuite, connectez-vous avec votre compte Utilisateur 5 et chargez le document protégé par AIP dans le dossier Documents de la collection de sites Prise en charge.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.
    
2. Accédez à [http://portal.office.com](http://portal.office.com).
    
3. Dans la page **Office 365 se connecter** , cliquez sur le nom du compte User5 et se connecter.
    
4. Dans l’onglet **Accueil Microsoft Office**, cliquez sur **SharePoint > Collection de sites Prise en charge**.
    
5. Cliquez sur **Documents**, sur **Charger**, sur le document **AfterAIP**, puis sur **Ouvrir**.
    
    Vous devriez voir AfterAIP.docx dans le dossier Documents de la collection de sites Prise en charge.
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Environnement de développement/test Office 365 et EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


