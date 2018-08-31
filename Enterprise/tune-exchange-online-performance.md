---
title: Optimisation des performances Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Cet article contient des conseils d’ordre général et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540691"
---
# <a name="tune-exchange-online-performance"></a>Optimisation des performances Exchange Online

Cet article contient des conseils d’ordre général et des liens vers d’autres ressources qui vous indiquent comment améliorer les performances d’Exchange Online. Cet article fait partie du projet [de planification du réseau et de réglage des performances pour Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Éléments à prendre en compte afin d’améliorer les performances d’Exchange Online

Pour améliorer la vitesse de migration et réduire les contraintes de bande passante de votre organisation pour Exchange Online, considérez les points suivants :
  
- **Réduire la taille des boîtes aux lettres.** Le fait de disposer de boîtes aux lettres de plus petite taille accélère la vitesse de migration. 
    
- **Utiliser les capacités de déplacement de boîte aux lettres avec un déploiement Exchange hybride.** Grâce à un déploiement Exchange hybride, les messages en mode hors connexion (sous forme de fichiers .ost) n’ont pas besoin d’être à nouveau téléchargés lors de la migration vers Exchange Online. Cela réduit sensiblement les besoins en bande passante de téléchargement. 
    
- **Programmer les déplacements de boîtes aux lettres pendant les périodes de faible trafic Internet et de faible utilisation d’Exchange local.** Lorsque vous programmez les déplacements, les demandes de migration sont soumises au proxy de réplication de boîte aux lettres et peuvent ne pas être exécutées immédiatement. 
    
- **Utiliser popouts maigre pour Outlook sur le web.** Popouts maigre fournit plus petits, moins gourmandes en mémoire versions de certains messages électroniques dans Microsoft Edge ou Internet Explorer via le rendu de certains composants sur le serveur. Pour plus d’informations, voir [popouts maigre utilisés afin de réduire la mémoire utilisée lors de la lecture des messages électroniques](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).
    
Pour plus d’informations sur les performances de migration Exchange, voir [meilleures pratiques et performances de migration d’Office 365](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

