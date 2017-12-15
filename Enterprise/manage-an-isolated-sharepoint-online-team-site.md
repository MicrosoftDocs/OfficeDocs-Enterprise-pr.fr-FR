---
title: "Gestion d'un site d'équipe SharePoint Online isolé"
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
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "Résumé : Découvrez comment gérer votre site d'équipe SharePoint Online isolé."
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>Gestion d'un site d'équipe SharePoint Online isolé

 **Résumé :** Découvrez comment gérer votre site d'équipe SharePoint Online isolé.
  
Cet article vous explique comment gérer un site d'équipe SharePoint Online isolé.
  
## <a name="add-a-new-user"></a>Ajouter un nouvel utilisateur

Lorsqu'un nouvel utilisateur rejoint le site, vous devez choisir son niveau de participation :
  
- Administration : ajoutez le compte du nouvel utilisateur au groupe d'accès Administrateurs du site
    
- Collaboration active : ajoutez le compte de l'utilisateur au groupe d'accès Membres du site
    
- Consultation : ajoutez le compte de l'utilisateur au groupe d'accès Visiteurs du site
    
Si vous gérez des comptes d'utilisateur et des groupes via Windows Server Active Directory (AD), ajoutez les utilisateurs appropriés aux groupes d'accès appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.
  
Si vous gérez des comptes d'utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d'administration Office ou Microsoft PowerShell :
  
- Pour le Centre d'administration Office, connectez-vous avec un compte d'utilisateur ayant le rôle Administrateur des comptes d'utilisateur ou Administrateur d'entreprise et utilisez les groupes pour ajouter les utilisateurs appropriés aux groupes d'accès appropriés.
    
