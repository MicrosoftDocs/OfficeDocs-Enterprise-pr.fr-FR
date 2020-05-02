---
title: Utilisation du cache d’objets avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.
ms.openlocfilehash: e489a5f5c9438a773b7aa790ccb25d9c558729d3
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004187"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Utilisation du cache d’objets avec SharePoint Online

Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 sur site et SharePoint Online.
  
Il y a un impact négatif significatif sur le recours au cache d’objets dans le déploiement de SharePoint Online. Toute dépendance vis-à-vis du cache d’objets dans SharePoint Online réduira la fiabilité de votre page. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Fonctionnement du cache d’objets SharePoint Online et SharePoint Server 2013

Lorsque SharePoint Server 2013 est hébergé en local, le client dispose de serveurs Web frontaux privés qui hébergent le cache d’objets. Cela signifie que le cache est dédié à un client et qu’il est limité par la capacité de mémoire disponible et allouée au cache d’objets. Étant donné qu’un seul client est pris en charge dans le scénario local, les serveurs Web frontaux ont généralement des demandes de requêtes sur les mêmes sites. Cela signifie que le cache est saturé rapidement et qu’il reste complet des résultats de la requête de liste et des objets SharePoint demandés régulièrement par vos utilisateurs.
  
![Affiche le trafic et la charge vers les serveurs web frontaux locaux](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Par conséquent, la deuxième fois qu’un utilisateur visite une page, le temps de chargement de la page est amélioré. Après un minimum de quatre chargements de la même page, la page est mise en cache sur tous les serveurs Web frontaux.
  
En revanche, dans SharePoint Online, il existe beaucoup plus de serveurs, mais également de nombreux autres sites. Chaque utilisateur peut se connecter à un autre serveur Web frontal qui n’a pas de cache rempli. Ou peut-être que le cache est rempli pour un serveur, mais que le prochain utilisateur de ce serveur Web frontal demande une page d’un autre site. Ou bien, même si l’utilisateur suivant demande la même page que lors de sa visite précédente, il bénéficie d’un équilibrage de charge sur un autre serveur Web frontal qui n’a pas cette page dans son cache. Dans ce dernier cas, la mise en cache n’aide pas les utilisateurs.
  
Dans la figure suivante, chaque point représente une page demandée par un utilisateur et là où il est mis en cache. Différentes couleurs représentent différents clients qui utilisent l’infrastructure SaaS partagée.
  
![Affiche les résultats de la mise en cache d’objets dans SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Comme vous pouvez le voir dans le diagramme, les risques qu’un utilisateur donné accède à un serveur avec la version mise en cache de la page sont réduits. En outre, en raison du grand débit et du fait que les serveurs sont partagés entre de nombreux sites, le cache n’a pas été utilisé depuis longtemps car il n’y a qu’un espace suffisant pour la mise en cache.
  
Pour toutes ces raisons, il n’est pas possible de s’appuyer sur la récupération des objets mis en cache pour garantir une expérience utilisateur de qualité et des temps de chargement des pages dans SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Si nous ne pouvons pas compter sur le cache d’objets pour améliorer les performances dans SharePoint Online, que pouvons-nous utiliser à la place ?

Étant donné que vous ne devez pas vous appuyer sur la mise en cache dans SharePoint Online, vous devez évaluer d’autres approches de conception pour les personnalisations SharePoint qui utilisent le cache d’objets. Cela signifie que l’utilisation d’approches pour les problèmes de performances ne repose pas sur la mise en cache d’objets pour produire de bonnes résultats pour les utilisateurs. Ceci est décrit dans certains autres Articles de cette série et inclut les éléments suivants :
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation de réseaux de distribution de contenu](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

