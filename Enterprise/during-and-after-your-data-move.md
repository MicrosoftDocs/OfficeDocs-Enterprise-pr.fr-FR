---
title: Pendant et après le déplacement de vos données
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Data moves are a back-end operation with minimal impact to end-users. No action is required while Microsoft moves each service and associated data for your tenant to a new datacenter geo. Data transfer and validation occur in the background in advance with minimal impact to users.
ms.openlocfilehash: d07c9c62a778ce23d2e088ddeb8b34346911a19a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774489"
---
# <a name="during-and-after-your-data-move"></a>Pendant et après le déplacement de vos données

Data moves are a back-end operation with minimal impact to end-users. No action is required while Microsoft moves each service and associated data for your tenant to a new datacenter geo. Data transfer and validation occur in the background in advance with minimal impact to users.
  
> [!NOTE]
> Moves occur at different times for each service. As a result, you'll see the described reduced functionality for each service at a different time. 
  
Regardez le centre de messages Microsoft 365 pour confirmer le déplacement de chaque Exchange Online, SharePoint Online, teams et Skype entreprise. Comme indiqué dans le tableau ci-dessous, le déplacement de toutes les données pour tous les clients dans une zone géographique spécifique peut prendre jusqu’à 24 mois à compter de la fin de la période d’inscription. Si vous rencontrez des problèmes avec votre client après le déplacement, contactez le [support technique](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour obtenir de l’aide. 
  

|**Clients avec pays d’abonnement dans**|**Tous les déplacements terminés d'ici le**|
|:-----|:-----|
|Australie, Nouvelle-Zélande, Fidji  <br/> |1er juillet 2022  <br/> |
|Japon  <br/> |1er juillet 2022  <br/> |
|Inde  <br/> |1er juillet 2022  <br/> |
|Canada  <br/> |1er juillet 2022  <br/> |
|Corée du Sud  <br/> |1er juillet 2022  <br/> |
|Royaume-Uni  <br/> |1er juillet 2022  <br/> |
|France  <br/> |1er juillet 2022  <br/> |
|Émirats arabes unis  <br/> |1er juillet 2022  <br/> |
|Afrique du Sud  <br/> |1er juillet 2022  <br/> |
|Suisse, Liechtenstein  <br/> |1er juillet 2022  <br/> |
|Allemagne  <br/> |Vision  <br/> |
|Norvège  <br/> |1er novembre 2022  <br/> |

## <a name="exchange-online"></a>Exchange Online

Comme le déplacement de chaque utilisateur vers la nouvelle zone géographique de centres de données pour un seul client prend du temps, certains utilisateurs seront encore dans l’ancienne zone géographique de centres de données pendant le déplacement, tandis que d’autres seront dans la nouvelle. Cela signifie que certaines fonctionnalités qui impliquent l’accès à plusieurs boîtes aux lettres peuvent ne pas fonctionner entièrement pendant une période du processus de déplacement, qui peut durer des semaines. Ces fonctionnalités sont décrites dans les sections suivantes.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Ouvrez « Dossier partagé » dans Outlook Web Access 

Some users open a shared mail folder from another mailbox (that the user has read or write permissions to) in Outlook Web Access using the "Shared Folder" feature. The following table describes how access to shared folders works during a mailbox move. Please note that users with full permissions to a shared mailbox can open the mailbox by using Outlook Web Access during the move. 
  
|**Configuration**|**Description**|
|:-----|:-----|
|L'utilisateur dispose d'autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l'utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même zone géographique lors du déplacement de client, l'utilisateur A ne peut pas ouvrir le dossier la boîte aux lettres B dans Outlook Web Access s'il n'a de droit d'accès que pour un dossier spécifique de la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d'utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d’accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l’utilisateur a dispose de l’autorisation « accès total » à la boîte aux lettres B, l’utilisateur A peut cliquer sur le dossier partagé dans le volet de navigation gauche dans Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  Un utilisateur peut ouvrir une boîte aux lettres partagée à l’aide d’Outlook Web Access lors du déplacement sans impact négatif. La limitation s’applique uniquement au partage au niveau du dossier dans une boîte aux lettres.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise
    
- Project Online
    
- Project pour Microsoft 365
    
- Services vidéo Microsoft 365
    
- Office dans le navigateur
    
- Applications Microsoft 365 pour les grandes entreprises
    
- Visio Pro pour Microsoft 365
    
Une fois que nous aurons déplacé vos données SharePoint Online, vous pourrez éventuellement observer certains des effets suivants.
  
### <a name="microsoft-365-video-services"></a>Services vidéo Microsoft 365

- Le déplacement de vidéos prend plus de temps que le déplacement d'autres contenus dans SharePoint Online.
    
- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.
    
- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.
    
### <a name="search"></a>Rechercher

In the course of moving your SharePoint Online data, we migrate your search index and search settings to a new location. Until we've **completed** the move of your SharePoint Online data, we continue to serve your users from the index in the original location. In the new location, search automatically starts crawling your content after we've completed moving your SharePoint Online data. From this point and onwards we serve your users from the migrated index. Changes to your content that occurred after the migration aren't included in the migrated index until crawling picks them up. Most customers don't notice that results are less fresh right after we've completed moving their SharePoint Online data, but some customers might experience reduced freshness in the first 24-48 hours 
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n’incluent pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées. 
    
- Delve : Delve n'inclut pas les modifications qui se sont produites après la migration jusqu'à ce que l'analyse les ait récupérées.
    
- Popularity and Search Reports for the site: Counts for Excel reports in the new location only include migrated counts and counts from usage reports that have run after we completed moving your SharePoint Online data. Any counts from the interim period are lost and can't be recovered. This period is typically a couple of days. Some customers might experience shorter or longer losses.
    
- Portail vidéo : les nombres et les statistiques de vue dépendent des statistiques des rapports Excel. Par conséquent, ils sont perdus pendant le même nombre de jours que les rapports Excel.
    
- eDiscovery (découverte électronique) : Les éléments modifiés au cours de la migration ne sont pas affichés avant que l’analyse n’ait récupéré les modifications.
    
- Protection contre la perte de données (DLP) : Les politiques ne sont pas appliquées sur les éléments qui changent avant que l’analyse n’ait récupéré les modifications.

## <a name="microsoft-teams"></a>Microsoft Teams

Outre Exchange Online, SharePoint Online et OneDrive entreprise, Microsoft migre les données de teams vers le centre de données local.

- Les messages de conversation Teams, y compris les messages privés et les messages de canal.
- Images de teams utilisées dans les conversations.

Les fichiers teams sont stockés dans SharePoint Online et les fichiers de conversation teams sont stockés dans OneDrive entreprise. La messagerie vocale, le calendrier, l’historique des conversations et les contacts sont stockés dans Exchange Online. Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive entreprise sont déjà utilisés par le client dans la région du centre de connaissances local et font également partie du programme de migration de Microsoft 365 pour les pays clients éligibles.

## <a name="skype-for-business"></a>Skype Entreprise

Les déplacements Skype entreprise sont disponibles pour l’Australie, le Japon, l’Inde, le Canada, le Royaume-Uni et la Corée du Sud.

All users will be signed out from the Skype for Business client software during cut-over. The automatic sign-in will reconnect users within two minutes.
  
|**Fonctionnalités disponibles pendant l'intégralité du déplacement**|**Fonctionnalités pouvant être limitées pendant une partie du déplacement**|
|:-----|:-----|
| Messagerie instantanée et appels vocaux  <br/>  Les utilisateurs peuvent ajouter des contacts, des groupes de contacts et des réunions, ainsi qu’indiquer leur emplacement et modifier le texte dans « Activités du jour ».  <br/>  Audio Conferencing Provider (ACP) settings are copied to the target datacenter geo. If the ACP provider is present in the target datacenter, it will work. Otherwise, it will not.  <br/> | Les administrateurs ne pourront pas se servir de la fonctionnalité TRPS (PowerShell client à distance) d’administration des clients pour créer des sessions.  <br/>  Les administrateurs ne pourront pas utiliser la fonctionnalité LAC de l'administrateur client pour se connecter et modifier les paramètres utilisateur.  <br/> |
   
|**Après le déplacement**|
|:-----|
| Les données de la réunion (présentations téléchargées, etc.) ne seront pas déplacées et devront être téléchargées à nouveau.  <br/>  Les clients Lync plus anciens, tels que les clients Lync 2010 et Lync pour Mac 2011, mettent en cache des informations DNS dans le service, ce qui entraîne des problèmes de connexion. Le cache DNS devra peut-être être effacé si l’utilisateur ne se trouve pas sur le dernier client Windows de Skype Entreprise. Consultez la rubrique [Troubleshooting Skype for Business Online DNS configuration Problems in Office 365](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue). Les utilisateurs de Lync pour Mac doivent suivre [ces instructions](https://support.microsoft.com/kb/2629861).  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>Déplacements Skype entreprise impliquant un fournisseur de services d’audioconférence tiers
Les services de module complémentaire de fournisseurs de services d’audioconférence tiers pour Skype Entreprise ne sont pas disponibles pour les utilisateurs hébergés dans des centres de données propres à une nouvelle zone géographique.   Les clients existants qui utilisent un service de fournisseur de services d’audioconférence tiers ne doivent pas demander de déplacement vers un centre de données propre à une nouvelle zone géographique.   Les nouveaux clients déployés dans les centres de données propres à une nouvelle zone géographique doivent demander un déplacement vers un centre de données régional afin d’utiliser un fournisseur de services d’audioconférence tiers. 
  
## <a name="related-topics"></a>Voir aussi 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
