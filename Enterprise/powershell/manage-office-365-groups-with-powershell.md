---
title: Utiliser PowerShell pour gérer les groupes Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
description: Découvrez comment effectuer des tâches de gestion courantes pour Office 365 groupes dans Microsoft PowerShell.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760056"
---
# <a name="manage-office-365-groups-with-powershell"></a>Utiliser PowerShell pour gérer les groupes Office 365

 *Dernière avril 18 mis à jour, 2018* 
  
Cet article fournit des instructions pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il indique également les applets de commande PowerShell pour les groupes. Pour obtenir des informations sur la gestion des sites SharePoint, voir [sites gérer SharePoint Online à l’aide de PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Lien vers votre directives d’utilisation de groupes de Office 365
<a name="BK_LinkToGuideLines"> </a>

Lorsque les utilisateurs de [créer ou modifier un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez afficher les un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous exige un préfixe spécifique ou suffixe à ajouter à un nom de groupe.
  
Utiliser Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365. Extrayez [d’Azure Active Directory des applets de commande pour configurer les paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir le lien hypertexte orientation de l’utilisation. Une fois vous avez exécuté l’applet de commande DAS, l’utilisateur sera voir le lien dans vos spécifications lorsqu’ils créent ou modifier un groupe dans Outlook. 
  
![Créer un nouveau groupe avec liaison des instructions d’utilisation](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Cliquez sur les directives d’utilisation de groupe pour voir vos organisations instructions de groupes d’Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Autoriser les utilisateurs à envoyer en tant que le groupe d’Office 365
<a name="BK_LinkToGuideLines"> </a>
  
Si vous souhaitez activer vos groupes d’Office 365 « Envoyer en tant que », utilisez le [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) et les applets de commande [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cette configuration. Une fois que vous activez ce paramètre, les utilisateurs de groupe de Office 365 peuvent utiliser Outlook ou Outlook sur le site web d’envoyer et de répondre aux messages que le groupe d’Office 365. Les utilisateurs peuvent accéder au groupe de créer un nouveau courrier électronique et de modifier le champ « Envoyer en tant que » à l’adresse de messagerie du groupe. 

([Vous pouvez également le faire dans le centre d’administration Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).
  
Utiliser le script, en remplaçant * \<GroupAlias\> * avec l’alias du groupe que vous souhaitez mettre à jour, et * \<UserAlias\> * avec l’alias de l’utilisateur auquel vous souhaitez accorder des autorisations. [Se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour exécuter ce script.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Une fois que l’applet de commande est exécutée, les utilisateurs peuvent aller à Outlook ou Outlook sur le web pour envoyer en tant que le groupe, en ajoutant l’adresse de messagerie de groupe pour **le champ** . 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Créer des classifications pour les groupes d’Office dans votre organisation

Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe d’Office 365. Par exemple, vous pouvez permettre aux utilisateurs de définir des « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Classifications de groupe ne sont pas définies par défaut et que vous devez créer dans l’ordre pour vos utilisateurs à définir. Utiliser Windows Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365.
  
Extrayez des [applets de commande Azure Active Directory pour la configuration des paramètres de groupe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir la classification des groupes d’Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Pour associer une description à chaque classification que vous pouvez utiliser l’attribut *ClassificationDescriptions* pour définir les paramètres.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

où Classification établit une correspondance avec les chaînes dans la ClassificationList.

Exemple :
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté l’applet de commande pour définir votre classification Azure Active Directory ci-dessus, exécutez l’applet de commande [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si vous souhaitez définir la classification pour un groupe spécifique. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Ou créez un nouveau groupe avec une classification.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Consultez la rubrique [à l’aide de PowerShell avec Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) et [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour plus d’informations sur l’utilisation d’Exchange Online PowerShell. 
  
Une fois ces paramètres sont activés, le propriétaire du groupe sera en mesure de choisir une classification dans la liste déroulante menu dans Outlook sur le Web et d’Outlook et enregistrez-le à partir de la page **Modifier** du groupe. 
  
![Choisissez la classification des groupes d’Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Masquer les groupes d’Office 365 à partir de la liste d’adresses globale
<a name="BKMK_CreateClassification"> </a>

Vous pouvez spécifier si un groupe d’Office 365 apparaît dans la liste d’adresses globale (LAG) et d’autres listes au sein de votre organisation. Par exemple, si vous disposez d’un groupe du département juridique que vous ne voulez pas que s’affiche dans la liste d’adresses, vous pouvez arrêter ce groupe d’apparaître dans la liste d’adresses globale. Exécutez l’applet de commande groupe Set-Unified pour masquer le groupe à partir de la liste d’adresses similaire à celle-ci :
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Autoriser uniquement les utilisateurs internes envoyer un message au groupe d’Office 365
<a name="BKMK_CreateClassification"> </a>

Si vous ne voulez pas que les utilisateurs d’autres organisations pour envoyer un message électronique à un groupe d’Office 365, vous pouvez modifier les paramètres pour ce groupe. Elle permet uniquement les utilisateurs internes puissent envoyer un message électronique à votre groupe. Si vous essaient d’envoyer un message à ce groupe utilisateurs externes, ils seront rejetés.
  
Exécutez l’applet de commande Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit :

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Ajouter des infos-courrier aux groupes d’Office 365
<a name="BKMK_CreateClassification"> </a>

Lorsqu’un expéditeur essaie d’envoyer un message électronique à un groupe d’Office 365, une info-courrier peut être affichée pour eux.
  
Exécutez l’applet de commande pour ajouter une info-courrier au groupe Set-Unified groupe :

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Avec info-courrier, vous pouvez également définir MailTipTranslations, qui spécifie les langues supplémentaires pour l’info-courrier. Supposons que vous disposez de la traduction espagnole, puis exécutez la commande suivante :
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Modifier le nom complet du groupe d’Office 365

Nom d’affichage spécifie le nom du groupe d’Office 365. Vous pouvez voir ce nom dans votre centre d’administration exchange ou un portail d’administration d’Office 365. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe d’Office 365 existant en exécutant la commande Set-UnifiedGroup :

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut d’Office 365 groupes pour Outlook Public ou privé
<a name="BKMK_CreateClassification"> </a>

Office 365 groupes dans Outlook sont créés comme étant privé par défaut. Si votre organisation souhaite Office 365 groupes peuvent être créés en tant que Public par défaut (ou en privé), utilisez cette syntaxe d’applet de commande PowerShell :
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Pour définir privé :
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Pour vérifier le paramètre : 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Pour plus d’informations, voir [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) et [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Applets de commande de groupes Office 365

Les applets de commande suivante peut être utilisé avec Office 365 groupes.
  
|**Nom de la cmdlet**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Utilisez cette applet de commande pour rechercher des groupes d’existants Office 365 et pour afficher les propriétés de l’objet de groupe  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Mettre à jour les propriétés d’un groupe de 365 Office spécifique  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Créer un nouveau groupe d’Office 365. Cette applet de commande fournit un ensemble de paramètres minimal, pour le paramètre de valeurs pour les propriétés étendues utilisent Set-UnifiedGroup après la création du nouveau groupe  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Supprimer un groupe de 365 Office existant  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Récupérer des informations d’appartenance et le propriétaire d’un groupe d’Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Ajouter des centaines ou des milliers d’utilisateurs, ou de nouveaux propriétaires, à un groupe de 365 Office existant  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Supprimer les propriétaires et les membres d’un groupe de 365 Office existant  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Permet d’afficher des informations sur la photo de l’utilisateur associée à un compte. Photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Utilisé pour associer une photo de l’utilisateur à un compte. Photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Supprimer la photo d’un groupe d’Office 365  <br/> |

## <a name="related-topics"></a>Voir aussi

[Listes de distribution de mise à niveau vers Office 365 groupes](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Gérer les personnes autorisées à créer des groupes Office 365](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Gérer l'accès invité aux groupes Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Modifier l’appartenance au groupe statique dynamique dans](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
