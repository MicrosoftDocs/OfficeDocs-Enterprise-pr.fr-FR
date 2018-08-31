---
title: Conception d’un site d’équipe SharePoint Online isolé
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
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: 'Résumé : Découvrez comment concevoir des sites d’équipe SharePoint Online.'
ms.openlocfilehash: 4807b7cef0a401901eb5abec3d683ca67b2193db
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914839"
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>Conception d’un site d’équipe SharePoint Online isolé

 **Résumé :** Découvrez comment concevoir des sites d’équipe SharePoint Online.
  
Cet article vous aide à faire les bons choix de conception avant de créer un site d’équipe SharePoint Online isolé.
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>Phase 1 : choix des groupes SharePoint et des niveaux d’autorisation

Chaque site d’équipe SharePoint Online par défaut est créé avec les groupes SharePoint suivants :
  
- \<nom du site > membres
    
- \<nom du site > visiteurs
    
- \<nom du site > propriétaires
    
Ces groupes sont différents des groupes Office 365 et Azure Active Directory (AD), et permettent d’attribuer des autorisations pour l’utilisation des ressources du site.
  
L’ensemble des autorisations qui déterminent ce que le membre d’un groupe SharePoint peut faire dans un site est un niveau d’autorisation. Il existe trois niveaux d’autorisation par défaut pour un site d’équipe SharePoint Online : Modification, Lecture et Contrôle total. Le tableau suivant indique la corrélation par défaut des groupes SharePoint et les niveaux d’autorisation affectés :
  
|**Groupe SharePoint**|**Niveau d’autorisation**|
|:-----|:-----|
|\<nom du site > membres  <br/> |Éditer  <br/> |
|\<nom du site > visiteurs  <br/> |Lire  <br/> |
|\<nom du site > propriétaires  <br/> |Contrôle total  <br/> |
   
 **Conseil :** vous pouvez créer des groupes SharePoint et des niveaux d’autorisation supplémentaires. Cependant, nous vous recommandons d’utiliser les groupes SharePoint par défaut et les niveaux d’autorisation pour votre site SharePoint Online isolé.
  
Voici les groupes SharePoint par défaut et les niveaux d’autorisation.
  
