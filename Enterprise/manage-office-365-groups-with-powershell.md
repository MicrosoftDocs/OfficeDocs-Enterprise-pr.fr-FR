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
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="cb828-103">Utiliser PowerShell pour gérer les groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="cb828-104">*Dernière avril 18 mis à jour, 2018*</span><span class="sxs-lookup"><span data-stu-id="cb828-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="cb828-p101">Cet article fournit des instructions pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il indique également les applets de commande PowerShell pour les groupes. Pour obtenir des informations sur la gestion des sites SharePoint, voir [sites gérer SharePoint Online à l’aide de PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb828-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="cb828-108">Tâches courantes de gestion des groupes d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="cb828-109">Listes de distribution de mise à niveau vers Office 365 groupes</span><span class="sxs-lookup"><span data-stu-id="cb828-109">Upgrade distribution lists to Office 365 Groups</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [<span data-ttu-id="cb828-110">Gérer les personnes autorisées à créer des groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [<span data-ttu-id="cb828-111">Gérer l'accès invité aux groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [<span data-ttu-id="cb828-112">Gérer les groupes de façon dynamique dans Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="cb828-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="cb828-113">Ajouter des centaines, voire des milliers d’utilisateurs aux groupes d’Office 365, utilisez la [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="cb828-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="cb828-114">Lien vers votre directives d’utilisation de groupes de Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="cb828-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-115"></span></span>

<span data-ttu-id="cb828-p102">Lorsque les utilisateurs de [créer ou modifier un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez afficher les un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous exige un préfixe spécifique ou suffixe à ajouter à un nom de groupe.</span><span class="sxs-lookup"><span data-stu-id="cb828-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="cb828-p103">Utiliser Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365. Extrayez [d’Azure Active Directory des applets de commande pour configurer les paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir le lien hypertexte orientation de l’utilisation. Une fois vous avez exécuté l’applet de commande DAS, l’utilisateur sera voir le lien dans vos spécifications lorsqu’ils créent ou modifier un groupe dans Outlook.</span><span class="sxs-lookup"><span data-stu-id="cb828-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Créer un nouveau groupe avec liaison des instructions d’utilisation](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Cliquez sur les directives d’utilisation de groupe pour voir vos organisations instructions de groupes d’Office 365](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="cb828-123">Autoriser les utilisateurs à envoyer en tant que le groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="cb828-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-124"></span></span>

<span data-ttu-id="cb828-p104">Vous pouvez également procéder ainsi dans le centre d’administration Exchange. Voir [Autoriser les membres « Envoyer en tant que » ou « Envoyer de la part de » un groupe d’Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb828-p104">You can also do this in the Exchange Admin Center. See [Allow members to "Send as" or "Send on behalf of" an Office 365 Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span></span>
  
<span data-ttu-id="cb828-p105">Si vous souhaitez activer vos groupes d’Office 365 « Envoyer en tant que », utilisez le [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) et les applets de commande [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cette configuration. Une fois que vous activez ce paramètre, les utilisateurs de groupe de Office 365 peuvent utiliser Outlook ou Outlook sur le site web d’envoyer et de répondre aux messages que le groupe d’Office 365. Les utilisateurs peuvent accéder au groupe de créer un nouveau courrier électronique et de modifier le champ « Envoyer en tant que » à l’adresse de messagerie du groupe.</span><span class="sxs-lookup"><span data-stu-id="cb828-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="cb828-130">Vous devez ajouter l’adresse de messagerie du groupe dans le champ **Cc** lorsque vous composez le courrier électronique « Envoyer en tant que », afin que le message est envoyé au groupe et s’affiche dans des conversations de groupe.</span><span class="sxs-lookup"><span data-stu-id="cb828-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="cb828-131">À ce stade, la seule façon de mettre à jour la stratégie de boîte aux lettres est via [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb828-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="cb828-132">Utilisez cette commande pour définir l’alias de groupe.</span><span class="sxs-lookup"><span data-stu-id="cb828-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="cb828-133">Utilisez cette commande pour définir l’alias de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cb828-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="cb828-134">Cette commande permet de transmettre le groupalias à l’applet de commande Get-Recipient pour obtenir les détails du destinataire.</span><span class="sxs-lookup"><span data-stu-id="cb828-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="cb828-p106">Le nom du destinataire cible (nom du groupe) doit être transmis à la cmdlet Add-RecipientPermission. Useralias pour lesquels l’autorisation sendas bénéficiera sera attribué au paramètre - du client approuvé.</span><span class="sxs-lookup"><span data-stu-id="cb828-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="cb828-137">Une fois que l’applet de commande est exécutée, les utilisateurs peuvent aller à Outlook ou Outlook sur le web pour envoyer en tant que le groupe, en ajoutant l’adresse de messagerie de groupe pour **le champ** .</span><span class="sxs-lookup"><span data-stu-id="cb828-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="cb828-138">Créer des classifications pour les groupes d’Office dans votre organisation</span><span class="sxs-lookup"><span data-stu-id="cb828-138">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="cb828-p107">Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe d’Office 365. Par exemple, vous pouvez permettre aux utilisateurs de définir des « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Classifications de groupe ne sont pas définies par défaut et que vous devez créer dans l’ordre pour vos utilisateurs à définir. Utiliser Windows Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="cb828-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="cb828-143">Extrayez des [applets de commande Azure Active Directory pour la configuration des paramètres de groupe](https://go.microsoft.com/fwlink/?LinkID=827484) et suivez les étapes décrites dans les **paramètres de création au niveau du répertoire** pour définir la classification des groupes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="cb828-143">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="cb828-144">Pour associer une description à chaque classification que vous pouvez utiliser l’attribut *ClassificationDescriptions* pour définir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb828-144">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="cb828-145">Exemple :</span><span class="sxs-lookup"><span data-stu-id="cb828-145">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="cb828-146">Après avoir exécuté l’applet de commande pour définir votre classification Azure Active Directory ci-dessus, exécutez l’applet de commande [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) si vous souhaitez définir la classification pour un groupe spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb828-146">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="cb828-147">Ou créez un nouveau groupe avec une classification.</span><span class="sxs-lookup"><span data-stu-id="cb828-147">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="cb828-148">Consultez la rubrique [à l’aide de PowerShell avec Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) et [se connecter à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) pour plus d’informations sur l’utilisation d’Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb828-148">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="cb828-149">Une fois ces paramètres sont activés, le propriétaire du groupe sera en mesure de choisir une classification dans la liste déroulante menu dans Outlook sur le Web et d’Outlook et enregistrez-le à partir de la page **Modifier** du groupe.</span><span class="sxs-lookup"><span data-stu-id="cb828-149">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Choisissez la classification des groupes d’Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="cb828-151">Masquer les groupes d’Office 365 à partir de la liste d’adresses globale</span><span class="sxs-lookup"><span data-stu-id="cb828-151">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="cb828-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-152"></span></span>

<span data-ttu-id="cb828-p108">Vous pouvez spécifier si un groupe d’Office 365 apparaît dans la liste d’adresses globale (LAG) et d’autres listes au sein de votre organisation. Par exemple, si vous disposez d’un groupe du département juridique que vous ne voulez pas que s’affiche dans la liste d’adresses, vous pouvez arrêter ce groupe d’apparaître dans la liste d’adresses globale. Exécutez l’applet de commande groupe Set-Unified pour masquer le groupe à partir de la liste d’adresses similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="cb828-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="cb828-156">Autoriser uniquement les utilisateurs internes envoyer un message au groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-156">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="cb828-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-157"></span></span>

<span data-ttu-id="cb828-p109">Si vous ne voulez pas que les utilisateurs d’autres organisations pour envoyer un message électronique à un groupe d’Office 365, vous pouvez modifier les paramètres pour ce groupe. Elle permet uniquement les utilisateurs internes puissent envoyer un message électronique à votre groupe. Si vous essaient d’envoyer un message à ce groupe utilisateurs externes, ils seront rejetés.</span><span class="sxs-lookup"><span data-stu-id="cb828-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="cb828-161">Exécutez l’applet de commande Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit :</span><span class="sxs-lookup"><span data-stu-id="cb828-161">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="cb828-162">Ajouter des infos-courrier aux groupes d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-162">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="cb828-163"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-163"></span></span>

<span data-ttu-id="cb828-164">Lorsqu’un expéditeur essaie d’envoyer un message électronique à un groupe d’Office 365, une info-courrier peut être affichée pour lui.</span><span class="sxs-lookup"><span data-stu-id="cb828-164">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="cb828-165">Exécutez l’applet de commande groupe Set-Unified pour ajouter une info-courrier au groupe :</span><span class="sxs-lookup"><span data-stu-id="cb828-165">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="cb828-p110">Avec info-courrier, vous pouvez également définir MailTipTranslations, qui spécifie les langues supplémentaires pour l’info-courrier. Supposons que vous disposez de la traduction espagnole, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="cb828-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="cb828-168">Modifier le nom complet du groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-168">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="cb828-p111">Nom d’affichage spécifie le nom du groupe d’Office 365. Vous pouvez voir ce nom dans votre portail d’administration exchange admin center ou o365. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe d’Office 365 existant en exécutant la commande Set-UnifiedGroup :</span><span class="sxs-lookup"><span data-stu-id="cb828-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="cb828-172">Gérer les photos de l’utilisateur dans Office 365 groupes</span><span class="sxs-lookup"><span data-stu-id="cb828-172">Manage user photos in Office 365 Groups</span></span>

|<span data-ttu-id="cb828-173">**Nom de la cmdlet**</span><span class="sxs-lookup"><span data-stu-id="cb828-173">**Cmdlet name**</span></span>|<span data-ttu-id="cb828-174">**Description**</span><span class="sxs-lookup"><span data-stu-id="cb828-174">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="cb828-175">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cb828-175">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="cb828-p112">Permet d’afficher des informations sur la photo de l’utilisateur associée à un compte. Photos de l’utilisateur sont stockées dans Active Directory</span><span class="sxs-lookup"><span data-stu-id="cb828-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="cb828-178">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cb828-178">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="cb828-p113">Utilisé pour associer une photo de l’utilisateur à un compte. Photos de l’utilisateur sont stockées dans Active Directory</span><span class="sxs-lookup"><span data-stu-id="cb828-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="cb828-181">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cb828-181">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="cb828-182">Supprimer la photo d’un groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-182">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="cb828-183">Modifier le paramètre par défaut d’Office 365 groupes pour Outlook Public ou privé</span><span class="sxs-lookup"><span data-stu-id="cb828-183">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="cb828-184"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cb828-184"></span></span>

<span data-ttu-id="cb828-p114">Office 365 groupes dans Outlook sont créés comme étant privé par défaut. Si votre organisation souhaite Office 365 groupes Outlook être créé en tant que Public par défaut (ou à privée), utilisez cette syntaxe d’applet de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cb828-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="cb828-187">Pour définir privé :</span><span class="sxs-lookup"><span data-stu-id="cb828-187">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="cb828-188">Pour vérifier le paramètre :</span><span class="sxs-lookup"><span data-stu-id="cb828-188">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="cb828-189">Pour plus d’informations, voir [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) et [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="cb828-189">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="cb828-190">Applets de commande de groupes Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-190">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="cb828-p115">Les applets de commande suivantes ont été apportées récemment disponibles aux groupes d’Office 365. Si vous n’êtes pas en mesure d’utiliser ces, votre abonnement Office 365 n'a pas été encore mis à jour avec cette fonctionnalité. Vérifiez votre centre de messages et de la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).</span><span class="sxs-lookup"><span data-stu-id="cb828-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap).</span></span>
  
|<span data-ttu-id="cb828-194">**Nom de la cmdlet**</span><span class="sxs-lookup"><span data-stu-id="cb828-194">**Cmdlet name**</span></span>|<span data-ttu-id="cb828-195">**Description**</span><span class="sxs-lookup"><span data-stu-id="cb828-195">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="cb828-196">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cb828-196">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="cb828-197">Utilisez cette applet de commande pour rechercher des groupes d’existants Office 365 et pour afficher les propriétés de l’objet de groupe</span><span class="sxs-lookup"><span data-stu-id="cb828-197">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="cb828-198">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cb828-198">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="cb828-199">Mettre à jour les propriétés d’un groupe de 365 Office spécifique</span><span class="sxs-lookup"><span data-stu-id="cb828-199">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cb828-200">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cb828-200">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="cb828-p116">Créer un nouveau groupe d’Office 365. Cette applet de commande fournit un ensemble de paramètres minimal, pour le paramètre de valeurs pour les propriétés étendues utilisent Set-UnifiedGroup après la création du nouveau groupe</span><span class="sxs-lookup"><span data-stu-id="cb828-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="cb828-203">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cb828-203">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="cb828-204">Supprimer un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="cb828-204">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cb828-205">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cb828-205">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="cb828-206">Récupérer des informations d’appartenance et le propriétaire d’un groupe d’Office 365</span><span class="sxs-lookup"><span data-stu-id="cb828-206">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cb828-207">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cb828-207">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="cb828-208">Ajouter des centaines ou des milliers d’utilisateurs, ou de nouveaux propriétaires, à un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="cb828-208">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cb828-209">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cb828-209">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="cb828-210">Supprimer les propriétaires et les membres d’un groupe de 365 Office existant</span><span class="sxs-lookup"><span data-stu-id="cb828-210">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="cb828-211">Pour plus d’informations</span><span class="sxs-lookup"><span data-stu-id="cb828-211">For more information</span></span>

[<span data-ttu-id="cb828-212">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb828-212">Manage Office 365 with Office 365 PowerShell</span></span>](powershell/manage-office-365-with-office-365-powershell.md)
