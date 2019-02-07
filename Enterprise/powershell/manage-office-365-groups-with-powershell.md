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
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="6f580-103">Utiliser PowerShell pour gérer les groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="6f580-104">*Dernière avril 18 mis à jour, 2018*</span><span class="sxs-lookup"><span data-stu-id="6f580-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="6f580-p101">Cet article fournit des instructions pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il indique également les applets de commande PowerShell pour les groupes. Pour obtenir des informations sur la gestion des sites SharePoint, voir [sites gérer SharePoint Online à l’aide de PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="6f580-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="6f580-108">Lien vers votre directives d’utilisation de groupes de Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="6f580-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-109"></span></span>

<span data-ttu-id="6f580-p102">Lorsque les utilisateurs de [créer ou modifier un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez afficher les un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous exige un préfixe spécifique ou suffixe à ajouter à un nom de groupe.</span><span class="sxs-lookup"><span data-stu-id="6f580-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="6f580-p103">Utiliser Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365. Extrayez [d’Azure Active Directory des applets de commande pour configurer les paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir le lien hypertexte orientation de l’utilisation. Une fois vous avez exécuté l’applet de commande DAS, l’utilisateur sera voir le lien dans vos spécifications lorsqu’ils créent ou modifier un groupe dans Outlook.</span><span class="sxs-lookup"><span data-stu-id="6f580-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Créer un nouveau groupe avec liaison des instructions d’utilisation](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Cliquez sur les directives d’utilisation de groupe pour voir vos organisations instructions de groupes d’Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="6f580-117">Autoriser les utilisateurs à envoyer en tant que le groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="6f580-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-118"></span></span>
  
<span data-ttu-id="6f580-p104">Si vous souhaitez activer vos groupes d’Office 365 « Envoyer en tant que », utilisez le [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) et les applets de commande [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cette configuration. Une fois que vous activez ce paramètre, les utilisateurs de groupe de Office 365 peuvent utiliser Outlook ou Outlook sur le site web d’envoyer et de répondre aux messages que le groupe d’Office 365. Les utilisateurs peuvent accéder au groupe de créer un nouveau courrier électronique et de modifier le champ « Envoyer en tant que » à l’adresse de messagerie du groupe.</span><span class="sxs-lookup"><span data-stu-id="6f580-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="6f580-122">([Vous pouvez également le faire dans le centre d’administration Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="6f580-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="6f580-p105">Utiliser le script, en remplaçant \* \<GroupAlias\> \* avec l’alias du groupe que vous souhaitez mettre à jour, et \* \<UserAlias\> \* avec l’alias de l’utilisateur auquel vous souhaitez accorder des autorisations. [Se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour exécuter ce script.</span><span class="sxs-lookup"><span data-stu-id="6f580-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="6f580-125">Une fois que l’applet de commande est exécutée, les utilisateurs peuvent aller à Outlook ou Outlook sur le web pour envoyer en tant que le groupe, en ajoutant l’adresse de messagerie de groupe pour **le champ** .</span><span class="sxs-lookup"><span data-stu-id="6f580-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="6f580-126">Créer des classifications pour les groupes d’Office dans votre organisation</span><span class="sxs-lookup"><span data-stu-id="6f580-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="6f580-p106">Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe d’Office 365. Par exemple, vous pouvez permettre aux utilisateurs de définir des « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Classifications de groupe ne sont pas définies par défaut et que vous devez créer dans l’ordre pour vos utilisateurs à définir. Utiliser Windows Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="6f580-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="6f580-131">Extrayez des [applets de commande Azure Active Directory pour la configuration des paramètres de groupe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir la classification des groupes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="6f580-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="6f580-132">Pour associer une description à chaque classification que vous pouvez utiliser l’attribut *ClassificationDescriptions* pour définir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="6f580-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="6f580-133">où Classification établit une correspondance avec les chaînes dans la ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="6f580-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="6f580-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6f580-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="6f580-135">Après avoir exécuté l’applet de commande pour définir votre classification Azure Active Directory ci-dessus, exécutez l’applet de commande [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si vous souhaitez définir la classification pour un groupe spécifique.</span><span class="sxs-lookup"><span data-stu-id="6f580-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="6f580-136">Ou créez un nouveau groupe avec une classification.</span><span class="sxs-lookup"><span data-stu-id="6f580-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="6f580-137">Consultez la rubrique [à l’aide de PowerShell avec Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) et [se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour plus d’informations sur l’utilisation d’Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f580-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="6f580-138">Une fois ces paramètres sont activés, le propriétaire du groupe sera en mesure de choisir une classification dans la liste déroulante menu dans Outlook sur le Web et d’Outlook et enregistrez-le à partir de la page **Modifier** du groupe.</span><span class="sxs-lookup"><span data-stu-id="6f580-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Choisissez la classification des groupes d’Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="6f580-140">Masquer les groupes d’Office 365 à partir de la liste d’adresses globale</span><span class="sxs-lookup"><span data-stu-id="6f580-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="6f580-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-141"></span></span>

<span data-ttu-id="6f580-p107">Vous pouvez spécifier si un groupe d’Office 365 apparaît dans la liste d’adresses globale (LAG) et d’autres listes au sein de votre organisation. Par exemple, si vous disposez d’un groupe du département juridique que vous ne voulez pas que s’affiche dans la liste d’adresses, vous pouvez arrêter ce groupe d’apparaître dans la liste d’adresses globale. Exécutez l’applet de commande groupe Set-Unified pour masquer le groupe à partir de la liste d’adresses similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="6f580-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="6f580-145">Autoriser uniquement les utilisateurs internes envoyer un message au groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="6f580-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-146"></span></span>

<span data-ttu-id="6f580-p108">Si vous ne voulez pas que les utilisateurs d’autres organisations pour envoyer un message électronique à un groupe d’Office 365, vous pouvez modifier les paramètres pour ce groupe. Elle permet uniquement les utilisateurs internes puissent envoyer un message électronique à votre groupe. Si vous essaient d’envoyer un message à ce groupe utilisateurs externes, ils seront rejetés.</span><span class="sxs-lookup"><span data-stu-id="6f580-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="6f580-150">Exécutez l’applet de commande Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit :</span><span class="sxs-lookup"><span data-stu-id="6f580-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="6f580-151">Ajouter des infos-courrier aux groupes d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="6f580-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-152"></span></span>

<span data-ttu-id="6f580-153">Lorsqu’un expéditeur essaie d’envoyer un message électronique à un groupe d’Office 365, une info-courrier peut être affichée pour eux.</span><span class="sxs-lookup"><span data-stu-id="6f580-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="6f580-154">Exécutez l’applet de commande pour ajouter une info-courrier au groupe Set-Unified groupe :</span><span class="sxs-lookup"><span data-stu-id="6f580-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="6f580-p109">Avec info-courrier, vous pouvez également définir MailTipTranslations, qui spécifie les langues supplémentaires pour l’info-courrier. Supposons que vous disposez de la traduction espagnole, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6f580-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="6f580-157">Modifier le nom complet du groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="6f580-p110">Nom d’affichage spécifie le nom du groupe d’Office 365. Vous pouvez voir ce nom dans votre centre d’administration exchange ou un portail d’administration d’Office 365. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe d’Office 365 existant en exécutant la commande Set-UnifiedGroup :</span><span class="sxs-lookup"><span data-stu-id="6f580-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="6f580-161">Modifier le paramètre par défaut d’Office 365 groupes pour Outlook Public ou privé</span><span class="sxs-lookup"><span data-stu-id="6f580-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="6f580-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="6f580-162"></span></span>

<span data-ttu-id="6f580-p111">Office 365 groupes dans Outlook sont créés comme étant privé par défaut. Si votre organisation souhaite Office 365 groupes peuvent être créés en tant que Public par défaut (ou en privé), utilisez cette syntaxe d’applet de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6f580-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="6f580-165">Pour définir privé :</span><span class="sxs-lookup"><span data-stu-id="6f580-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="6f580-166">Pour vérifier le paramètre :</span><span class="sxs-lookup"><span data-stu-id="6f580-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="6f580-167">Pour plus d’informations, voir [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) et [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="6f580-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="6f580-168">Applets de commande de groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="6f580-169">Les applets de commande suivante peut être utilisé avec Office 365 groupes.</span><span class="sxs-lookup"><span data-stu-id="6f580-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="6f580-170">**Nom de la cmdlet**</span><span class="sxs-lookup"><span data-stu-id="6f580-170">**Cmdlet name**</span></span>|<span data-ttu-id="6f580-171">**Description**</span><span class="sxs-lookup"><span data-stu-id="6f580-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="6f580-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="6f580-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="6f580-173">Utilisez cette applet de commande pour rechercher des groupes d’existants Office 365 et pour afficher les propriétés de l’objet de groupe</span><span class="sxs-lookup"><span data-stu-id="6f580-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="6f580-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="6f580-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="6f580-175">Mettre à jour les propriétés d’un groupe de 365 Office spécifique</span><span class="sxs-lookup"><span data-stu-id="6f580-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="6f580-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="6f580-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="6f580-p112">Créer un nouveau groupe d’Office 365. Cette applet de commande fournit un ensemble de paramètres minimal, pour le paramètre de valeurs pour les propriétés étendues utilisent Set-UnifiedGroup après la création du nouveau groupe</span><span class="sxs-lookup"><span data-stu-id="6f580-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="6f580-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="6f580-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="6f580-180">Supprimer un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="6f580-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="6f580-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="6f580-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="6f580-182">Récupérer des informations d’appartenance et le propriétaire d’un groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="6f580-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="6f580-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="6f580-184">Ajouter des centaines ou des milliers d’utilisateurs, ou de nouveaux propriétaires, à un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="6f580-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="6f580-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="6f580-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="6f580-186">Supprimer les propriétaires et les membres d’un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="6f580-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="6f580-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="6f580-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="6f580-p113">Permet d’afficher des informations sur la photo de l’utilisateur associée à un compte. Photos de l’utilisateur sont stockées dans Active Directory</span><span class="sxs-lookup"><span data-stu-id="6f580-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="6f580-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="6f580-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="6f580-p114">Utilisé pour associer une photo de l’utilisateur à un compte. Photos de l’utilisateur sont stockées dans Active Directory</span><span class="sxs-lookup"><span data-stu-id="6f580-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="6f580-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="6f580-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="6f580-194">Supprimer la photo d’un groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="6f580-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f580-195">Related topics</span></span>

[<span data-ttu-id="6f580-196">Listes de distribution de mise à niveau vers Office 365 groupes</span><span class="sxs-lookup"><span data-stu-id="6f580-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="6f580-197">Gérer les personnes autorisées à créer des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="6f580-198">Gérer l'accès invité aux groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="6f580-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="6f580-199">Modifier l’appartenance au groupe statique dynamique dans</span><span class="sxs-lookup"><span data-stu-id="6f580-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
