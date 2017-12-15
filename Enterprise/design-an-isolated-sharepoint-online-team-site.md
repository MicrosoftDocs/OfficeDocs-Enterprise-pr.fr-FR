---
title: "Conception d’un site d’équipe SharePoint Online isolé"
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
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "Résumé : L’étape dans le processus de conception pour les sites d’équipe SharePoint Online isolés."
ms.openlocfilehash: 343872ef7a41b40a87454da27ddccc4530ffe2eb
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>Conception d’un site d’équipe SharePoint Online isolé

 **Résumé :** Parcourez le processus de conception pour les sites d’équipe SharePoint Online isolés.
  
Cet article vous aide à faire les bons choix de conception avant de créer un site d’équipe SharePoint Online isolé.
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>Phase 1 : choix des groupes SharePoint et des niveaux d’autorisation

Chaque site d’équipe SharePoint Online par défaut est créé avec les groupes SharePoint suivants :
  
- \<nom du site > membres
    
- \<nom du site > les visiteurs
    
- \<nom du site > propriétaires
    
Ces groupes sont différents des groupes Office 365 et Azure Active Directory (AD), et permettent d’attribuer des autorisations pour l’utilisation des ressources du site.
  
L’ensemble des autorisations qui déterminent ce que le membre d’un groupe SharePoint peut faire dans un site est un niveau d’autorisation. Il existe trois niveaux d’autorisation par défaut pour un site d’équipe SharePoint Online : Modification, Lecture et Contrôle total. Le tableau suivant indique la corrélation par défaut des groupes SharePoint et les niveaux d’autorisation affectés :
  
|**Groupe SharePoint**|**Niveau d'autorisation**|
|:-----|:-----|
|\<nom du site > membres  <br/> |Modification  <br/> |
|\<nom du site > les visiteurs  <br/> |Lecture  <br/> |
|\<nom du site > propriétaires  <br/> |Contrôle total  <br/> |
   
 **Meilleures pratiques :** Vous pouvez créer d’autres groupes SharePoint et les niveaux d’autorisation. Toutefois, nous recommandons à l’aide des groupes SharePoint par défaut et les niveaux d’autorisation de votre site SharePoint Online isolé.
  
Voici les niveaux d’autorisation des groupes SharePoint par défaut.
  
