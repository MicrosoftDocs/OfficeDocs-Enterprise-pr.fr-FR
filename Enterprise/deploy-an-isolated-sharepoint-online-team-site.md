---
title: "Déploiement d’un site d’équipe SharePoint Online isolé"
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
- Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "Résumé : Déployer un nouveau site d’équipe de SharePoint Online isolé avec ces instructions pas à pas."
ms.openlocfilehash: b22f9bd6ca5562f6c9632709d8afb54cd7b8d634
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>Déploiement d’un site d’équipe SharePoint Online isolé

 **Résumé :** Déployer un nouveau site d’équipe de SharePoint Online isolé avec ces instructions pas à pas.
  
Cet article est un guide de déploiement détaillé pour créer et configurer un site d’équipe SharePoint Online isolé dans Microsoft Office 365. Pour cela, vous devez utiliser les trois groupes SharePoint par défaut et les niveaux d’autorisation correspondants (un groupe d’accès Azure Active Directory (AD) pour chaque niveau d’accès).
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>Phase 1 : Créer et remplir les groupes d’accès site équipe

Au cours de cette phase, vous allez créer les trois groupes d’accès basés sur Azure AD pour les trois groupes SharePoint par défaut et les remplir avec les comptes d’utilisateur appropriés.
  
> [!NOTE]
> Pour réaliser les étapes suivantes, vous devez avoir créé tous les comptes d’utilisateur nécessaires et leur avoir affecté les licences appropriées. Dans le cas contraire, ajoutez-les et attribuez-leur des licences avant de passer à l’étape 1. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>Étape 1 : liste des administrateurs SharePoint Online du site

Choisissez les comptes d’utilisateur des administrateurs SharePoint Online pour le site d’équipe isolé.
  
Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser Windows PowerShell, dressez une liste de leurs noms d’utilisateur principaux (UPN) (exemple d’UPN : belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>Étape 2 : liste des membres du site

Choisissez les comptes d’utilisateur des membres du site d’équipe isolé, c’est-à-dire ceux qui collaboreront sur les ressources stockées sur le site.
  
Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser PowerShell, dressez une liste de leurs UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>Étape 3 : liste des visiteurs du site

Choisissez les comptes d’utilisateur des visiteurs du site d’équipe isolé, c’est-à-dire ceux qui peuvent afficher les ressources stockées sur le site sans pouvoir les modifier ou collaborer directement sur leur contenu.
  
Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser PowerShell, dressez une liste de leurs UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.
  
Les visiteurs du site peuvent comprendre des membres de l’équipe de direction, du service juridique ou de plusieurs services.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>Étape 4 : création des trois groupes d’accès du site dans Azure AD

Vous devez créer les groupes d’accès suivants dans Azure AD :
  
- Administrateurs du site (qui contient la liste de l’étape 1)
    
- Membres du site (qui contient la liste de l’étape 2)
    
- Visiteurs du site (qui contient la liste de l’étape 3)
    
1. Dans votre navigateur, accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com) et connectez-vous avec les informations d’identification d’un compte qui a été affectée avec le rôle de l’administrateur de gestion d’utilisateur ou l’administrateur de la société.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > utilisateurs et groupes > tous les groupes de**.
    
3. Sur la lame de **tous les groupes** , cliquez sur **+ le nouveau groupe**.
    
4. Sur la lame de **groupe** :
    
  - Dans la zone **nom**, tapez le nom du groupe.
    
  - Sélectionnez **affecté** dans **l’appartenance**.
    
  - Cliquez sur **Oui** pour **activer Office fonctionnalités**.
    
5. Cliquez sur **créer**, puis fermez la lame du **groupe** .
    
6. Répétez les étapes 3 à 5 pour les autres groupes.
    
> [!NOTE]
> Vous devez utiliser le portail Azure pour créer les groupes afin qu’ils aient les fonctionnalités d’Office. Si un site isolé SharePoint Online est ultérieurement configuré comme un site hautement confidentielles avec une étiquette de Protection d’informations Azure (AIP) pour crypter des fichiers et affecter des autorisations à des groupes spécifiques, les groupes autorisés doivent avoir été créés avec les fonctionnalités de Office activé. Vous ne pouvez pas modifier le paramètre de fonctionnalités Office d’un groupe d’annonces Azure après que qu’il a été créé. 
  
Voici votre configuration obtenue avec les groupes d’accès de trois sites.
  
