---
title: Préparation d’un domaine non routable pour la synchronisation d’annuaires
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Pour savoir comment procéder, si vous avez un domaine non-routale associé à vos utilisateurs locaux avant de procéder à une synchronisation avec Microsoft 365.
ms.openlocfilehash: 148d7e1abdeeeea11c838697bbc957e2937ea7f8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736012"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Préparation d’un domaine non routable pour la synchronisation d’annuaires
Lorsque vous synchronisez votre annuaire sur site avec Microsoft 365, vous devez disposer d’un domaine vérifié dans Azure Active Directory (Azure AD). Seuls les noms d’utilisateur principal (UPN) associés au domaine local sont synchronisés. Toutefois, tout nom UPN contenant un domaine non routable, par exemple, local (comme billa@contoso. local), sera synchronisé avec un domaine. onmicrosoft.com (comme billa@contoso.onmicrosoft.com). 

Si vous utilisez actuellement un domaine. local pour vos comptes d’utilisateur dans les services de domaine Active Directory (AD DS), il est recommandé de les modifier afin qu’ils utilisent un domaine vérifié (par exemple, billa@contoso.com) afin de se synchroniser correctement avec votre domaine Microsoft 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Que se passe-t-il si j’ai uniquement un domaine local sur site ?

Le dernier outil que vous pouvez utiliser pour synchroniser votre AD DS vers Azure AD est nommé Azure AD Connect. Pour plus d’informations, reportez-vous à [la rubrique intégration de vos identités locales à Azure ad](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect synchronise le nom d’utilisateur et le mot de passe de vos utilisateurs afin que les utilisateurs puissent se connecter avec les mêmes informations d’identification qu’ils utilisent localement. Toutefois, Azure AD Connect synchronise uniquement les utilisateurs avec les domaines qui sont vérifiés par Microsoft 365. Cela signifie que le domaine est également vérifié par Azure AD car les identités Microsoft 365 sont gérées par Azure AD. En d’autres termes, le domaine doit être un domaine Internet valide (par exemple,. com,. org, .net,. US, etc.). Si votre AD DS interne utilise uniquement un domaine qui n’est pas routable (par exemple,. local), il ne peut pas correspondre au domaine vérifié que vous avez sur Microsoft 365. Vous pouvez résoudre ce problème en modifiant votre domaine principal dans votre service AD DS local ou en ajoutant un ou plusieurs suffixes UPN.
  
### <a name="change-your-primary-domain"></a>**Modifier votre domaine principal**

Modifiez votre domaine principal en un domaine que vous avez vérifié dans Microsoft 365, par exemple, contoso.com. Chaque utilisateur ayant le domaine contoso. local est ensuite mis à jour vers contoso.com. Pour obtenir des instructions, consultez [la rubrique How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). Il s’agit d’un processus très important, mais une solution plus facile est décrite dans la section suivante.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Ajouter des suffixes UPN et mettre à jour vos utilisateurs vers eux**

Vous pouvez résoudre le problème. local en enregistrant de nouveaux suffixes ou suffixes UPN dans AD DS pour qu’ils correspondent au domaine (ou aux domaines) que vous avez vérifié dans Microsoft 365. Après avoir enregistré le nouveau suffixe, vous mettez à jour l’utilisateur UPN pour remplacer le fichier. local par le nouveau nom de domaine par exemple, de sorte qu’un compte d’utilisateur ressemble à billa@contoso.com.
  
Une fois que vous avez mis à jour l’UPN pour utiliser le domaine vérifié, vous êtes prêt à synchroniser votre AD DS sur site avec Microsoft 365.
  
 **Étape 1 : ajouter le nouveau suffixe UPN**
  
1. Sur le contrôleur de domaine AD DS, dans le gestionnaire de serveur, choisissez **Outils** \> **domaines et approbations Active Directory**.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez sur la **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez dans Domain. msc, puis cliquez sur **OK**.
    
    ![Choisissez domaines et approbations Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Dans la fenêtre **domaines et approbations Active Directory** , cliquez avec le bouton droit sur **domaines et approbations Active Directory**, puis choisissez **Propriétés**.
    
    ![Cliquez avec le bouton droit sur domaines et approbations Active Directory, puis choisissez Propriétés.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Dans l’onglet **suffixes UPN** , dans la zone **autres suffixes UPN** , tapez votre nouveau suffixe ou suffixe UPN, puis choisissez **Ajouter** \> **Apply**.
    
    ![Ajouter un nouveau suffixe UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Choisissez **OK** lorsque vous avez terminé d’ajouter des suffixes. 
    
 **Étape 2 : modifier le suffixe UPN pour les utilisateurs existants**
  
1. Sur le contrôleur de domaine AD DS, dans le gestionnaire de serveur, choisissez **Outils** \> **et utilisateurs Active Directory**.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez sur la **touche Windows + R** pour ouvrir la boîte de dialogue **exécuter** , puis tapez dsa. msc, puis cliquez sur **OK** .
    
2. Sélectionnez un utilisateur, cliquez avec le bouton droit, puis choisissez **Propriétés**.
    
3. Dans l’onglet **compte** , dans la liste déroulante suffixe UPN, choisissez le nouveau suffixe UPN, puis choisissez **OK**.
    
    ![Ajouter un nouveau suffixe UPN pour un utilisateur](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Effectuez ces étapes pour chaque utilisateur.
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Vous pouvez également utiliser Windows PowerShell pour modifier le suffixe UPN pour tous les utilisateurs**

Si vous avez un grand nombre d’utilisateurs à mettre à jour, il est plus facile d’utiliser Windows PowerShell. L’exemple suivant utilise les cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) et [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) pour remplacer tous les suffixes contoso. local par contoso.com. 

Pour exemple, vous pouvez exécuter les commandes Windows PowerShell suivantes pour mettre à jour tous les suffixes contoso. local vers contoso.com :
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

Consultez la rubrique [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) pour en savoir plus sur l’utilisation de Windows PowerShell dans AD DS. 

