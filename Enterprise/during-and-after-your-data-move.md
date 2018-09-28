---
title: Pendant et après le déplacement de vos données
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Les déplacements de données sont des opérations principales n'ayant que peu d'impact sur les utilisateurs finals. Aucune action de votre part n'est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l'avance, et n'ont qu'une incidence minimale sur les utilisateurs.
ms.openlocfilehash: 0c715e80acbac126626c73a75fac1bbc809367e2
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975172"
---
# <a name="during-and-after-your-data-move"></a>Pendant et après le déplacement de vos données

Les déplacements de données sont des opérations principales n'ayant que peu d'impact sur les utilisateurs finals. Aucune action de votre part n'est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l'avance, et n'ont qu'une incidence minimale sur les utilisateurs.
  
> [!NOTE]
> Le déplacement se produit à différents moments pour chaque service. Par conséquent, vous ne verrez pas la description des fonctionnalités réduites pour chaque service au même moment. 
  
Surveillez le centre de messages Office 365 dans l'attente de la confirmation de la fin du déplacement de chaque service Exchange Online, SharePoint Online et Skype Entreprise. Comme indiqué dans le tableau ci-dessous, le déplacement de toutes les données pour tous les clients dans une zone géographique spécifique peut prendre jusqu'à 24 mois à compter de la fin de la période d'inscription. Si vous rencontrez des problèmes avec votre client après le déplacement, contactez le [support Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour obtenir de l'aide. 
  

|**Clients avec une adresse de facturation en/au**|**Tous les déplacements terminés d'ici le**|
|:-----|:-----|
|Australie, Nouvelle-Zélande, Fidji  <br/> |31 octobre 2017  <br/> |
|Japon  <br/> |31 octobre 2018  <br/> |
|Inde  <br/> |31 octobre 2018  <br/> |
|Canada  <br/> |31 octobre 2018  <br/> |
|Corée du Sud  <br/> |31 octobre 2018  <br/> |
|Royaume-Uni  <br/> |15 septembre 2019  <br/> |
|France  <br/> |15 septembre 2020  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>Déplacements impliquant un fournisseur de services d'audioconférence tiers

- Les services de module complémentaire de fournisseurs de services d'audioconférence tiers pour Skype Entreprise ne sont pas disponibles pour les utilisateurs hébergés dans des centres de données propres à une nouvelle zone géographique. 
    
- Les clients existants qui utilisent un service de fournisseur de services d'audioconférence tiers ne doivent pas demander de déplacement vers un centre de données propre à une nouvelle zone géographique. 
    
- Les nouveaux clients déployés dans les centres de données propres à une nouvelle zone géographique doivent demander un déplacement vers un centre de données régional afin d'utiliser un fournisseur de services d'audioconférence tiers. 
    
## <a name="exchange-online"></a>Exchange Online

Comme le déplacement de chaque utilisateur vers la nouvelle zone géographique de centres de données pour un seul client prend du temps, certains utilisateurs seront encore dans l'ancienne zone géographique de centres de données pendant le déplacement, tandis que d'autres seront dans la nouvelle. Par conséquent, certaines fonctionnalités impliquant l'accès à plusieurs boîtes aux lettres ne fonctionneront pas totalement pendant une période du processus de déplacement, laquelle peut durer plusieurs semaines. Ces fonctionnalités sont décrites dans les sections suivantes.
  
### <a name="mailbox-move"></a>Déplacement de boîte aux lettres

Quand une boîte aux lettres individuelles passe d'une zone géographique de centres de données à une autre, son contenu est d'abord préconfiguré afin que les données existantes soient copiées dans la zone géographique cible sans répercussions sur la boîte aux lettres. Au moment du basculement vers la zone géographique cible, la boîte aux lettres qui se trouve dans la zone géographique source est verrouillée pendant quelques minutes. Pendant cette période, les clients de messagerie ne peuvent pas se connecter. Les modifications supplémentaires sont copiées vers la zone géographique cible et le déplacement se termine. Il n'y a aucune interruption du flux de messages lors du déplacement.
  