![Trois groupes d’accès pour le déploiement d’un site SharePoint Online isolé.](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>Étape 5. Ajouter les comptes d’utilisateurs aux groupes d’accès

Procédez comme suit :
  
1. Ajoutez la liste des utilisateurs de l’étape 1 au groupe d’accès Administrateurs du site
    
2. Ajoutez la liste des utilisateurs de l’étape 2 au groupe d’accès Membres du site
    
3. Ajoutez la liste des utilisateurs de l’étape 3 au groupe d’accès Visiteurs du site
    
Si vous gérez des comptes d’utilisateur et des groupes via Windows Server AD, ajoutez les utilisateurs aux groupes d’accès appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.
  
Si vous gérez des comptes d’utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d’administration Office ou PowerShell. Si plusieurs groupes d’accès portent le même nom, utilisez le Centre d’administration Office.
  
Pour le centre d’administration d’Office, connectez-vous avec un compte d’utilisateur qui vous a été attribué le rôle d’administrateur de compte d’utilisateur ou l’administrateur de la société et d’utiliser des groupes pour ajouter les comptes d’utilisateur et des groupes aux groupes d’accès approprié.
  
Pour PowerShell, consultez la rubrique [Se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Ensuite, utilisez le bloc de commandes suivant pour ajouter un compte d’utilisateur à un groupe d’accès :
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Pour un fichier texte qui contient toutes les commandes PowerShell et une feuille de calcul de configuration Excel qui génère des commandes PowerShell en fonction des noms de compte de vos utilisateurs et groupes, téléchargez le [kit de déploiement du site d'équipe SharePoint Online isolé](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 
  
Si vous avez stocké les UPN des comptes d’utilisateur des groupes d’accès dans un fichier texte, vous pouvez exécuter le bloc de commandes PowerShell suivant pour les ajouter tous en même temps :
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

De PowerShell, utiliser le bloc de commandes suivant pour ajouter un groupe à un groupe d’accès :
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

Voici les résultats que vous devriez obtenir :
  
- Le groupe d’annonces Azure d’Administrateurs du site contient les comptes d’utilisateur de site admin ou les groupes
    
- Le groupe d’annonces Azure de membres site contient les comptes d’utilisateurs de membres de site ou les groupes
    
- Le groupe d’utilisateurs AD Azure site contient les comptes d’utilisateurs ou les groupes qui peuvent uniquement afficher le contenu du site
    
Validez la liste des membres de chaque groupe d’accès avec le Centre d’administration Office ou le bloc de commandes PowerShell suivant :
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

Voici votre configuration obtenue avec les groupes d’accès de trois sites rempli avec des comptes d’utilisateurs ou de groupes.
  
![Les trois groupes d’accès renseignés avec les comptes d’utilisateurs.](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>Phase 2 : création et configuration du site d’équipe isolé

Au cours de cette phase, vous allez créer le site SharePoint Online isolé et configurer les niveaux d’autorisation SharePoint Online par défaut pour utiliser vos nouveaux groupes d’accès Azure AD.
  
Commencez par créer le site d’équipe SharePoint Online en suivant ces étapes.
  
1. Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des mosaïques, cliquez sur **SharePoint**.
    
3. Dans le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ créer le site**.
    
4. Dans la page **créer un site** , cliquez sur **site d’équipe**.
    
5. Dans la zone **nom du Site**, tapez un nom pour le site d’équipe. 
    
6. Dans la **description de site d’équipe,** tapez une description facultative de l’objectif de votre site.
    
7. Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
    
8. Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.
    
Ensuite, dans le nouveau site d’équipe SharePoint Online, configurez les autorisations.
  
1. Dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.
    
2. Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.
    
3. Dans l’onglet **autorisations** de nouveau de votre navigateur, cliquez sur **Paramètres de demande d’accès**.
    
4. Dans la boîte de dialogue **Paramètres de demandes d’accès** , désactivez **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les demandes d’accès** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur **OK**.
    
5. Dans l’onglet **autorisations** de votre navigateur, cliquez sur ** \<nom du site > membres** dans la liste.
    
6. **Personnes et groupes**, cliquez sur **Nouveau**.
    
7. Dans la boîte de dialogue de **partage** , tapez le nom du groupe accès aux membres de site, sélectionnez-le, puis cliquez sur **partage**.
    
8. Cliquez sur le bouton de retour de votre navigateur.
    
9. Cliquez sur ** \<nom du site > propriétaires** dans la liste.
    
10. **Personnes et groupes**, cliquez sur **Nouveau**.
    
11. Dans la boîte de dialogue de **partage** , tapez le nom du groupe d’accès admins du site, sélectionnez-le, puis cliquez sur **partage**.
    
12. Cliquez sur le bouton de retour de votre navigateur.
    
13. Cliquez sur ** \<nom du site > visiteurs** dans la liste.
    
14. **Personnes et groupes**, cliquez sur **Nouveau**.
    
15. Dans la boîte de dialogue de **partage** , tapez le nom du groupe d’accès site visionneuses, sélectionnez-le, puis cliquez sur **partage**.
    
16. Fermez l’onglet **autorisations** de votre navigateur.
    
Voici les résultats que vous devez escompter :
  
- La ** \<nom du site > propriétaires** groupe SharePoint contient le groupe Administrateurs de l’accès, dans laquelle tous les membres ont le niveau d’autorisation **contrôle total** .
    
- La ** \<nom du site > membres** groupe SharePoint contient le groupe membres de l’accès, dans lequel tous les membres ont le niveau d’autorisation **Modifier** .
    
- La ** \<nom du site > visiteurs** groupe SharePoint contient le groupe d’accès site visionneuses, dans lequel tous les membres ont le niveau d’autorisation **lecture** .
    
- La possibilité pour les membres à inviter d’autres membres ou pour les non-membres demander l’accès est désactivée.
    
Voici votre configuration obtenue avec les trois groupes SharePoint pour le site configuré pour utiliser les trois groupes d’accès, qui sont remplis avec des comptes d’utilisateurs ou les groupes d’annonces Azure.
  
![Configuration finale de votre site SharePoint Online isolé avec des comptes d’utilisateurs et groupes d’accès.](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
Comme vous êtes membres de l’un des groupes d’accès, vous et les membres du site pouvez désormais collaborer sur les ressources du site.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous devez modifier l’appartenance au groupe de site access ou créer un dossier de documents avec des autorisations personnalisées, consultez [Gestion d’un site d’équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Voir aussi

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md)
  
[Gestion d'un site d'équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)
  
[Solutions de sécurité](security-solutions.md)



