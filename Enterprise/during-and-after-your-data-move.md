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
description: Les déplacements de données sont des opérations principales n'ayant que peu d'impact sur les utilisateurs finals. Aucune action de votre part n'est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l'avance, et n'ont qu'une incidence minimale sur les utilisateurs.
ms.openlocfilehash: ee2a63ed11e83a16ec6c894a3eaf34cf36ebbc4f
ms.sourcegitcommit: cf92870078d971ae8e36b75bd35f4b8f36ec7a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "43772105"
---
# <a name="during-and-after-your-data-move"></a>Pendant et après le déplacement de vos données

Les déplacements de données sont des opérations principales n'ayant que peu d'impact sur les utilisateurs finals. Aucune action de votre part n'est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l'avance, et n'ont qu'une incidence minimale sur les utilisateurs.
  
> [!NOTE]
> Le déplacement se produit à différents moments pour chaque service. Par conséquent, vous ne verrez pas la description des fonctionnalités réduites pour chaque service au même moment. 
  
Regardez le centre de messages Microsoft 365 pour confirmer le déplacement de chaque Exchange Online, SharePoint Online, teams et Skype entreprise. Comme indiqué dans le tableau ci-dessous, le déplacement de toutes les données pour tous les clients dans une zone géographique spécifique peut prendre jusqu'à 24 mois à compter de la fin de la période d'inscription. Si vous rencontrez des problèmes avec votre client après le déplacement, contactez le [support Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour obtenir de l'aide. 
  

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

Certains utilisateurs ouvrent un dossier de messagerie partagé à partir d'une autre boîte aux lettres (sur laquelle l'utilisateur a des autorisations en lecture ou en écriture) dans Outlook Web Access à l'aide de la fonctionnalité « Dossier partagé ». Le tableau suivant indique comment fonctionne l'accès aux dossiers partagés au cours d'un déplacement de boîte aux lettres. Notez que les utilisateurs disposant d'autorisations complètes sur une boîte aux lettres partagée peuvent ouvrir la boîte aux lettres à l'aide d'Outlook Web Access lors du déplacement. 
  
|**Configuration**|**Description**|
|:-----|:-----|
|L'utilisateur dispose d'autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l'utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même zone géographique lors du déplacement de client, l'utilisateur A ne peut pas ouvrir le dossier la boîte aux lettres B dans Outlook Web Access s'il n'a de droit d'accès que pour un dossier spécifique de la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d'utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d’accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l’utilisateur a dispose de l’autorisation « accès total » à la boîte aux lettres B, l’utilisateur A peut cliquer sur le dossier partagé dans le volet de navigation gauche dans Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  Un utilisateur peut ouvrir une boîte aux lettres partagée à l’aide d’Outlook Web Access lors du déplacement sans impact négatif. La limitation s’applique uniquement au partage au niveau du dossier dans une boîte aux lettres.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise
    
- Project Online
    
- Project pour Office 365
    
- Services vidéo Office 365
    
- Office dans le navigateur
    
- Office 365 ProPlus
    
- Visio Pro pour Office 365
    
Une fois que nous aurons déplacé vos données SharePoint Online, vous pourrez éventuellement observer certains des effets suivants.
  
### <a name="office-365-video-services"></a>Services vidéo Office 365

- Le déplacement de vidéos prend plus de temps que le déplacement d’autres contenus dans SharePoint Online.
    
- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.
    
- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.
    
### <a name="search"></a>Recherche

Dans le cadre du déplacement de vos données SharePoint Online, nous migrons vos paramètres de recherche et d'index vers un nouvel emplacement. Jusqu'à la **fin** du déplacement de vos données SharePoint Online, nous continuons de desservir vos utilisateurs depuis l'index situé dans l'emplacement d'origine. Dans le nouvel emplacement, la fonction recherche démarre automatiquement une analyse de votre contenu une fois le déplacement de vos données SharePoint Online terminé. À ce moment-là, nous desservirons vos utilisateurs depuis l'index migré. Les modifications apportées à votre contenu après la migration ne sont pas prises en compte dans l'index migré tant que l'analyse ne les a pas récupérées. La plupart des clients ne remarquent pas que les résultats proposent des contenus moins récents immédiatement après la migration de leurs données SharePoint Online, mais certains peuvent s'en apercevoir au cours des 24-48 premières heures d'utilisation. 
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n’incluent pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées. 
    
- Delve : Delve n'inclut pas les modifications qui se sont produites après la migration jusqu'à ce que l'analyse les ait récupérées.
    
- Rapports de popularité et de recherche pour le site : le nombre de rapports Excel situés dans le nouvel emplacement prend uniquement en compte le nombre de rapports migrés et de rapports d'utilisation exécutés après le déplacement de vos données SharePoint Online. Le nombre de rapports existant pendant la période de transition est perdu et ne peut pas être récupéré. Cette période correspond généralement à quelques jours. Certains clients peuvent constater des pertes plus courtes ou plus longues.
    
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

Tous les utilisateurs seront déconnectés du logiciel client Skype Entreprise pendant le basculement. La connexion automatique permettra aux utilisateurs de se reconnecter dans les deux minutes qui suivent.
  
|**Fonctionnalités disponibles pendant l'intégralité du déplacement**|**Fonctionnalités pouvant être limitées pendant une partie du déplacement**|
|:-----|:-----|
| Messagerie instantanée et appels vocaux  <br/>  Les utilisateurs peuvent ajouter des contacts, des groupes de contacts et des réunions, ainsi qu’indiquer leur emplacement et modifier le texte dans « Activités du jour ».  <br/>  Les paramètres du fournisseur de services d’audioconférence sont copiés vers la zone géographique de centres de données cible. Si le fournisseur de services d’audioconférence est présent dans le centre de données cible, la fonctionnalité sera disponible. Sinon, vous ne pourrez pas l’utiliser.  <br/> | Les administrateurs ne pourront pas se servir de la fonctionnalité TRPS (PowerShell client à distance) d’administration des clients pour créer des sessions.  <br/>  Les administrateurs ne pourront pas utiliser la fonctionnalité LAC de l'administrateur client pour se connecter et modifier les paramètres utilisateur.  <br/> |
   
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
