---
title: Utiliser PowerShell pour gérer les groupes Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
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
description: Découvrez comment effectuer des tâches de gestion courantes pour les groupes Office 365 dans Microsoft PowerShell.
ms.openlocfilehash: b2cd536630f80dec66344162669b0bbe1cf3b4cd
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069020"
---
# <a name="manage-office-365-groups-with-powershell"></a>Utiliser PowerShell pour gérer les groupes Office 365

 *Dernière mise à jour: 18 avril 2018* 
  
Cet article décrit les étapes à suivre pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il répertorie également les applets de commande PowerShell pour les groupes. Pour plus d’informations sur la gestion des sites SharePoint, voir [gérer les sites SharePoint Online à l’aide de PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Lien vers les instructions d’utilisation de vos groupes Office 365
<a name="BK_LinkToGuideLines"> </a>

Lorsque les utilisateurs [créent ou modifient un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez leur montrer un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous avez besoin d’ajouter un préfixe ou un suffixe spécifique à un nom de groupe.
  
Utilisez Azure Active Directory PowerShell pour faire pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes Office 365. Consultez les [applets de commande Azure Active Directory pour configurer les paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans la **section créer des paramètres au niveau du répertoire** pour définir le lien hypertexte des indications d’utilisation. Une fois que vous avez exécuté la cmdlet AAD, les utilisateurs verront le lien vers vos instructions lors de la création ou de la modification d’un groupe dans Outlook. 
  
![Créer un nouveau groupe avec les instructions d’utilisation lien](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Cliquez sur conseils sur l’utilisation des groupes pour consulter les directives de groupes Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Autoriser les utilisateurs à envoyer en tant que groupe Office 365
<a name="BK_LinkToGuideLines"> </a>
  
Si vous souhaitez activer vos groupes Office 365 sur «Envoyer en tant que», utilisez les cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) et [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) pour configurer ce. Une fois que vous activez ce paramètre, les utilisateurs du groupe Office 365 peuvent utiliser Outlook ou Outlook sur le Web pour envoyer et répondre à des messages électroniques en tant que groupe 365 Office. Les utilisateurs peuvent accéder au groupe, créer un nouveau courrier électronique et modifier le champ «envoyer en tant que» sur l’adresse de messagerie du groupe. 

([Vous pouvez également le faire dans le centre d’administration Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)
  
Utilisez le script suivant, en * \<remplaçant\> GroupAlias* par l’alias du groupe que vous souhaitez mettre à jour, * \<et\> userAlias* par l’alias de l’utilisateur auquel vous souhaitez accorder permssions. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour exécuter ce script.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Une fois l’applet de commande exécutée, les utilisateurs peuvent accéder à Outlook ou à Outlook sur le Web pour les envoyer en tant que groupe, en ajoutant l’adresse de messagerie du groupe au champ **de** . 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Créer des classifications pour les groupes Office dans votre organisation

Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lors de la création d’un groupe Office 365. Par exemple, vous pouvez autoriser les utilisateurs à définir «standard», «secret» et «top secret» dans les groupes qu’ils créent. Les classifications de groupe ne sont pas définies par défaut et vous devez les créer afin que les utilisateurs puissent la définir. Utilisez Azure Active Directory PowerShell pour faire pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes Office 365.
  
Consultez les [applets de commande Azure Active Directory pour configurer les paramètres de groupe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) et suivez les étapes décrites dans la **section Create Settings at the Directory Level** to define the Classification for Office 365 groups. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Afin d’associer une description à chaque classification, vous pouvez utiliser l’attribut Settings *ClassificationDescriptions* pour définir.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

où la classification établit une correspondance avec les chaînes du ClassificationList.

Exemple :
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté la cmdlet Azure Active Directory ci-dessus pour définir votre classification, exécutez la cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si vous voulez définir la classification pour un groupe spécifique. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Ou créez un groupe avec une classification.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Pour plus d’informations sur l’utilisation d’Exchange Online PowerShell, consultez [l’aide de PowerShell avec Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) et [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) . 
  
Une fois ces paramètres activés, le propriétaire du groupe pourra choisir une classification dans le menu déroulant dans Outlook sur le Web et Outlook, puis enregistrez-le à partir de la page **modifier** le groupe. 
  
![Choisir la classification de groupe Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Masquer les groupes Office 365 dans la liste d’adresses globale
<a name="BKMK_CreateClassification"> </a>

Vous pouvez spécifier si un groupe Office 365 apparaît dans la liste d’adresses globale (LAG) et d’autres listes de votre organisation. Par exemple, si vous avez un groupe de services légaux que vous ne voulez pas afficher dans la liste d’adresses, vous pouvez l’empêcher d’apparaître dans la liste d’adresses globale. Exécutez la cmdlet Set-Unified Group pour masquer le groupe de la liste d’adresses comme suit:
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Autoriser uniquement les utilisateurs internes à envoyer un message au groupe Office 365
<a name="BKMK_CreateClassification"> </a>

Si vous ne voulez pas que les utilisateurs d’autres organisations puissent envoyer des messages électroniques à un groupe Office 365, vous pouvez modifier les paramètres de ce groupe. Il permettra uniquement aux utilisateurs internes d’envoyer un courrier électronique à votre groupe. Si un utilisateur externe essaie d’envoyer un message à ce groupe, il sera rejeté.
  
Exécutez la cmdlet Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit:

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Ajouter des infos-courrier aux groupes Office 365
<a name="BKMK_CreateClassification"> </a>

Chaque fois qu’un expéditeur tente d’envoyer un message électronique à un groupe Office 365, un info-courrier peut s’afficher.
  
Exécutez la cmdlet Set-Unified Group pour ajouter un info-courrier au groupe:

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Avec info-courrier, vous pouvez également définir MailTipTranslations, qui spécifie des langues supplémentaires pour l’info-courrier. Supposons que vous voulez avoir la traduction espagnole, puis exécutez la commande suivante:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Modifier le nom d’affichage du groupe Office 365

Nom d’affichage spécifie le nom du groupe Office 365. Vous pouvez voir ce nom dans votre centre d’administration Exchange ou dans le portail d’administration d’Office 365. Vous pouvez modifier le nom d’affichage du groupe ou attribuer un nom d’affichage à un groupe Office 365 existant en exécutant la commande Set-UnifiedGroup:

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut des groupes Office 365 pour Outlook en mode public ou privé
<a name="BKMK_CreateClassification"> </a>

Les groupes Office 365 dans Outlook sont créés comme étant privés par défaut. Si votre organisation souhaite que les groupes Office 365 soient créés en tant que public par défaut (ou retour à privé), utilisez la syntaxe de cette cmdlet PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Pour définir sur privé:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Pour vérifier le paramètre: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Pour plus d’informations, consultez la rubrique [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) et [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets de groupes Office 365

Les applets de commande suivantes peuvent être utilisées avec les groupes Office 365.
  
|**Nom de l'applet de commande**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Utilisez cette applet de commande pour rechercher des groupes Office 365 existants et afficher les propriétés de l’objet de groupe.  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Mettre à jour les propriétés d’un groupe Office 365 spécifique  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Créez un groupe Office 365. Cette applet de commande fournit un ensemble minimal de paramètres pour définir les valeurs des propriétés étendues, utilisez Set-UnifiedGroup après avoir créé le groupe.  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Supprimer un groupe Office 365 existant  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Récupérer les informations d’appartenance et de propriétaire pour un groupe Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Ajouter des centaines ou des milliers d’utilisateurs ou de nouveaux propriétaires à un groupe Office 365 existant  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Supprimer des propriétaires et des membres d’un groupe Office 365 existant  <br/> |
|[Get-applet userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Permet d’afficher des informations sur la photo de l’utilisateur associée à un compte. Les photos des utilisateurs sont stockées dans Active Directory  <br/> |
|[Set-applet userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Utilisé pour associer une photo d’utilisateur à un compte. Les photos des utilisateurs sont stockées dans Active Directory  <br/> |
|[Remove-applet userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Suppression de la photo d’un groupe Office 365  <br/> |

## <a name="related-topics"></a>Sujets associés

[Mettre à niveau des listes de distribution vers des groupes Office 365](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Gérer les personnes autorisées à créer des groupes Office 365](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Gérer l'accès invité aux groupes Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Modifier l’appartenance au groupe statique en membre dynamique dans](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
