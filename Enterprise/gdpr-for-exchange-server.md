---
title: RGPD pour Exchange Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Découvrez comment satisfaire aux exigences du RGPD pour l’environnement Exchange Server local.
ms.openlocfilehash: cf6d670134bd4aab60b97cd9f55e69a21ce06b19
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-exchange-server"></a><span data-ttu-id="a7e5a-103">RGPD pour Exchange Server</span><span class="sxs-lookup"><span data-stu-id="a7e5a-103">GDPR for Exchange Server</span></span>

<span data-ttu-id="a7e5a-104">Dans le cadre de la protection des informations personnelles, nous vous recommandons d’effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="a7e5a-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="a7e5a-105">Utilisez des [balises et stratégies de rétention](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx) dans Exchange Server pour implémenter une stratégie de cycle de vie messagerie.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-105">Use [Retention Tags and Policies](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx) in Exchange Server to implement an email life cycle policy.</span></span>

-   <span data-ttu-id="a7e5a-106">Appliquez la [gestion des droits relatifs à l'information](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx) pour limiter l’accès aux informations stockées dans Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-106">Deploy [Information Rights Management](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx) to limit who has access to information stored in Exchange Server.</span></span>

-   <span data-ttu-id="a7e5a-107">Activez le [chiffrement BitLocker](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/) sur vos serveurs.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-107">Enable [BitLocker encryption](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/) on your servers.</span></span>

## <a name="identifying-in-scope-content"></a><span data-ttu-id="a7e5a-108">Identification du contenu concerné</span><span class="sxs-lookup"><span data-stu-id="a7e5a-108">Identifying In-scope Content</span></span>

<span data-ttu-id="a7e5a-p101">Exchange utilise deux référentiels de stockage principaux pour le contenu généré par les utilisateurs finaux : les boîtes aux lettres et les dossiers publics. Le contenu stocké dans la boîte aux lettres d’un utilisateur individuel est associé de façon unique à cet utilisateur et représente son référentiel par défaut dans Exchange. Les données stockées dans la boîte aux lettres d’un utilisateur incluent du contenu créé à l’aide d’Outlook, des clients Outlook sur le web (anciennement Outlook Web App), Exchange ActiveSync, Skype Entreprise et d’autres outils tiers qui se connectent aux serveurs Exchange par le biais des protocoles POP ou IMAP, ou des services web Exchange. Voici quelques exemples de ces éléments de contenu : messages, éléments de calendrier (réunions et rendez-vous), contacts, notes et tâches. La suppression de boîte aux lettres d’un utilisateur individuel supprime le contenu qu’il a généré ou qui lui a été directement envoyé dans sa boîte aux lettres. Vous pouvez supprimer les boîtes aux lettres d’utilisateur par le biais du centre d’administration Exchange ou de la cmdlet [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) dans l’environnement de ligne de commande Exchange Management Shell.\\</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p101">Exchange uses two primary storage repositories for end user generated content: mailboxes and public folders. Content stored in an individual user’s mailbox is uniquely associated to that user and represents their default repository within Exchange. The data stored in a user mailbox includes content created using Outlook, Outlook on the web (formerly known as Outlook Web App), Exchange ActiveSync, Skype for Business clients and other third-party tools that connect to Exchange servers using POP, IMAP or Exchange Web Services (EWS). Examples of these items include: messages, calendar items (meetings and appointments), contacts, notes and tasks. Deleting an individual user’s mailbox removes content generated by or sent directly to the user in the context of their mailbox. You can delete user mailboxes by using the Exchange admin center (EAC) or the [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) cmdlet in the Exchange Management Shell.\\</span></span>
<span data-ttu-id="a7e5a-115">Remarque : le paramètre Permanent sur la cmdlet Remove-Mailbox doit être utilisé avec précaution, car les données ne sont pas récupérables lorsque cette option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-115">Note: The Permanent parameter on the Remove-Mailbox cmdlet should be used with caution as the data will not be recoverable if this option is used.</span></span>

<span data-ttu-id="a7e5a-p102">Exchange propose également des boîtes aux lettres partagées qui autorisent l’accès à un ou plusieurs utilisateurs, de façon à ce qu’ils puissent envoyer et recevoir du contenu stocké dans une boîte aux lettres commune. La boîte aux lettres partagée est une entité unique non liée à un seul compte. Au lieu de cela, plusieurs utilisateurs y ont accès pour envoyer, recevoir et consulter des e-mails dans la boîte aux lettres partagée. Les boîtes aux lettres partagées sont gérées par le biais du centre d’administration Exchange et des cmdlets permettant de gérer des boîtes aux lettres utilisateur ordinaires. Si vous avez besoin de supprimer des messages personnels d’une boîte aux lettres, plusieurs options s’offrent à vous en fonction de la version d’Exchange. Dans Exchange Server 2010 et 2013, vous pouvez utiliser la cmdlet [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) avec le paramètre DeleteContent pour identifier et supprimer des messages d’une boîte aux lettres. Dans Exchange Server 2016 et les versions ultérieures, vous devez utiliser la fonctionnalité [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx).</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p102">Exchange also provides shared mailboxes that allow one or more users access to send and receive content that’s stored in a common mailbox. The shared mailbox is a unique entity that’s not associated with a single account. Instead, multiple users are granted access to send, receive and review email content in the shared mailbox. Shared mailboxes are administered using the Exchange admin center and the same cmdlets used to manage regular user mailboxes. If you need to remove individual messages from a mailbox, there are different options available depending upon the version of Exchange. In Exchange Server 2010 and 2013, you can use the [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) cmdlet with the DeleteContent parameter to identify and remove messages from a mailbox. In Exchange Server 2016 and later, you need to use the [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx) functionality.</span></span>

<span data-ttu-id="a7e5a-p103">Les dossiers publics consistent en une implémentation de stockage partagé qui n'est pas associée à un utilisateur spécifique. Les utilisateurs bénéficient d’un accès aux dossiers publics afin de générer du contenu. L’implémentation effective des dossiers publics varie en fonction de la version d’Exchange (Exchange Server 2010 utilise une autre implémentation qu’Exchange Server 2013 et les versions ultérieures). Il existe des outils limités qui permettent de gérer le contenu des dossiers publics. Les outils client (par exemple, Outlook) constituent le moyen principal de gérer le contenu des dossiers publics. Il existe des cmdlets pour gérer les objets des dossiers publics, mais pas pour gérer les éléments de contenu personnels d’un dossier public. Un script personnalisé basé sur les services web Exchange ou sur d’autres outils tiers sera probablement nécessaire pour gérer les éléments personnels des dossiers publics.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p103">Public folders are a shared storage implementation that’s not associated with a specific user. Instead, users are granted access to public folders to generate content. The actual implementation of public folders varies depending upon the version of Exchange (Exchange Server 2010 uses a different implementation than Exchange Server 2013 and later). Limited tools exist to manage the content in public folders. Client tools (for example, Outlook) are the primary mechanism for managing content in public folders. There are cmdlets for managing public folder objects, but not for managing individual content items within the public folder. A custom script that leverages Exchange Web Services (EWS) or other third-party tools will likely be needed to manage individual public folder items.</span></span>

<span data-ttu-id="a7e5a-p104">La première chose que vous devrez faire sera de gérer le contenu de la boîte aux lettres d’un utilisateur individuel. Vous pourrez le faire facilement à l’aide des outils graphiques ou des cmdlets que vous utilisez régulièrement pour gérer les boîtes aux lettres. Si vous devez traiter du contenu dans plusieurs boîtes aux lettres ou dans plusieurs types de ressources, [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx) est la fonctionnalité la plus adaptée dans Exchange pour identifier le contenu concerné.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p104">The primary requirement will likely be managing individual user mailbox content. This requirement will be easily addressed through the graphical or cmdlet-based tools that you regularly use to manage mailboxes. If you need to process content across multiple mailboxes or types of resources, [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx) is the preferred mechanism within Exchange to identify in-scope content.</span></span>

## <a name="deleted-item-retention"></a><span data-ttu-id="a7e5a-133">Rétention des éléments supprimés</span><span class="sxs-lookup"><span data-stu-id="a7e5a-133">Deleted Item Retention</span></span>

<span data-ttu-id="a7e5a-p105">Lorsque vous supprimez des éléments ou des messages personnels d’une boîte aux lettres (pas la boîte aux lettres entière ou la ressource du dossier public même), le contenu est conservé dans un format récupérable en fonction de la valeur du paramètre DeletedItemRetention pour la base de données de la boîte aux lettres ou celle du dossier public. La valeur par défaut est de 14 jours, mais elle peut être configurée par un administrateur Exchange.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p105">When you delete individual messages or items from a mailbox (not the entire mailbox or public folder resource itself) the content is retained in a recoverable form based on the value of the DeletedItemRetention parameter for the mailbox database or public folder database. The default value is 14 days, but this value is configurable by an Exchange administrator.</span></span>

## <a name="removing-soft-deleted-and-disconnected-mailboxes"></a><span data-ttu-id="a7e5a-136">Suppression de boîtes aux lettres supprimées (récupérables) et déconnectées</span><span class="sxs-lookup"><span data-stu-id="a7e5a-136">Removing Soft-Deleted and Disconnected Mailboxes</span></span>

<span data-ttu-id="a7e5a-p106">Lorsqu’une boîte aux lettres Exchange est désactivée, supprimée ou déplacée d’une base de données à une autre (par exemple, pour l’équilibrage de charge), elle est placée en état désactivé, supprimé (récupérable) ou déconnecté en fonction de l’opération. Lorsque la boîte aux lettres se trouve dans un de ces états, Exchange la traite (elle et son contenu) en fonction de la valeur actuelle du paramètre MailboxRetention spécifiée dans la base de données de la boîte aux lettres. La valeur par défaut est de 30 jours, mais elle peut être configurée par un administrateur Exchange. Vous pouvez utiliser la cmdlet [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) pour forcer Exchange à supprimer définitivement (purger) toutes les données associées à la boîte aux lettres avant que la période de rétention n’expire naturellement.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p106">When an Exchange mailbox is disabled, deleted or moved between databases (for example, as a part of load balancing), the mailbox is placed into a disabled, soft-deleted or disconnected state depending on the operation. While the mailbox is in any of these states, Exchange maintains the mailbox (which includes its contents) based on the current value of the MailboxRetention parameter that’s specified on the mailbox database. The default value is 30 days, but this value is configurable by an Exchange administrator. You can use the [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) cmdlet to force Exchange to permanently remove (purge) all data associated with a mailbox prior to the retention period expiring naturally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7e5a-141">Dans la mesure où la cmdlet Remove-StoreMailbox entraîne une perte de données définitive, utilisez-la avec précaution.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-141">Use the Remove-StoreMailbox cmdlet with caution as it results in an unrecoverable loss of data for the target mailbox.</span></span> 

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="a7e5a-142">Migrations depuis votre ordinateur vers le cloud</span><span class="sxs-lookup"><span data-stu-id="a7e5a-142">On-Prem to Cloud Migrations</span></span>

<span data-ttu-id="a7e5a-p107">Lors de la migration de données depuis Exchange Server vers Exchange Online, les données migrées peuvent continuer à se trouver dans le serveur local Exchange Server source dans un format récupérable par un administrateur Exchange. Par défaut, ces données seront automatiquement supprimées de la base de données au bout de 30 jours (reportez-vous à la section Suppression de boîtes aux lettres supprimées (récupérables) et déconnectées ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p107">While migrating data from Exchange Server to Exchange Online, migrated data may continue to reside on the source on-premises Exchange Server in a form that’s recoverable by an Exchange administrator. By default, this data will be automatically removed from the database within 30 days (see the Removing Soft-Deleted and Disconnected Mailboxes section above).</span></span>

## <a name="automatic-data-collection-reported-to-microsoft-by-exchange-server"></a><span data-ttu-id="a7e5a-145">Rapports automatiques de collecte de données envoyés à Microsoft par Exchange Server</span><span class="sxs-lookup"><span data-stu-id="a7e5a-145">Automatic Data Collection Reported to Microsoft by Exchange Server</span></span>

<span data-ttu-id="a7e5a-p108">Les serveurs Exchange Server déployés dans des environnements locaux ne fournissent aucun type de capture de données des utilisateurs finaux ou de rapports automatiques à Microsoft. Les serveurs Exchange Server dont la fonction de rapport de vidage sur incident Watson est activée sur le système d’exploitation Windows peuvent recevoir des contenus de mémoire limités lors de la génération du rapport d’incident.</span><span class="sxs-lookup"><span data-stu-id="a7e5a-p108">Exchange Servers deployed in on-premises environments do not provide any type of automated reporting or end user data capture to Microsoft. Exchange Servers that have Watson crash dump reporting enabled in the Windows Operating System may receive limited contents of memory at the time the crash report is produced.</span></span>