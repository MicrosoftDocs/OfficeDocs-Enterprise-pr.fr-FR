---
title: Utilisation du cache d’objets avec SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056163"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Utilisation du cache d’objets avec SharePoint Online

Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.
  
Le fait de compter sur le cache d’objets a un impact négatif conséquent sur le déploiement SharePoint Online. réduira la fiabilité de votre page. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Comment le SharePoint Online et SharePoint Server 2013 objet cache fonctionne

Lorsque SharePoint Server 2013 est hébergée sur site, le client a des serveurs web frontaux privée qui hébergent le cache d’objets. Cela signifie que le cache est dédié à un seul client et est limité uniquement par la quantité de mémoire est disponible et allouée au cache d’objets. Car un seul client est pris en charge dans le scénario locale les serveurs web frontaux ont généralement les utilisateurs effectuent des demandes pour les sites même indéfiniment. Cela signifie que le cache complète rapidement et reste complète des résultats de requête de liste et des objets SharePoint que vos utilisateurs demandent régulièrement.
  
![Affiche le trafic et la charge vers les serveurs web frontaux locaux](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Par conséquent, lorsqu’un utilisateur consulte une page pour la deuxième fois, le temps de chargement de la page diminue. Après au moins quatre chargements de la même page, la page est mise en cache sur tous les serveurs web frontaux.
  
En revanche, dans SharePoint Online sont nombreux serveurs mais également davantage de sites. Chaque utilisateur peut se connecter à un autre serveur web frontal qui ne dispose pas le cache rempli. Ou, par exemple le cache sont rempli pour un serveur, mais l’utilisateur à ce serveur web frontal suivant demande une page à partir d’un autre site. Ou, même si l’utilisateur suivant demande la même page que sur leur visite précédente, ils sont à charge équilibrée pour un autre serveur web frontal qui ne possède pas de cette page dans son cache. Dans ce dernier cas, la mise en cache n’aide les utilisateurs à tout.
  
Dans la figure suivante, chaque point représente une page qu’un utilisateur demande et l’emplacement où elle est mise en cache. Les différentes couleurs représentent plusieurs clients qui se partagent l’infrastructure SaaS.
  
![Affiche les résultats de la mise en cache d’objets dans SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Comme vous pouvez le constater dans le diagramme, les risques d’un utilisateur donné en appuyant sur un serveur avec la version en cache de leur page sont très faible. En outre, en raison de la grande débit et fait que les serveurs sont partagées entre plusieurs sites, le cache ne dure depuis longtemps bien espace uniquement pour la mise en cache est disponible.
  
Ces différents points démontrent que pour assurer une expérience utilisateur de qualité et un temps de chargement des pages efficace dans SharePoint Online, il n’est pas pertinent de compter sur la mise en cache des objets des utilisateurs.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Alors, si nous ne pouvons pas compter sur le cache d’objets pour améliorer les performances dans SharePoint Online, que devons-nous utiliser ?

Puisque nous ne recommandons pas de compter sur la mise en cache dans SharePoint Online, vous devez évaluer les autres approches de conception pour les personnalisations SharePoint qui utilisent le cache d’objets. Pour résoudre les problèmes de performances et obtenir des résultats satisfaisants pour les utilisateurs, vous devez donc utiliser des approches qui ne reposent pas sur la mise en cache d’objets. Ces approches font l’objet d’autres articles de cette série, dont notamment :
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation de réseaux de distribution de contenu](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

