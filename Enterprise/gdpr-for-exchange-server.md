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
# <a name="gdpr-for-exchange-server"></a>RGPD pour Exchange Server

Dans le cadre de la protection des informations personnelles, nous vous recommandons d’effectuer les tâches suivantes :

-   Utilisez des [balises et stratégies de rétention](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx) dans Exchange Server pour implémenter une stratégie de cycle de vie messagerie.

-   Appliquez la [gestion des droits relatifs à l'information](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx) pour limiter l’accès aux informations stockées dans Exchange Server.

-   Activez le [chiffrement BitLocker](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/) sur vos serveurs.

## <a name="identifying-in-scope-content"></a>Identification du contenu concerné

Exchange utilise deux référentiels de stockage principaux pour le contenu généré par les utilisateurs finaux : les boîtes aux lettres et les dossiers publics. Le contenu stocké dans la boîte aux lettres d’un utilisateur individuel est associé de façon unique à cet utilisateur et représente son référentiel par défaut dans Exchange. Les données stockées dans la boîte aux lettres d’un utilisateur incluent du contenu créé à l’aide d’Outlook, des clients Outlook sur le web (anciennement Outlook Web App), Exchange ActiveSync, Skype Entreprise et d’autres outils tiers qui se connectent aux serveurs Exchange par le biais des protocoles POP ou IMAP, ou des services web Exchange. Voici quelques exemples de ces éléments de contenu : messages, éléments de calendrier (réunions et rendez-vous), contacts, notes et tâches. La suppression de boîte aux lettres d’un utilisateur individuel supprime le contenu qu’il a généré ou qui lui a été directement envoyé dans sa boîte aux lettres. Vous pouvez supprimer les boîtes aux lettres d’utilisateur par le biais du centre d’administration Exchange ou de la cmdlet [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) dans l’environnement de ligne de commande Exchange Management Shell.\
Remarque : le paramètre Permanent sur la cmdlet Remove-Mailbox doit être utilisé avec précaution, car les données ne sont pas récupérables lorsque cette option est utilisée.

Exchange propose également des boîtes aux lettres partagées qui autorisent l’accès à un ou plusieurs utilisateurs, de façon à ce qu’ils puissent envoyer et recevoir du contenu stocké dans une boîte aux lettres commune. La boîte aux lettres partagée est une entité unique non liée à un seul compte. Au lieu de cela, plusieurs utilisateurs y ont accès pour envoyer, recevoir et consulter des e-mails dans la boîte aux lettres partagée. Les boîtes aux lettres partagées sont gérées par le biais du centre d’administration Exchange et des cmdlets permettant de gérer des boîtes aux lettres utilisateur ordinaires. Si vous avez besoin de supprimer des messages personnels d’une boîte aux lettres, plusieurs options s’offrent à vous en fonction de la version d’Exchange. Dans Exchange Server 2010 et 2013, vous pouvez utiliser la cmdlet [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) avec le paramètre DeleteContent pour identifier et supprimer des messages d’une boîte aux lettres. Dans Exchange Server 2016 et les versions ultérieures, vous devez utiliser la fonctionnalité [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx).

Les dossiers publics consistent en une implémentation de stockage partagé qui n'est pas associée à un utilisateur spécifique. Les utilisateurs bénéficient d’un accès aux dossiers publics afin de générer du contenu. L’implémentation effective des dossiers publics varie en fonction de la version d’Exchange (Exchange Server 2010 utilise une autre implémentation qu’Exchange Server 2013 et les versions ultérieures). Il existe des outils limités qui permettent de gérer le contenu des dossiers publics. Les outils client (par exemple, Outlook) constituent le moyen principal de gérer le contenu des dossiers publics. Il existe des cmdlets pour gérer les objets des dossiers publics, mais pas pour gérer les éléments de contenu personnels d’un dossier public. Un script personnalisé basé sur les services web Exchange ou sur d’autres outils tiers sera probablement nécessaire pour gérer les éléments personnels des dossiers publics.

La première chose que vous devrez faire sera de gérer le contenu de la boîte aux lettres d’un utilisateur individuel. Vous pourrez le faire facilement à l’aide des outils graphiques ou des cmdlets que vous utilisez régulièrement pour gérer les boîtes aux lettres. Si vous devez traiter du contenu dans plusieurs boîtes aux lettres ou dans plusieurs types de ressources, [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx) est la fonctionnalité la plus adaptée dans Exchange pour identifier le contenu concerné.

## <a name="deleted-item-retention"></a>Rétention des éléments supprimés

Lorsque vous supprimez des éléments ou des messages personnels d’une boîte aux lettres (pas la boîte aux lettres entière ou la ressource du dossier public même), le contenu est conservé dans un format récupérable en fonction de la valeur du paramètre DeletedItemRetention pour la base de données de la boîte aux lettres ou celle du dossier public. La valeur par défaut est de 14 jours, mais elle peut être configurée par un administrateur Exchange.

## <a name="removing-soft-deleted-and-disconnected-mailboxes"></a>Suppression de boîtes aux lettres supprimées (récupérables) et déconnectées

Lorsqu’une boîte aux lettres Exchange est désactivée, supprimée ou déplacée d’une base de données à une autre (par exemple, pour l’équilibrage de charge), elle est placée en état désactivé, supprimé (récupérable) ou déconnecté en fonction de l’opération. Lorsque la boîte aux lettres se trouve dans un de ces états, Exchange la traite (elle et son contenu) en fonction de la valeur actuelle du paramètre MailboxRetention spécifiée dans la base de données de la boîte aux lettres. La valeur par défaut est de 30 jours, mais elle peut être configurée par un administrateur Exchange. Vous pouvez utiliser la cmdlet [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) pour forcer Exchange à supprimer définitivement (purger) toutes les données associées à la boîte aux lettres avant que la période de rétention n’expire naturellement.

> [!IMPORTANT]
> Dans la mesure où la cmdlet Remove-StoreMailbox entraîne une perte de données définitive, utilisez-la avec précaution. 

## <a name="on-prem-to-cloud-migrations"></a>Migrations depuis votre ordinateur vers le cloud

Lors de la migration de données depuis Exchange Server vers Exchange Online, les données migrées peuvent continuer à se trouver dans le serveur local Exchange Server source dans un format récupérable par un administrateur Exchange. Par défaut, ces données seront automatiquement supprimées de la base de données au bout de 30 jours (reportez-vous à la section Suppression de boîtes aux lettres supprimées (récupérables) et déconnectées ci-dessus).

## <a name="automatic-data-collection-reported-to-microsoft-by-exchange-server"></a>Rapports automatiques de collecte de données envoyés à Microsoft par Exchange Server

Les serveurs Exchange Server déployés dans des environnements locaux ne fournissent aucun type de capture de données des utilisateurs finaux ou de rapports automatiques à Microsoft. Les serveurs Exchange Server dont la fonction de rapport de vidage sur incident Watson est activée sur le système d’exploitation Windows peuvent recevoir des contenus de mémoire limités lors de la génération du rapport d’incident.
