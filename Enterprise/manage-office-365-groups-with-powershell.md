---
title: Utiliser PowerShell pour gérer les groupes Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Cet article fournit des instructions pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell.
ms.openlocfilehash: 83b7340cea1fd8d38bba073353b61f0b17fad8a0
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741227"
---
# <a name="manage-office-365-groups-with-powershell"></a>Utiliser PowerShell pour gérer les groupes Office 365

 *Dernière avril 18 mis à jour, 2018* 
  
Cet article fournit des instructions pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il indique également les applets de commande PowerShell pour les groupes. Pour obtenir des informations sur la gestion des sites SharePoint, voir [sites gérer SharePoint Online à l’aide de PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Tâches courantes de gestion des groupes d’Office 365

- [Listes de distribution de mise à niveau vers Office 365 groupes](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [Gérer les personnes autorisées à créer des groupes Office 365](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [Gérer l'accès invité aux groupes Office 365](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [Gérer les groupes de façon dynamique dans Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Ajouter des centaines, voire des milliers d’utilisateurs aux groupes d’Office 365, utilisez la [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Lien vers votre directives d’utilisation de groupes de Office 365
<a name="BK_LinkToGuideLines"> </a>

Lorsque les utilisateurs de [créer ou modifier un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez afficher les un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous exige un préfixe spécifique ou suffixe à ajouter à un nom de groupe.
  
Utiliser Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365. Extrayez [d’Azure Active Directory des applets de commande pour configurer les paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir le lien hypertexte orientation de l’utilisation. Une fois vous avez exécuté l’applet de commande DAS, l’utilisateur sera voir le lien dans vos spécifications lorsqu’ils créent ou modifier un groupe dans Outlook. 
  
![Créer un nouveau groupe avec liaison des instructions d’utilisation](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Cliquez sur les directives d’utilisation de groupe pour voir vos organisations instructions de groupes d’Office 365](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Autoriser les utilisateurs à envoyer en tant que le groupe d’Office 365
<a name="BK_LinkToGuideLines"> </a>

Vous pouvez également procéder ainsi dans le centre d’administration Exchange. Voir [Autoriser les membres « Envoyer en tant que » ou « Envoyer de la part de » un groupe d’Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).
  
Si vous souhaitez activer vos groupes d’Office 365 « Envoyer en tant que », utilisez le [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) et les applets de commande [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cette configuration. Une fois que vous activez ce paramètre, les utilisateurs de groupe de Office 365 peuvent utiliser Outlook ou Outlook sur le site web d’envoyer et de répondre aux messages que le groupe d’Office 365. Les utilisateurs peuvent accéder au groupe de créer un nouveau courrier électronique et de modifier le champ « Envoyer en tant que » à l’adresse de messagerie du groupe. 
  
> [!NOTE]
> Vous devez ajouter l’adresse de messagerie du groupe dans le champ **Cc** lorsque vous composez le courrier électronique « Envoyer en tant que », afin que le message est envoyé au groupe et s’affiche dans des conversations de groupe. 
  
À ce stade, la seule façon de mettre à jour la stratégie de boîte aux lettres est via [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Utilisez cette commande pour définir l’alias de groupe.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Utilisez cette commande pour définir l’alias de l’utilisateur.
    
  ```
  $userAlias = "User"
  ```

- Cette commande permet de transmettre le groupalias à l’applet de commande Get-Recipient pour obtenir les détails du destinataire.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- Le nom du destinataire cible (nom du groupe) doit être transmis à la cmdlet Add-RecipientPermission. Useralias pour lesquels l’autorisation sendas bénéficiera sera attribué au paramètre - du client approuvé.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Une fois que l’applet de commande est exécutée, les utilisateurs peuvent aller à Outlook ou Outlook sur le web pour envoyer en tant que le groupe, en ajoutant l’adresse de messagerie de groupe pour **le champ** . 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Créer des classifications pour les groupes d’Office dans votre organisation

Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe d’Office 365. Par exemple, vous pouvez permettre aux utilisateurs de définir des « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Classifications de groupe ne sont pas définies par défaut et que vous devez créer dans l’ordre pour vos utilisateurs à définir. Utiliser Windows Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365.
  
Extrayez des [applets de commande Azure Active Directory pour la configuration des paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir la classification des groupes d’Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Pour associer une description à chaque classification que vous pouvez utiliser l’attribut *ClassificationDescriptions* pour définir les paramètres. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Exemple :
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté l’applet de commande pour définir votre classification Azure Active Directory ci-dessus, exécutez l’applet de commande [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) si vous souhaitez définir la classification pour un groupe spécifique. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Ou créez un nouveau groupe avec une classification.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Consultez la rubrique [à l’aide de PowerShell avec Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) et [se connecter à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) pour plus d’informations sur l’utilisation d’Exchange Online PowerShell. 
  
Une fois ces paramètres sont activés, le propriétaire du groupe sera en mesure de choisir une classification dans la liste déroulante menu dans Outlook sur le Web et d’Outlook et enregistrez-le à partir de la page **Modifier** du groupe. 
  
![Choisissez la classification des groupes d’Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Masquer les groupes d’Office 365 à partir de la liste d’adresses globale
<a name="BKMK_CreateClassification"> </a>

Vous pouvez spécifier si un groupe d’Office 365 apparaît dans la liste d’adresses globale (LAG) et d’autres listes au sein de votre organisation. Par exemple, si vous disposez d’un groupe du département juridique que vous ne voulez pas que s’affiche dans la liste d’adresses, vous pouvez arrêter ce groupe d’apparaître dans la liste d’adresses globale. Exécutez l’applet de commande groupe Set-Unified pour masquer le groupe à partir de la liste d’adresses similaire à celle-ci :
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Autoriser uniquement les utilisateurs internes envoyer un message au groupe d’Office 365
<a name="BKMK_CreateClassification"> </a>

Si vous ne voulez pas que les utilisateurs d’autres organisations pour envoyer un message électronique à un groupe d’Office 365, vous pouvez modifier les paramètres pour ce groupe. Elle permet uniquement les utilisateurs internes puissent envoyer un message électronique à votre groupe. Si vous essaient d’envoyer un message à ce groupe utilisateurs externes, ils seront rejetés.
  
Exécutez l’applet de commande Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit :
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Ajouter des infos-courrier aux groupes d’Office 365
<a name="BKMK_CreateClassification"> </a>

Lorsqu’un expéditeur essaie d’envoyer un message électronique à un groupe d’Office 365, une info-courrier peut être affichée pour lui.
  
Exécutez l’applet de commande groupe Set-Unified pour ajouter une info-courrier au groupe :
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Avec info-courrier, vous pouvez également définir MailTipTranslations, qui spécifie les langues supplémentaires pour l’info-courrier. Supposons que vous disposez de la traduction espagnole, puis exécutez la commande suivante :
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Modifier le nom complet du groupe d’Office 365

Nom d’affichage spécifie le nom du groupe d’Office 365. Vous pouvez voir ce nom dans votre portail d’administration exchange admin center ou o365. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe d’Office 365 existant en exécutant la commande Set-UnifiedGroup :
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Gérer les photos de l’utilisateur dans Office 365 groupes

|**Nom de la cmdlet**|**Description**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Permet d’afficher des informations sur la photo de l’utilisateur associée à un compte. Photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Utilisé pour associer une photo de l’utilisateur à un compte. Photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Supprimer la photo d’un groupe d’Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut d’Office 365 groupes pour Outlook Public ou privé
<a name="BKMK_CreateClassification"> </a>

Office 365 groupes dans Outlook sont créés comme étant privé par défaut. Si votre organisation souhaite Office 365 groupes Outlook être créé en tant que Public par défaut (ou à privée), utilisez cette syntaxe d’applet de commande PowerShell :
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Pour définir privé :
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Pour vérifier le paramètre : 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Pour plus d’informations, voir [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) et [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Applets de commande de groupes Office 365

Les applets de commande suivantes ont été apportées récemment disponibles aux groupes d’Office 365. Si vous n’êtes pas en mesure d’utiliser ces, votre abonnement Office 365 n'a pas été encore mis à jour avec cette fonctionnalité. Vérifiez votre centre de messages et de la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).
  
|**Nom de la cmdlet**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Utilisez cette applet de commande pour rechercher des groupes d’existants Office 365 et pour afficher les propriétés de l’objet de groupe  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Mettre à jour les propriétés d’un groupe de 365 Office spécifique  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Créer un nouveau groupe d’Office 365. Cette applet de commande fournit un ensemble de paramètres minimal, pour le paramètre de valeurs pour les propriétés étendues utilisent Set-UnifiedGroup après la création du nouveau groupe  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Supprimer un groupe de 365 Office existant  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Récupérer des informations d’appartenance et le propriétaire d’un groupe d’Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Ajouter des centaines ou des milliers d’utilisateurs, ou de nouveaux propriétaires, à un groupe de 365 Office existant  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Supprimer les propriétaires et les membres d’un groupe de 365 Office existant  <br/> |
   
## <a name="for-more-information"></a>Pour plus d’informations

[Gérer Office 365 avec Office 365 PowerShell](powershell/manage-office-365-with-office-365-powershell.md)