Vous devrez redémarrer bureau Outlook une fois la boîte aux lettres est déplacée, comme décrit dans [l’article de la Base de connaissances 2591913](https://support.microsoft.com/kb/2591913)certains utilisateurs.
  
### <a name="shared-mailbox"></a>Boîte aux lettres partagée

Les utilisateurs ayant l'autorisation « Accès complet » aux boîtes aux lettres partagées ne sont pas touchés lors du déplacement.
  
### <a name="resource-mailbox"></a>Boîte aux lettres de ressources

Un utilisateur qui doit gérer les configurations de boîte aux lettres de ressources via la page Options d'Outlook Web Access peut continuer de le faire lors du déplacement.
  
Si les boîtes aux lettres de ressources sont gérées directement via des cmdlets Exchange, les cmdlets Set-MailboxRegionalConfiguration et Set-MailboxCalendarConfiguration ne fonctionnent pas si l'utilisateur et la boîte aux lettres de ressources se trouvent dans des zones géographiques différentes.
  
### <a name="calendar-delegation"></a>Délégation de calendrier

Le statut de disponibilité et le partage de calendrier ne sont pas touchés lors du déplacement du client. Un utilisateur A disposant d'autorisations d'écriture dans le dossier de calendrier de la boîte aux lettres B peut toujours gérer celui-ci à l'aide de l'application de bureau Outlook. Toutefois, lors du déplacement, si l'utilisateur A et la boîte aux lettres B ne sont pas dans la même zone géographique, l'utilisateur A ne peut pas modifier le calendrier de la boîte aux lettres B dans Outlook Web Access jusqu'à ce qu'ils soient tous les deux déplacés vers la zone géographique cible.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Ouvrez « Dossier partagé » dans Outlook Web Access

Certains utilisateurs ouvrent un dossier de messagerie partagé à partir d'une autre boîte aux lettres (sur laquelle l'utilisateur a des autorisations en lecture ou en écriture) dans Outlook Web Access à l'aide de la fonctionnalité « Dossier partagé ». Le tableau suivant indique comment fonctionne l'accès aux dossiers partagés au cours d'un déplacement de boîte aux lettres. Notez que les utilisateurs disposant d'autorisations complètes sur une boîte aux lettres partagée peuvent ouvrir la boîte aux lettres à l'aide d'Outlook Web Access lors du déplacement. 
  
|**Configuration**|**Description**|
|:-----|:-----|
|L'utilisateur dispose d'autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l'utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même zone géographique lors du déplacement de client, l'utilisateur A ne peut pas ouvrir le dossier la boîte aux lettres B dans Outlook Web Access s'il n'a de droit d'accès que pour un dossier spécifique de la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d'utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d'accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l'utilisateur A dispose de droits d'accès complet sur la boîte aux lettres B, il peut cliquer sur le dossier partagé dans le volet de navigation gauche d'Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  <br/> > [!NOTE]> Un utilisateur peut ouvrir une boîte aux lettres partagée à l'aide d'Outlook Web Access lors du déplacement sans aucun impact négatif. La limitation s'applique uniquement au partage au niveau du dossier dans une boîte aux lettres.           |
   
### <a name="public-folders"></a>Dossiers publics

Si la boîte aux lettres de dossier public se trouve temporairement dans une autre zone géographique de centre de données que l'utilisateur qui tente d'y accéder, l'utilisateur ne peut pas accéder à la boîte aux lettres. 
  
### <a name="online-archives"></a>Archives en ligne

Lorsque le déplacement est en cours, les utilisateurs se connectant via Outlook Web Access ne peuvent pas se connecter à leur boîte aux lettres d'archivage en ligne. L'accès à la boîte aux lettres d'archivage pour les utilisateurs se connectant avec Outlook est pris en charge.
  
