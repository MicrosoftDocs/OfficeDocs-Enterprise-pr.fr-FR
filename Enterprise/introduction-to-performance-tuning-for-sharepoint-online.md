---
title: Introduction à l’optimisation des performances pour SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Cet article explique les aspects spécifiques, vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540333"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduction à l’optimisation des performances pour SharePoint Online

Cet article explique les aspects spécifiques, vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
  
## <a name="in-this-article"></a>Contenu de cet article

- [Mesures de SharePoint Online](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) et [Conclusions atteint en raison de données](introduction-to-performance-tuning-for-sharepoint-online.md#data)
    
- [Utilisez un compte d’utilisateur standard lors de la vérification des performances](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- [Pour régler les performances des catégories de connexion](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [connexion au serveur](introduction-to-performance-tuning-for-sharepoint-online.md#server), de [connexion réseau](introduction-to-performance-tuning-for-sharepoint-online.md#network)et de [connexion du navigateur](introduction-to-performance-tuning-for-sharepoint-online.md#browser)
    
## <a name="sharepoint-online-metrics"></a>Indicateurs de performances SharePoint Online
<a name="spometrics"> </a>

Les indicateurs globaux suivants pour SharePoint Online fournissent des données réelles sur les performances :
  
- La vitesse de chargement des pages
    
- Le nombre de boucles nécessaires par page
    
- Les problèmes avec le service
    
- Autres éléments qui provoquent la dégradation des performances
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusions des données recueillies
<a name="data"> </a>

Les données nous ont permis de tirer les conclusions suivantes :
  
- Les performances de la plupart des pages sont bonnes sur SharePoint Online.
    
- Le chargement des pages non personnalisées est très rapide.
    
- Le chargement de OneDrive Entreprise, des sites d’équipe et des pages système, telles que _layouts, etc., est rapide.
    
- Le chargement des pages SharePoint Online les plus lentes (à hauteur de 1 % de l’ensemble des pages) s’élève à plus de 5 000 millisecondes.
    
Pour effectuer un test simple d’évaluation, vous pouvez mesurer les performances en comparant le temps de chargement de votre propre portail au temps de chargement de la page d’accueil OneDrive Entreprise, car elle utilise peu de fonctionnalités personnalisées. Si vous contactez l’assistance technique pour des problèmes de performances réseau, il vous sera généralement demandé d’exécuter ce test pour commencer.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Utilisez un compte d’utilisateur standard lors de la vérification des performances
<a name="standuser"> </a>

Un administrateur de Collection de sites, propriétaire de Site, l’éditeur ou collaborateur appartiennent à des groupes de sécurité, disposer d’autorisations supplémentaires et donc des éléments supplémentaires SharePoint charges sur une page.
  
Ceci s’applique à SharePoint sur site et SharePoint Online, mais dans un scénario local les différences ne seront pas aussi facilement perceptibles comme dans SharePoint Online.
  
Pour pouvoir évaluer correctement comment une page effectue pour les utilisateurs, vous devez utiliser un compte d’utilisateur standard pour éviter de charger la création de contrôles et le trafic supplémentaire relatives aux groupes de sécurité.
  
## <a name="connection-categories-for-performance-tuning"></a>Catégories de connexion pour l’optimisation des performances
<a name="connect"> </a>

Vous pouvez classer les connexions entre le serveur et l’utilisateur en trois composants principaux. Prenez-les en compte lors de la conception de pages SharePoint Online pour obtenir une vision globale du processus de chargement des pages.
  
- **Server.** Les serveurs que Microsoft héberge dans les centres de données.
    
- **Réseau.** Le réseau Microsoft, Internet et votre réseau local entre le centre de données et de vos utilisateurs.
    
- **Navigateur.** Où la page est chargée.
    
Ces trois connexions présentent généralement cinq raisons susceptibles d’être à l’origine de 95 % de la lenteur de chargement des pages. Chacune de ces raisons est décrite dans cet article :
  
- Problèmes de navigation
    
- Regroupement de contenu
    
- Fichiers volumineux
    
- Grand nombre de demandes au serveur
    
- Traitement des composants WebPart
    
### <a name="server-connection"></a>Connexion au serveur
<a name="server"> </a>

Un grand nombre des problèmes qui ont un impact négatif sur les performances de SharePoint local s’appliquent également à SharePoint Online.
  
Comme on pouvait s’y attendre, avec SharePoint local, vous contrôlez davantage les performances des serveurs. Avec SharePoint Online, ce n’est pas exactement la même chose. Plus vous demandez de travail à un serveur, plus le temps d’affichage d’une page sera long. Avec SharePoint, les pages complexes contenant plusieurs composants WebPart constituent la plus grande cause de ralentissement.
  
SharePoint Online
  
![Capture d’écran du serveur en ligne](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint
  
![Capture d’écran du serveur local](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Avec SharePoint Online, certaines demandes de page peuvent réellement finir par appeler plusieurs serveurs. Vous pourriez vous retrouver avec une matrice de demandes entre serveurs pour une simple demande unique. Ces interactions pèsent sur le chargement des pages et ralentissent ce processus.
  
Voici quelques exemples de ces interactions de serveur à serveur :
  
- Serveur web vers serveur SQL
    
- Serveur web vers serveur d’applications
    
Les interactions avec le serveur peuvent également être ralenties par les échecs liés au cache. Contrairement à SharePoint local, il est très peu probable que ce soit le même serveur qui vous fournisse une page que vous avez consultée précédemment. La mise en cache de l’objet est donc obsolète.
  
### <a name="network-connection"></a>Connexion réseau
<a name="network"> </a>

SharePoint local qui n’utilisent un réseau étendu, vous pouvez utiliser une connexion rapide entre des centres de données et les utilisateurs finaux. En règle générale, les éléments sont faciles à gérer à partir d’un point de vue du réseau.
  
Avec SharePoint Online, il existe d’autres facteurs à prendre en compte, par exemple :
  
- Le réseau Microsoft
    
- Internet
    
- Le fournisseur de services Internet
    
Quelle que soit la version de SharePoint (et le réseau) que vous utilisez, voici les principaux facteurs d’indisponibilité du réseau :
  
- Charge utile de grande taille
    
- Grand nombre de fichiers
    
- Grande distance physique pour atteindre le serveur
    
Une fonctionnalité que vous pouvez tirer parti de SharePoint Online est CDN (Content Delivery Network) Microsoft. Un CDN est simplement un ensemble distribué de serveurs déployés dans plusieurs centres de données. Avec un CDN, contenu sur les pages peut être hébergé sur un serveur a presque atteint le client, même si le client est éloignée du serveur d’origine SharePoint. Microsoft utilisera cette plus à l’avenir pour stocker les instances locales des pages qui ne peuvent pas être personnalisées, par exemple la page d’accueil d’administration SharePoint Online. Pour plus d’informations sur CDN, voir [réseaux de distribution de contenu](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).
  
Il existe un autre élément que vous devez connaître, même si vous ne pourrez sûrement rien y faire ; il s’agit de la vitesse de connexion de votre fournisseur de services Internet. Un simple outil de test de vitesse vous indiquera la vitesse de connexion.
  
### <a name="browser-connection"></a>Connexion du navigateur
<a name="browser"> </a>

Il existe quelques facteurs de performances à prendre en compte concernant les navigateurs web.
  
Visitez les pages complexes affecte les performances. La plupart des navigateurs ne disposez que d’un cache de petite taille (environ 90 Mo), lors de la moyenne page web est généralement environ 1,6 Mo. Cela n’est pas en long pour obtenir utilisé.
  
Bande passante peut également être un problème. Par exemple, si un utilisateur est regarder des vidéos dans une autre session, cela affecte les performances de votre page SharePoint. Lorsque vous ne pouvez pas empêcher les utilisateurs de diffusion multimédia par flux, vous pouvez contrôler la façon dont une page se charge pour les utilisateurs.
  
Consultez les articles suivants pour différentes techniques de personnalisation de la page SharePoint Online et d’autres meilleures pratiques pour vous aider à optimiser les performances.
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Utilisez l’outil de diagnostic de la Page pour SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation de réseaux de distribution de contenu](using-content-delivery-networks-with-sharepoint-online.md)
    
- [À l’aide du composant WebPart de recherche au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [La capacité de planification et de test SharePoint Online de charge](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnostic des problèmes de performances avec SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Utilisation du cache d’objets avec SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Procédure : éviter les limitations ou les blocages dans SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

