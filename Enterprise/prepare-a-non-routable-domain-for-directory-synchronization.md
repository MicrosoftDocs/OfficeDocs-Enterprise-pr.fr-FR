---
title: Préparer un domaine non routable pour la synchronisation d’annuaires
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Découvrez que faire si vous disposez d’un domaine non routale associé à vos utilisateurs sur site avant de le synchroniser avec Office 365.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674438"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Préparer un domaine non routable pour la synchronisation d’annuaires
Lorsque vous synchronisez votre annuaire local avec Office 365, vous devez disposer d’un domaine vérifié dans Azure Active Directory. Uniquement l’utilisateur Principal noms (UPN) qui sont associées dans le domaine local sont synchronisées. Toutefois, n’importe quel nom UPN qui contient un domaine non routable, par exemple .local (par exemple, billa@contoso.local), sera synchronisé avec un. onmicrosoft.com domaine (par exemple billa@contoso.onmicrosoft.com). 

Si vous utilisez actuellement un domaine .local pour vos comptes d’utilisateurs dans Active Directory, il est recommandé que vous les modifiez pour utiliser un domaine vérifié (comme billa@contoso.com) afin de synchroniser correctement avec votre domaine à Office 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Que se passe-t-il si j’ai uniquement un domaine local de .local ?

L’outil plus récente que vous pouvez utiliser pour la synchronisation Active Directory pour Azure Active Directory nommé Azure AD se connecter. Pour plus d’informations, voir [intégration des identités avec Azure Active Directory local](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect synchronise UPN et le mot de passe des utilisateurs afin que les utilisateurs peuvent se connecter avec les mêmes informations d’identification qu’ils utilisent sur site. Toutefois, Azure AD Connect synchronise uniquement aux utilisateurs de domaines qui ont été vérifiées par Office 365. Cela signifie que le domaine est également vérifié par Azure Active Directory étant donné que les identités Office 365 sont gérées par Azure Active Directory. En d’autres termes, le domaine doit être un domaine Internet valid (par exemple, .com, .org, .net, .us, etc.). Si votre environnement Active Directory interne utilise uniquement un domaine non routable (par exemple, .local), celui-ci ne peut pas éventuellement correspondre au domaine vérifié que vous avez sur Office 365. Vous pouvez résoudre ce problème en modifiant votre domaine principal dans votre environnement local sur Active Directory, ou en ajoutant un ou plusieurs suffixes UPN.
  
### <a name="change-your-primary-domain"></a>**Modifier votre domaine principal**

Modifier votre domaine principal à un domaine que vous avez vérifié dans Office 365, par exemple, contoso.com. Tous les utilisateurs dont le domaine contoso.local sont alors mis à jour pour contoso.com. Pour plus d’informations, voir [Domaine renommer fonctionnement](https://go.microsoft.com/fwlink/p/?LinkId=624174). Il s’agit d’un processus très complexe, cependant, et une solution plus simple consiste à [Ajouter un UPN suffixes et mettre à jour vos utilisateurs leur](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), comme indiqué dans la section suivante.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Ajouter des suffixes UPN et mettre à jour vos utilisateurs leur**

Vous pouvez résoudre le problème .local en enregistrant le nouveau suffixe UPN ou des suffixes dans Active Directory pour correspondre au domaine (ou domaines) que vous avez vérifié à Office 365. Une fois que vous enregistrez le nouveau suffixe, l’utilisateur UPN pour remplacer le .local avec le nouveau nom de domaine, par exemple, pour qu’un compte d’utilisateur ressemble billa@contoso.com mettre à jour.
  
Une fois que vous avez mis à jour l’UPN pour utiliser le domaine vérifié, vous êtes prêt à synchroniser Active Directory local avec Office 365.
  
 **Étape 1 : Ajouter le nouveau suffixe UPN**
  
1. Choisir les **Outils** sur le serveur qui exécute les Services de domaine Active Directory (AD DS) sur, dans le Gestionnaire de serveur \> **Directory domaines et approbations Active**.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez sur **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez Domain.msc, puis cliquez sur **OK**.
    
    ![Cliquez sur domaines et approbations Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Dans la fenêtre **Active Directory domaines et approbations** , avec le bouton droit de **domaines Active Directory et les approbations**, puis choisissez **Propriétés**.
    
    ![Avec le bouton droit ActiveDirectory domaines et approbations et choisissez Propriétés](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Sous l’onglet **Suffixes UPN** , dans la zone **Alternative des Suffixes UPN** , tapez votre nouveau suffixe UPN ou des suffixes, puis choisissez **Ajouter** \> **Appliquer**.
    
    ![Ajouter un nouveau suffixe UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Cliquez sur **OK** lorsque vous avez terminé d’ajouter des suffixes. 
    
 **Étape 2 : Modifier le suffixe UPN pour les utilisateurs existants**
  
1. Choisir les **Outils** sur le serveur qui exécute les Services de domaine Active Directory (AD DS) sur, dans le Gestionnaire de serveur \> **répertoire Active Directory utilisateurs et ordinateurs Active**.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez sur **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez dsa.msc, puis cliquez sur **OK**
    
2. Sélectionnez un utilisateur, avec le bouton droit, puis cliquez sur **Propriétés**.
    
3. Sous l’onglet **compte** , dans la liste déroulante du suffixe UPN, choisissez Nouveau suffixe UPN, puis cliquez sur **OK**.
    
    ![Ajouter un nouveau suffixe UPN pour un utilisateur](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Effectuez ces étapes pour chaque utilisateur.
    
    Vous pouvez également mettre à jour l’UPN suffixes [vous pouvez également utiliser Windows PowerShell pour modifier le suffixe UPN pour tous les utilisateurs](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Vous pouvez également utiliser Windows PowerShell pour modifier le suffixe UPN pour tous les utilisateurs**

Si vous avez un grand nombre d’utilisateurs à mettre à jour, il est plus facile d’utiliser Windows PowerShell. L’exemple suivant utilise les applets de commande [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) et [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) pour modifier tous les suffixes contoso.local pour contoso.com. 

Exécutez les commandes Windows PowerShell suivantes pour mettre à jour tous les suffixes contoso.local contoso.com :
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Voir [module Active Directory Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=624314) pour en savoir plus sur l’utilisation de Windows PowerShell dans Active Directory. 