![Groupes SharePoint par défaut et niveaux d’autorisation pour un site SharePoint Online.](media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>Phase 2 : attribution des autorisations aux utilisateurs membres de groupes d’accès

Vous pouvez attribuer des autorisations aux utilisateurs en ajoutant leur compte d’utilisateur, ou un groupe Office 365 ou Azure AD dont est membre le compte d’utilisateur, aux groupes SharePoint. Une fois ajoutés, les comptes d’utilisateur Office 365 reçoivent, directement ou indirectement via l’appartenance à un groupe Office 365 ou Azure AD, le niveau d’autorisation associé au groupe SharePoint.
  
En prenant l’exemple des groupes SharePoint par défaut :
  
- Les membres de le ** \<nom du site > membres** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et groupes, sont affectés à **Modifier** le niveau d’autorisation
    
- Les membres de le ** \<nom du site > visiteurs** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et groupes, sont affectés le niveau d’autorisation **lecture**
    
- Les membres de le ** \<nom du site > propriétaires** groupe SharePoint, qui peut inclure des comptes d’utilisateurs et groupes, sont affectés du niveau d’autorisation **contrôle total**
    
 **Conseil :** même si vous pouvez gérer les autorisations dans chaque compte d’utilisateur, nous vous recommandons plutôt d’utiliser un seul groupe Azure AD, appelé groupe d’accès. Cela simplifie la gestion des autorisations via l’appartenance au groupe d’accès, plutôt que via la gestion de la liste des comptes d’utilisateur pour chaque groupe SharePoint.
  
Les groupes Azure AD pour Office 365 sont différents des groupes Office 365. Les groupes Azure AD apparaissent dans le Centre d’administration Office. Leur **type** est défini sur **Sécurité** et ils n’ont pas d’adresse e-mail. Les groupes Azure AD peuvent être gérés dans :
  
- Windows Server Active Directory (AD)
    
    Ces groupes ont été créés dans votre infrastructure locale Windows Server AD et ont été synchronisés avec votre abonnement Office 365. Dans le Centre d’administration Office, ils affichent l’**état****Synchronisés avec Active Directory**.
    
- Office 365
    
    Ces groupes ont été créés à l’aide du Centre d’administration Office, du portail Azure ou de Microsoft PowerShell. Dans le Centre d’administration Office, ils affichent l’**état****Cloud**.
    
 **Conseil :** si vous utilisez Windows Server AD en local et que vous le synchronisez avec votre abonnement Office 365, gérez vos utilisateurs et groupes avec Windows Server AD.
  
Pour les sites d’équipe SharePoint Online isolés, voici à quoi ressemble la structure recommandée du groupe :
  
|**Groupe SharePoint**|**Groupe d’accès basé sur Azure AD**|**Niveau d’autorisation**|
|:-----|:-----|:-----|
|\<nom du site > membres  <br/> |\<nom du site > membres  <br/> |Éditer  <br/> |
|\<nom du site > visiteurs  <br/> |\<nom du site > visionneuses  <br/> |Lire  <br/> |
|\<nom du site > propriétaires  <br/> |\<nom du site > administrateurs  <br/> |Contrôle total  <br/> |
   
 **Conseil :** même si vous pouvez utiliser des groupes Office 365 ou Azure AD en tant que membres des groupes SharePoint, nous vous recommandons d’utiliser les groupes Azure AD. Grâce aux groupes Azure AD, gérés via Windows Server AD ou Office 365, vous bénéficiez d’une plus grande flexibilité pour attribuer des autorisations avec les groupes imbriqués.
  
Voici les groupes SharePoint configurés pour utiliser des groupes d’accès Azure AD par défaut.
  
![Utilisation des groupes d’accès en tant que membres des groupes de sites SharePoint Online par défaut.](media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
Lorsque vous concevez les trois groupes d’accès, rappelez-vous de ceci :
  
- Il doit être uniquement quelques membres dans les ** \<nom du site > administrateurs** groupe d’accès, correspondant à un petit nombre d’administrateurs SharePoint Online qui gèrent le site d’équipe.
    
- La plupart des membres de votre site se trouvent dans le ** \<nom du site > membres** ou ** \<nom du site > visionneuses** accéder aux groupes. Étant donné que site membres dans le ** \<nom du site > membres** groupe accès ont la possibilité de supprimer ou modifier des ressources dans le site, considérez avec son appartenance. En cas de doute, ajoutez le membre de site pour le ** \<nom du site > visionneuses** groupe d’accès.
    
Voici un exemple des groupes SharePoint et des groupes d’accès pour un site isolé nommé ProjectX.
  
![Exemple d’utilisation des groupes d’accès pour un site SharePoint Online nommé ProjectX.](media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>Phase 3 : Utilisez les groupes d’Azure AD

Pour un projet est limité à un petit nombre de personnes, un seul niveau de Azure access basée sur AD-groupes ajoutés aux groupes SharePoint du site adapté à la plupart des scénarios. Toutefois, si vous disposez d’un grand nombre de personnes et aux personnes qui sont déjà membres d’établies groupes Azure AD, vous pouvez plus facilement attribuer les autorisations SharePoint à l’aide de groupes imbriqués ou des groupes qui contiennent d’autres groupes en tant que membres.
  
Par exemple, vous souhaitez créer un site d’équipe SharePoint Online isolé pour favoriser la collaboration entre les responsables des services ventes, marketing, ingénierie, juridique et support technique, mais ils ont déjà leur propre groupe de comptes de responsable. Au lieu de créer un groupe pour les nouveaux membres du site et d’y placer tous les comptes de responsable un par un, placez les groupes de responsables existants pour chaque service dans le nouveau groupe.
  
  Si vous partagez un abonnement Office 365 avec d’autres organisations, il peut s’avérer difficile de gérer un seul niveau de groupe pour le site isolé d’une organisation en raison du nombre important de comptes d’utilisateur. Dans ce cas, vous pouvez utiliser les groupes Azure AD imbriqués pour chaque organisation dont les groupes gèrent les autorisations.
  
Pour utiliser les groupes Azure AD imbriqués, procédez comme suit :
  
1. Identifiez ou créez les groupes Azure AD qui contiendront les comptes d’utilisateur et ajoutez les comptes d’utilisateur en tant que membres.
    
2. Créez le groupe d’accès basé sur Azure AD conteneur qui contiendra les autres groupes Azure AD et ajoutez ces groupes en tant que membres.
    
3.   Pour définir le niveau d’accès approprié pour le groupe d’accès conteneur, identifiez le groupe SharePoint et définissez le niveau d’autorisation correspondant.
    
> [!NOTE]
> Vous ne pouvez pas utiliser des groupes Office 365 imbriqués. 
  
Voici un exemple d’Azure AD imbriqué les groupes pour le groupe d’accès membre ProjectX.
  
![Exemple d’utilisation des groupes d’accès imbriqués pour le groupe d’accès Membres pour le site ProjectX.](media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
Étant donné que tous les comptes d’utilisateur dans la recherche, ingénierie, Project leads équipes sont destinés à être membres du site, il est plus facile d’ajouter leurs groupes Azure AD au groupe membres ProjectX accès.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à créer et à configurer un site isolé en production, consultez la rubrique [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Voir aussi

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Gestion d'un site d'équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)
  
[Solutions de sécurité](security-solutions.md)

[Déploiement d'un site d'équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md)