### <a name="ediscovery-amp-auditing"></a>découverte électronique &amp; d’audit

La découverte et l’audit des fonctionnalités de sécurité Office 365 &amp; déplace client de cross-localisés de prise en charge de centre de conformité. interroger les utilisateurs qui ne sont pas déplacées encore une fois que le client déplacer a commencé à la différence du centre d’administration Exchange (CAE), qui ne prend en charge. Pour plus d’informations sur la sécurité &amp; centre de conformité, voir [Office 365 sécurité &amp; centre de conformité](https://go.microsoft.com/fwlink/p/?linkid=841313). 
  
Le tableau suivant vous montre comment accéder aux eDiscovery et l’audit par le biais de la sécurité et le CAE &amp; centre de conformité.
  
||**Centre d'administration Exchange**|**Sécurité &amp; centre de conformité**|
|:-----|:-----|:-----|
|eDiscovery  <br/> | Accédez à https://portal.office.com, puis cliquez sur la vignette de **l’administrateur** . <br/> Cliquez sur **Admin centres** \> **Exchange**. <br/> Sélectionnez **gestion de la conformité** \> **archives permanentes &amp; contenir**. | Accédez à https://portal.office.com, puis cliquez sur la vignette d’administration. <br/> Cliquez sur **Admin centres** \> **sécurité &amp; conformité**. <br/> Sélectionnez **recherche &amp; enquête** \> **eDiscovery**.|
|Audit  <br/> | Accédez à https://portal.office.com, puis cliquez sur la vignette de **l’administrateur** . <br/> Cliquez sur **Admin centres** \> **Exchange**. Sélectionnez **gestion de la conformité** \> **l’audit**. | Accédez à https://portal.office.com, puis cliquez sur la vignette d’administration. <br/> Cliquez sur **Admin centres** \> **sécurité &amp; conformité**. <br/> Sélectionnez **recherche &amp; enquête** \> **recherche des journaux d’Audit**. |
   
### <a name="mailbox-migration"></a>Migration des boîtes aux lettres

Lorsqu’un client se déplace entre des zones géographiques, un lot de migration peut indiquer les erreurs sur certains utilisateurs du lot de migration qui sont laissés dans la zone géographique source. Dans ce cas, supprimez le lot migration pour supprimer la demande de synchronisation sous-jacente. Une fois que le lot est entièrement éliminé, créez-le lot de nouveau. Cette opération lance la création de demandes de synchronisation dans la zone géographique cible.
  
## <a name="sharepoint-online"></a>SharePoint Online

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise
    
- Project Online
    
- Project pour Office 365
    
- Services vidéo Office 365
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro pour Office 365
    
Une fois que nous aurons déplacé vos données SharePoint Online, vous pourrez éventuellement observer certains des effets suivants.
  
### <a name="office-365-video-services"></a>Services vidéo Office 365

- Le déplacement de vidéos prend plus de temps que le déplacement d'autres contenus dans SharePoint Online.
    
- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.
    
- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.
    
### <a name="search"></a>Rechercher

Dans le cadre du déplacement de vos données SharePoint Online, nous migrons vos paramètres de recherche et d'index vers un nouvel emplacement. Jusqu'à la **fin** du déplacement de vos données SharePoint Online, nous continuons de desservir vos utilisateurs depuis l'index situé dans l'emplacement d'origine. Dans le nouvel emplacement, la fonction recherche démarre automatiquement une analyse de votre contenu une fois le déplacement de vos données SharePoint Online terminé. À ce moment-là, nous desservirons vos utilisateurs depuis l'index migré. Les modifications apportées à votre contenu après la migration ne sont pas prises en compte dans l'index migré tant que l'analyse ne les a pas récupérées. La plupart des clients ne remarquent pas que les résultats proposent des contenus moins récents immédiatement après la migration de leurs données SharePoint Online, mais certains peuvent s'en apercevoir au cours des 24-48 premières heures d'utilisation. 
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n'incluent pas les modifications qui se sont produites après la migration jusqu'à ce que l'analyse les ait récupérées. 
    
- Delve : Delve n'inclut pas les modifications qui se sont produites après la migration jusqu'à ce que l'analyse les ait récupérées.
    
- Rapports de popularité et de recherche pour le site : le nombre de rapports Excel situés dans le nouvel emplacement prend uniquement en compte le nombre de rapports migrés et de rapports d'utilisation exécutés après le déplacement de vos données SharePoint Online. Le nombre de rapports existant pendant la période de transition est perdu et ne peut pas être récupéré. Cette période correspond généralement à quelques jours. Certains clients peuvent constater des pertes plus courtes ou plus longues.
    
- Portail vidéo : les nombres et les statistiques de vue dépendent des statistiques des rapports Excel. Par conséquent, ils sont perdus pendant le même nombre de jours que les rapports Excel.
    
- eDiscovery (découverte électronique) : Les éléments modifiés au cours de la migration ne sont pas affichés avant que l'analyse n'ait récupéré les modifications.
    
- Protection contre la perte de données (DLP) : Les politiques ne sont pas appliquées sur les éléments qui changent avant que l'analyse n'ait récupéré les modifications.
    
## <a name="skype-for-business"></a>Skype Entreprise

Tous les utilisateurs seront déconnectés du logiciel client Skype Entreprise pendant le basculement. La connexion automatique permettra aux utilisateurs de se reconnecter dans les deux minutes qui suivent.
  
|**Fonctionnalités disponibles pendant l'intégralité du déplacement**|**Fonctionnalités pouvant être limitées pendant une partie du déplacement**|
|:-----|:-----|
| Messagerie instantanée et appels vocaux  <br/>  Les utilisateurs peuvent ajouter des contacts, des groupes de contacts et des réunions, ainsi qu'indiquer leur emplacement et modifier le texte dans « Activités du jour ».  <br/>  Les paramètres du fournisseur de services d'audioconférence sont copiés vers la zone géographique de centres de données cible. Si le fournisseur de services d'audioconférence est présent dans le centre de données cible, la fonctionnalité sera disponible. Sinon, vous ne pourrez pas l'utiliser.  <br/> | Les administrateurs ne pourront pas se servir de la fonctionnalité TRPS (PowerShell client à distance) d’administration des clients pour créer des sessions.  <br/>  Les administrateurs ne pourront pas utiliser la fonctionnalité LAC de l'administrateur client pour se connecter et modifier les paramètres utilisateur.  <br/> |
   
|**Après le déplacement**|
|:-----|
| Les données de la réunion (présentations téléchargées, etc.) ne seront pas déplacées et devront être téléchargées à nouveau.  <br/>  Les clients Lync plus anciens, tels que les clients Lync 2010 et Lync pour Mac 2011, mettent en cache des informations DNS dans le service, ce qui entraîne des problèmes de connexion. Le cache DNS devra peut-être être effacé si l'utilisateur ne se trouve pas sur le dernier client Windows de Skype Entreprise. Vous devez indiquer aux utilisateurs d'exécuter l' [assistant de dépannage](https://support.microsoft.com/en-us/kb/2541980) et de suivre les instructions relatives à l'effacement du cache client. Les utilisateurs de Lync pour Mac doivent suivre [ces instructions](https://support.microsoft.com/en-us/kb/2629861).  <br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>Données d'autres services, notamment Yammer et Power BI

Nous déplaçons uniquement les données client pour Exchange Online, SharePoint Online et Skype Entreprise. Nous ne déplaçons pas de données pour d'autres services. En tant que client ou utilisateur de ces autres services, vous ne remarquez aucune modification ou aucune conséquence. Le processus de déplacement n'a aucune incidence sur ces services et l'emplacement des données client reste le même.
  
## <a name="related-topics"></a>Voir aussi 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/en-us/regions/)

