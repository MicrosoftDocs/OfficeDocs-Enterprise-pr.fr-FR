---
title: Environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Résumé : Utilisez ce guide de laboratoire de test pour créer un abonnement d’évaluation Office 365 à des fins d’évaluation ou de développement/test.'
ms.openlocfilehash: 7a7b12038acf914667655decee52993286faab1e
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573998"
---
# <a name="office-365-devtest-environment"></a>Environnement de développement/test Office 365

 **Résumé :** Utilisez ce guide de laboratoire de test pour créer un abonnement d’évaluation Office 365 à des fins d’évaluation ou de développement/test.
  
Vous pouvez utiliser un abonnement d’évaluation Office 365 et créer un environnement de développement/test Office 365 pour les applications ou faire une démonstration des fonctionnalités d’Office 365. Deux versions sont disponibles :
  
- L’environnement de développement/test Office 365 léger se compose d’un abonnement d’évaluation Office 365 auquel vous accédez depuis votre ordinateur principal.
    
    Utilisez cet environnement lorsque vous voulez montrer rapidement une fonctionnalité. Pour l’environnement de développement/test Office 365 léger, suivez uniquement les instructions des phases 2 et 3 de cet article.
    
- L’environnement de développement/test Office 365 d’entreprise simulé comprend un abonnement d’évaluation Office 365 et un intranet d’organisation simplifié connecté à Internet, qui est hébergé dans les services d’infrastructure de Microsoft Azure. Vous pouvez créer cette configuration entièrement dans le cloud de Microsoft.
    
    Utilisez cet environnement lorsque vous voulez montrer une fonctionnalité ou une application dans un environnement semblable à un réseau d’entreprise classique connecté à Internet, ou pour les fonctionnalités pour lesquelles ce type d’environnement est nécessaire. Pour l’environnement de développement/test Office 365 d’entreprise simulé, suivez les instructions des phases 1, 2 et 3 de cet article.
    
> [!NOTE]
> Nous vous recommandons d’imprimer cet article afin de consigner les valeurs spécifiques dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement à la version d’évaluation pour 30 jours de plus. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un petit nombre de licences. 
  