- Pour PowerShell, première [connexion avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218). Pour ajouter un compte d’utilisateur à un groupe d’accès avec son nom d’utilisateur principal (UPN), utilisez le bloc de commande PowerShell suivant :
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Pour un fichier texte qui contient toutes les commandes PowerShell et une feuille de calcul de configuration Excel qui génère des commandes PowerShell en fonction des noms de compte de vos utilisateurs et groupes, téléchargez le [kit de déploiement du site d'équipe SharePoint Online isolé](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 

Pour ajouter un compte d'utilisateur à un groupe d'accès en utilisant son nom d'affichage, exécutez le bloc de commandes PowerShell suivant :

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>Ajouter un nouveau groupe

Pour ajouter un accès à un groupe, vous devez choisir le niveau de participation de tous les membres du groupe sur le site :
  
- Administration : ajoutez le groupe d'utilisateurs au groupe d'accès Administrateurs du site
    
- Collaboration active : ajoutez le groupe d'utilisateurs au groupe d'accès Membres du site
    
- Consultation : ajoutez le groupe d'utilisateurs au groupe d'accès Visiteurs du site
    
Si vous gérez des comptes d'utilisateur et des groupes via Windows Server AD, ajoutez les groupes d'utilisateurs appropriés aux groupes appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.
  
Si vous gérez des comptes d'utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d'administration Office ou PowerShell :
  
- Pour le Centre d'administration Office, connectez-vous avec un compte d'utilisateur ayant le rôle Administrateur des comptes d'utilisateur ou Administrateur d'entreprise et utilisez les groupes pour ajouter les groupes d'utilisateurs appropriés aux groupes d'accès appropriés.
    
- Pour PowerShell, première [connexion avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218). Ensuite, utilisez les commandes PowerShell suivantes :
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>Supprimer un utilisateur

Lorsque l'accès d'un utilisateur doit être supprimé du site, supprimez-le du groupe d'accès dont il est membre en fonction de sa participation sur le site :
  
- Administration : supprimez le compte d'utilisateur du groupe d'accès Administrateurs du site
    
- Collaboration active : supprimez le compte d'utilisateur du groupe d'accès Membres du site
    
- Consultation : supprimez le compte d'utilisateur du groupe d'accès Visiteurs du site
    
Si vous gérez des comptes d'utilisateur et des groupes via Windows Server AD, supprimez les utilisateurs appropriés des groupes d'accès appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.
  
Si vous gérez des comptes d'utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d'administration Office ou PowerShell :
  
- Pour le Centre d'administration Office, connectez-vous avec un compte d'utilisateur ayant le rôle Administrateur des comptes d'utilisateur ou Administrateur d'entreprise et utilisez les groupes pour supprimer les utilisateurs appropriés des groupes d'accès appropriés.
    
- Pour PowerShell, première [connexion avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218). Pour supprimer un compte d’utilisateur d’un groupe d’accès avec son nom UPN, utilisez le bloc de commande PowerShell suivant :
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

Pour supprimer un compte d'utilisateur d'un groupe d'accès en utilisant son nom d'affichage, exécutez le bloc de commandes PowerShell suivant :
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>Supprimer un groupe

Pour supprimer l'accès d'un groupe, supprimez le groupe du groupe d'accès dont il est membre en fonction de sa participation sur le site :
  
- Administration : supprimez le groupe du groupe d'accès Administrateurs du site
    
- Collaboration active : supprimez le groupe du groupe d'accès Membres du site
    
- Consultation : supprimez le groupe du groupe d'accès Visiteurs du site
    
Si vous gérez des comptes d'utilisateur et des groupes via Windows Server Active Directory, supprimez les groupes appropriés des groupes d'accès appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.
  
Si vous gérez des comptes d'utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d'administration Office ou PowerShell :
  
- Pour le Centre d'administration Office, connectez-vous avec un compte d'utilisateur disposant du rôle Administrateur des comptes d'utilisateur ou Administrateur d'entreprise et utilisez les groupes pour supprimer les groupes appropriés des groupes d'accès appropriés.
    
- Pour PowerShell, consultez la rubrique [Se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).    
Pour supprimer un groupe d'un groupe d'accès en utilisant son nom d'affichage, exécutez le bloc de commandes PowerShell suivant :
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>Création d'un sous-dossier de documents avec des autorisations personnalisées

Il arrive que des utilisateurs travaillant dans un site isolé aient besoin d'un espace privé pour travailler en équipe. Pour les sites SharePoint Online, vous pouvez créer un sous-dossier dans le dossier Documents du site et affecter des autorisations personnalisées. Les personnes non autorisées ne verront pas ce sous-dossier.
  
Pour créer un sous-dossier de documents avec des autorisations personnalisées, procédez comme suit :
  
1. Connectez-vous à Office 365 avec un compte membre du groupe d'accès Administrateurs du site. Pour plus d'informations, consultez la rubrique [Se connecter à Office 365 pour les entreprises](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Accédez au site d'équipe isolé, puis cliquez sur **Documents**.
    
3. Accédez au dossier dans le dossier de documents qui contiendra le sous-dossier bénéficiant d'autorisations personnalisées, créez le dossier, puis ouvrez-le.
    
4. Cliquez sur **Partager**.
    
5. Cliquez sur **Partagé avec > Avancé**.
    
6. Cliquez sur **Arrêter l'héritage des autorisations**, puis cliquez sur **OK**.
    
7. Cliquez sur **Partager**.
    
8. Cliquez sur **Partagé avec > Avancé**.
    
9. Cliquez sur **Accorder des autorisations > Partagé avec > Avancé**.
    
10. Dans la page autorisations, cliquez sur ** \<nom du site > membres de la liste**.
    
11. Sur le ** \<nom du site > membres** page, activez la case à cocher en regard du groupe de l’accès de membres de site, cliquez sur **Actions**, cliquez sur **Supprimer les utilisateurs du groupe**et puis cliquez sur **OK**.
    
12. Pour ajouter des membres à ce sous-dossier, cliquez sur **Nouveau > Ajouter des utilisateurs**.
    
13. Dans la boîte de dialogue **Partager**, saisissez les noms des comptes d'utilisateur qui peuvent collaborer sur des fichiers du sous-dossier, puis cliquez sur **Partager**.
    
14. Actualisez la page web pour afficher les nouveaux résultats.
    
15. Sous **groupes** dans la navigation de gauche, cliquez sur le ** \<nom du site > visiteurs** de groupe et d’utiliser les étapes 11 à 14 pour spécifier le jeu de comptes d’utilisateurs qui peuvent afficher les fichiers dans le sous-dossier (le cas échéant).
    
16. Sous **groupes** dans la navigation de gauche, cliquez sur le ** \<nom du site > propriétaires** de groupe et d’utiliser les étapes 11 à 14 pour spécifier le jeu de comptes d’utilisateurs qui peuvent administrer les autorisations dans le sous-dossier (le cas échéant).
    
17. Fermez l'onglet **Utilisateurs et groupes** dans votre navigateur.
    
## <a name="see-also"></a>See Also

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md)
  
[Solutions de sécurité](security-solutions.md)

[Déploiement d'un site d'équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md)



