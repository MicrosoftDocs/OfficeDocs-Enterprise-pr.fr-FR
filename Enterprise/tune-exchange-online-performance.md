---
title: Optimisation des performances Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online.
ms.openlocfilehash: d736568687da5ffe0ebed5a57a6afa6f93173c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070350"
---
# <a name="tune-exchange-online-performance"></a>Optimisation des performances Exchange Online

Cet article contient des conseils généraux et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online, en particulier avant une migration. Cet article fait partie du projet [planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Éléments à prendre en compte pour améliorer les performances d’Exchange Online

Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, prenez en compte les éléments suivants:
  
- **Réduisez la taille des boîtes aux lettres.** La taille de boîte aux lettres réduite améliore la vitesse de migration. 
    
- **Utiliser les fonctionnalités de déplacement de boîtes aux lettres avec un déploiement hybride Exchange.** Avec un déploiement hybride Exchange, le courrier hors connexion (sous la forme de. Fichiers OST) ne nécessite pas de téléchargement à nouveau lors de la migration vers Exchange Online. Cela réduit considérablement vos besoins en matière de bande passante de téléchargement. 
    
- **Planifiez les déplacements de boîtes aux lettres au cours des périodes de trafic Internet faible et de l’utilisation d’Exchange en local.** Lors de la planification des déplacements, les demandes de migration sont envoyées au proxy de réplication de boîte aux lettres et ne peuvent pas être placées immédiatement. 
    
- **Utilisez la la messagerie instantanée épuré pour Outlook sur le Web.** Les la messagerie instantanée épurées fournissent des versions plus petites et moins gourmandes en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer en affichant certains composants sur le serveur. Pour plus d’informations, reportez-vous à la rubrique [use Lean la messagerie instantanée pour réduire la mémoire utilisée lors de la lecture des messages électroniques](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Conseils généraux

- Assurez-vous que la recherche DNS pour outlook.office.com entre dans le centre de donnée Microsoft à un emplacement d’entrée logique de votre emplacement.

- Rechercher la mise en cache des boîtes aux lettres et choisir les options appropriées (re. période de mise en cache, mise en cache des boîtes aux lettres partagées et cetera).

- Conservez vos données Outlook en transitant par des connexions VPN (vers un bureau central) avant qu’elles ne circulent sur Internet.

- Assurez-vous que les données de votre boîte aux lettres respectent les limites du dossier et de l’élément, amounts.
    
Pour plus d’informations sur les performances de migration Exchange, consultez la rubrique relative aux [performances et aux meilleures pratiques pour la migration Office 365](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