![Guides de laboratoire de test dans Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Phase 1 : création de la configuration de base dans Azure

Suivez les instructions de la rubrique [Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md).
  
Vous devez posséder un abonnement Azure. Vous pouvez utiliser le [Compte gratuit Azure](https://azure.microsoft.com/pricing/free-trial/) pour cette configuration. Si vous avez un abonnement MSDN ou Visual Studio, reportez-vous à l’article [Crédit Azure mensuel pour les abonnés Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Voici la configuration obtenue.
  
![Environnement de développement/test de configuration de base dans Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
Cette configuration se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Phase 2 : création d’un abonnement d’évaluation Office 365

Pour démarrer votre abonnement d’évaluation Office 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.
  
1. Nous vous recommandons d’utiliser une variante du nom d’entreprise Contoso pour le nom de votre entreprise. Il s’agit d’une entreprise fictive utilisée dans le contenu d’exemple de Microsoft. Toutefois, cette étape n’est pas obligatoire. Indiquer le nom fictif de votre entreprise ici : ![](./media/Common-Images/TableLine.png)
    
2. Pour ouvrir un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créez un compte avec un nouveau compte de messagerie et une nouvelle adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.
    
  - Indiquer le prénom et le nom de famille utilisés pour votre nouveau compte ici : ![](./media/Common-Images/TableLine.png)
    
  - Indiquer l’adresse du nouveau compte de messagerie ici : ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscription à un abonnement d’évaluation Office 365 E5

1. Pour l’environnement de développement/test Office 365 léger, ouvrez le navigateur Internet sur votre ordinateur et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial). 
    
    Pour l’environnement de développement/test Office 365 d’entreprise simulé, connectez-vous à CLIENT1 avec le compte CORP\Utilisateur1 à partir du portail Azure.

    Dans l’écran d’accueil, exécutez Microsoft Edge et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Sur la page **Bienvenue, nous allons faire connaissance**, indiquez les informations suivantes :
    
  - votre emplacement physique ;
    
  - le prénom et le nom utilisés pour votre nouveau compte Microsoft ;
    
  - votre nouvelle adresse de compte de messagerie ;
    
  - un numéro de téléphone professionnel ;
    
  - le nom de votre entreprise fictive ;
    
  - la taille de votre entreprise (250 à 999 personnes).
    
3. Cliquez sur **Encore une dernière étape**.
    
4. Sur la page **Créer votre identifiant utilisateur**, entrez un nom d’utilisateur dérivé de votre nouvelle adresse de messagerie, le nom de votre entreprise fictive après le signe @ (supprimez tous les espaces dans le nom), puis un mot de passe (deux fois) pour ce nouveau compte Office 365. 
    
    Enregistrez le mot de passe saisi dans un emplacement sécurisé.
    
    Enregistrez le nom de votre entreprise fictive, ou **nom de l’organisation**, ici : ![](./media/Common-Images/TableLine.png)
    
5. Cliquez sur **Créer mon compte**.
    
6. Sur la page **Prouvez que vous n’êtes pas un robot.**, tapez le numéro de votre téléphone compatible avec du texte, puis cliquez sur **M’envoyer un SMS**.
    
7. Saisissez le code de vérification qui vous été envoyé par message, puis cliquez sur **Suivant**.
    
8. Enregistrez l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ![](./media/Common-Images/TableLine.png)
    
9. Enregistrez l’identifiant utilisateur ici (sélectionnez-le et copiez-le) : ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Cette valeur correspond au **nom de l’administrateur général Office 365**.
    
10. Cliquez sur le lien **Nous sommes prêts** lorsqu’il s’affiche.
    
11. Sur la page suivante, attendez qu’Office 365 termine la configuration et que tous les titres soient visibles.
    
Vous devriez voir la page principale du portail Office 365 à partir de laquelle vous pouvez accéder aux services Office Online et au Centre d’administration Microsoft 365.
  
Pour l’environnement de développement/test Office 365 d’entreprise simulé, voici la configuration que vous obtenez.
  
![Environnement de développement/test Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Cette configuration se compose des éléments suivants :  
  
- les machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure ;
    
- un abonnement d’évaluation Office 365 E5.
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Phase 3 : configuration de votre abonnement d’évaluation Office 365

Au cours de cette phase, vous allez configurer votre abonnement Office 365 en y ajoutant des sites d’équipes SharePoint Online et des utilisateurs supplémentaires.
  
Toute d’abord, ajoutez quatre nouveaux utilisateurs et attribuez-leur des licences E5.
  
Utilisez les instructions de l’article [Se connecter à Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) pour installer les modules PowerShell et vous connecter à votre nouvel abonnement Office 365 à partir de :
  
- Votre ordinateur (pour l’environnement de développement/test Office 365 léger).
    
- La machine virtuelle CLIENT1 (pour l’environnement de développement/test Office 365 d’entreprise simulé).
    
 Dans la boîte de dialogue Demande d’informations d’identification Windows PowerShell, saisissez le nom de l’administrateur général Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, puis exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 2 et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 3 et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 4 et enregistrez-le dans un emplacement sécurisé.
  
Exécutez les commandes suivantes à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Dans la zone de la commande **New-MsolUser**, notez le mot de passe généré pour le compte Utilisateur 5 et enregistrez-le dans un emplacement sécurisé.
  
Ensuite, créez trois nouveaux sites d’équipes SharePoint Online pour les services Ventes, Production et Support.
  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>Phase 4: Création de trois nouveaux sites d’équipes SharePoint Online (Optionnel)

Dans cette phase, vous configurez un ensemble de sites d’équipe SharePoint Online.
  
1. Installez [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la version x64).
    
2. Cliquez sur **Démarrer**, saisissez **sharepoint**, puis cliquez sur **SharePoint Online Management Shell**.
    
3. Indiquez le nom de votre organisation (exemple : contosotoycompany), puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell pour vous connecter au service SharePoint Online.
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. Dans la boîte de dialogue **Microsoft SharePoint Online Management Shell**, saisissez le nom de l’administrateur général Office 365 (par exemple, jdoe@contosotoycompany.onmicrosoft.com) et son mot de passe, puis cliquez sur **Se connecter**.
    
5. Pour créer trois nouveaux sites d’équipes (Ventes, Production et Support), indiquez le nom de l’administrateur général Office 365, puis exécutez les commandes suivantes à partir de l’invite SharePoint Online Management Shell :
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. Exécutez cette commande pour répertorier les URL de ces nouveaux sites :
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. Dans Internet Explorer, entrez l’URL du site Production pour afficher le site d’équipe SharePoint Online par défaut pour le service Production.
    
## <a name="record-values-for-future-reference"></a>Enregistrez les valeurs, vous en aurez besoin plus tard.

Enregistrez ces valeurs pour utiliser ou déployer les guides de laboratoire de test dans cet environnement de test :
  
- Nom de l’administrateur général Office 365 : ![](./media/Common-Images/TableLine.png).onmicrosoft.com (indiqué à l’étape 9 de la phase 2)
    
    Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.
    
- Nom de l’organisation de l’abonnement d’évaluation : ![](./media/Common-Images/TableLine.png) (indiqué à l’étape 4 de la phase 2)
    
- Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Enregistrez les noms de compte ici :
    
  - Nom du compte Utilisateur 2 : user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 3 : user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 4 : user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 5 : user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Enregistrez également les mots de passe de ces comptes dans un emplacement sécurisé.
    
- Pour répertorier les URL des sites d’équipes Ventes, Production et Support, exécutez la commande suivante à partir de l’invite SharePoint Online Management Shell :
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - URL du site Production : https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - URL du site Ventes : https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - URL du site Support : https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>Étapes suivantes

Utilisez ces articles supplémentaires dans votre environnement de développement/test Office 365 :
  
- [Synchronisation d’annuaires pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Authentification multifacteur pour votre environnement de développement/test Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Sécurité des applications cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Protection avancée contre les menaces pour votre environnement de développement/test Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Advanced eDiscovery pour votre environnement de développement/test Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Protection des fichiers sensibles dans l’environnement de développement/test Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Site d’équipe SharePoint Online isolé dans votre environnement de développement/test Office 365](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Classification et étiquetage des données dans l’environnement de développement/test Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
Étendez votre environnement de développement/test Office 365 afin d’y inclure des offres cloud supplémentaires de Microsoft :
  
- [Environnement de développement/test Microsoft 365 Entreprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>Voir aussi

- [Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
- [Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)