![Groupes SharePoint par défaut et niveaux d’autorisation pour un site SharePoint Online.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>Phase 2 : attribution des autorisations aux utilisateurs membres de groupes d’accès

Vous pouvez attribuer des autorisations aux utilisateurs en ajoutant leur compte d’utilisateur, ou un groupe Office 365 ou Azure AD dont est membre le compte d’utilisateur, aux groupes SharePoint. Une fois ajoutés, les comptes d’utilisateur Office 365 reçoivent, directement ou indirectement via l’appartenance à un groupe Office 365 ou Azure AD, le niveau d’autorisation associé au groupe SharePoint.
  
En prenant l’exemple des groupes SharePoint par défaut :
  
- Les membres de la ** \<nom du site > membres** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et de groupes, sont affectés le niveau d’autorisation **Modifier**
    
- Les membres de la ** \<nom du site > visiteurs** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et de groupes, sont affectées des autorisations de niveau **lecture**
    
- Les membres de la ** \<nom du site > propriétaires** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et de groupes, sont affectés le niveau d’autorisation **contrôle total**
    
 **Meilleures pratiques :** Bien que vous pouvez gérer les autorisations par le biais de comptes d’utilisateurs individuels, nous vous conseillons d’utiliser un seul groupe d’annonces Azure connue sous la forme d’un groupe d’accès, à la place. Cela simplifie la gestion des autorisations par le biais de l’appartenance au groupe d’accès, plutôt que de gérer la liste des utilisateurs de comptes pour chaque groupe SharePoint.
  
Les groupes d’annonces Azure pour Office 365 sont différents des groupes d’Office 365. Les groupes d’annonces Azure apparaissent dans le centre d’administration d’Office avec leur jeu de **Type** à la **sécurité** et n’ont pas une adresse de messagerie. Les groupes d’annonces Azure peuvent être gérés dans :
  
- Windows Server Active Directory (AD)
    
    Il s’agit de groupes qui ont été créés dans votre infrastructure de Windows Server, Active Directory sur site et synchronisés avec votre abonnement à Office 365. Dans le centre d’administration d’Office, ces groupes ont un **statut** **Synched avec active directory**.
    
- Office 365
    
    Il s’agit de groupes qui ont été créés avec le centre d’administration d’Office, le portail Azure ou Microsoft PowerShell. Dans le centre d’administration d’Office, ces groupes ont un **statut** de **nuage**.
    
 **Meilleures pratiques :** Si vous utilisez Windows Server Active Directory sur site et la synchronisation avec votre abonnement à Office 365, votre utilisateur et la gestion de groupe dans Windows Server Active Directory.
  
Pour les sites d’équipe SharePoint Online isolés, voici à quoi ressemble la structure recommandée du groupe :
  
|**Groupe SharePoint**|**Groupe d’accès AD Azure**|**Niveau d'autorisation**|
|:-----|:-----|:-----|
|\<nom du site > membres  <br/> |\<nom du site > membres  <br/> |Modification  <br/> |
|\<nom du site > les visiteurs  <br/> |\<nom du site > visionneuses  <br/> |Lecture  <br/> |
|\<nom du site > propriétaires  <br/> |\<nom du site > Admins  <br/> |Contrôle total  <br/> |
   
 **Meilleures pratiques :** Vous pouvez utiliser Office 365 ou publicité Azure groupes en tant que membres des groupes SharePoint, nous vous conseillons d’utiliser les groupes d’annonces Azure. Les groupes d’annonces Azure, gérés par le biais d’Active Directory du serveur Windows ou d’Office 365, vous donnent plus de flexibilité pour utiliser des groupes imbriqués pour affecter des autorisations.
  
Voici la valeur par défaut configurés pour utiliser des groupes d’accès AD Azure des groupes SharePoint.
  
![Utilisation des groupes d’accès en tant que membres des groupes de sites SharePoint Online par défaut.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
Lorsque vous concevez les trois groupes d’accès, rappelez-vous de ceci :
  
- Il convient que quelques membres de la ** \<nom du site > Admins** groupe d’accès, correspondant à un nombre restreint d’administrateurs de SharePoint Online qui gèrent le site d’équipe.
    
- La plupart des membres de votre site sont dans le ** \<nom du site > membres** ou ** \<nom du site > visionneuses** accéder aux groupes. Étant donné que site des membres dans le ** \<nom du site > membres** groupe accès ont la possibilité de supprimer ou de modifier les ressources dans le site, de son appartenance avec soin. En cas de doute, ajouter le membre de site pour le ** \<nom du site > visionneuses** groupe d’accès.
    
Voici un exemple des groupes SharePoint et les groupes d’accès pour un site isolé nommé ProjectX.
  
![Exemple d’utilisation des groupes d’accès pour un site SharePoint Online nommé ProjectX.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>Phase 3 : Utilisez les groupes d’annonces Azure

Pour un projet est limité à un petit nombre de personnes, un seul niveau de groupes d’accès AD Azure ajoutés aux groupes du site SharePoint peut contenir la plupart des scénarios. Toutefois, si vous avez un grand nombre de personnes et aux personnes qui sont déjà membres d’établi des groupes d’annonces d’Azure, vous pouvez affecter plus facilement les autorisations SharePoint à l’aide de groupes imbriqués ou des groupes qui contiennent d’autres groupes en tant que membres.
  
Par exemple, vous souhaitez créer un site d’équipe SharePoint Online isolé pour favoriser la collaboration entre les responsables des services ventes, marketing, ingénierie, juridique et support technique, mais ils ont déjà leur propre groupe de comptes de responsable. Au lieu de créer un groupe pour les nouveaux membres du site et d’y placer tous les comptes de responsable un par un, placez les groupes de responsables existants pour chaque service dans le nouveau groupe.
  
  Si vous partagez un abonnement Office 365 avec d’autres organisations, il peut s’avérer difficile de gérer un seul niveau de groupe pour le site isolé d’une organisation en raison du nombre important de comptes d’utilisateur. Dans ce cas, vous pouvez utiliser les groupes Azure AD imbriqués pour chaque organisation dont les groupes gèrent les autorisations.
  
Pour utiliser les groupes Azure AD imbriqués, procédez comme suit :
  
1. Identifiez ou créez les groupes Azure AD qui contiendront les comptes d’utilisateur et ajoutez les comptes d’utilisateur en tant que membres.
    
2. Créez le groupe d’accès basé sur Azure AD conteneur qui contiendra les autres groupes Azure AD et ajoutez ces groupes en tant que membres.
    
3.   Pour définir le niveau d’accès approprié pour le groupe d’accès conteneur, identifiez le groupe SharePoint et définissez le niveau d’autorisation correspondant.
    
> [!NOTE]
> Vous ne pouvez pas utiliser des groupes Office 365 imbriqués. 
  
Voici un exemple d’annonce d’Azure imbriqué des groupes pour le groupe d’accès de membre ProjectX.
  
![Exemple d’utilisation des groupes d’accès imbriqués pour le groupe d’accès Membres pour le site ProjectX.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
Parce que tous les comptes d’utilisateur dans la recherche, l’ingénierie et de projet de prospects équipes sont destinés à être des membres du site, il est plus facile d’ajouter leurs groupes d’annonces Azure au groupe d’accès membres du ProjectX.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt pour créer et configurer un site isolé dans la production, voir [déploiement d’un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>See Also

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Gestion d'un site d'équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)
  
[Solutions de sécurité](security-solutions.md)

[Déploiement d'un site d'équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md)



