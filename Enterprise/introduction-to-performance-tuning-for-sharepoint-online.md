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
description: Cet article décrit les aspects spécifiques que vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487158"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduction à l’optimisation des performances pour SharePoint Online

Cet article décrit les aspects spécifiques que vous devez prendre en compte lors de la conception de pages pour optimiser les performances dans SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Métriques SharePoint Online

Les grandes mesures suivantes de SharePoint Online fournissent des données réelles sur les performances:
  
- La vitesse de chargement des pages
    
- Nombre de boucles requises par page
    
- Problèmes liés au service
    
- Autres facteurs entraînant une dégradation des performances
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusions établies en raison des données

Les données nous indiquent:
  
- La plupart des pages fonctionnent correctement sur SharePoint Online.
    
- Les pages non personnalisées sont chargées très rapidement.
    
- OneDrive entreprise, les sites d'équipe et les pages système, telles que _ layouts, etc., sont tous rapides à charger.
    
- Le chargement des pages SharePoint Online les plus lentes est de plus de 5 000 millisecondes.
    
Il est possible de mesurer les performances en comparant le temps de chargement de votre propre portail et le temps de chargement de la page d'accueil de OneDrive entreprise, car il utilise peu de fonctionnalités personnalisées. Il s'agit souvent de la première étape que vous devez prendre en charge pour résoudre les problèmes de performances réseau.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Utiliser un compte d'utilisateur standard lors de la vérification des performances

Un administrateur de collection de sites, un propriétaire de site, un éditeur ou un collaborateur appartient à des groupes de sécurité supplémentaires, disposent d'autorisations supplémentaires et, par conséquent, ont des éléments supplémentaires chargés par SharePoint sur une page.
  
Ceci s'applique à SharePoint Online et SharePoint Online, mais dans un scénario local, les différences ne seront pas aussi facilement remarquées que dans SharePoint Online.
  
Pour évaluer correctement l'exécution d'une page pour les utilisateurs, vous devez utiliser un compte d'utilisateur standard afin d'éviter de charger les contrôles de création et le trafic supplémentaire lié aux groupes de sécurité.
  
## <a name="connection-categories-for-performance-tuning"></a>Catégories de connexion pour le réglage des performances

Vous pouvez catégoriser les connexions entre le serveur et l'utilisateur en trois composants principaux. Tenez compte de ces éléments lors de la conception de pages SharePoint Online pour un aperçu des temps de chargement.
  
- **Server (serveur** ) Les serveurs que Microsoft héberge dans les centres de contenu.
    
- **Réseau** Le réseau Microsoft, Internet et votre réseau local entre le centre de connaissances et vos utilisateurs.
    
- **Explorateur** Emplacement de chargement de la page.
    
Au sein de ces trois connexions, il existe généralement cinq raisons qui causent 95% de pages chargées. Chacune de ces raisons est abordée dans cet article:
  
- Problèmes de navigation
    
- Cumul de contenu
    
- Fichiers volumineux
    
- Nombreuses requêtes adressées au serveur
    
- Traitement des composants WebPart
    
### <a name="server-connection"></a>Connexion au serveur

De nombreux problèmes qui affectent les performances avec SharePoint en local s'appliquent également à SharePoint Online.
  
Comme vous pouvez vous y attendre, vous avez beaucoup plus de contrôle sur la façon dont les serveurs effectuent SharePoint sur site. Avec SharePoint Online, les choses sont un peu différentes. Plus le nombre de tâches que vous effectuez sur un serveur est long, plus le rendu d'une page est long. Avec SharePoint, le plus grand coupable de ce sujet sont des pages complexes avec plusieurs composants WebPart.
  
SharePoint Server en local
  
![Capture d’écran du serveur local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Capture d’écran du serveur en ligne](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Avec SharePoint Online, certaines demandes de page peuvent réellement appeler plusieurs serveurs. Vous pouvez obtenir une matrice des demandes entre les serveurs pour une demande individuelle. Ces interactions sont coûteuses du point de vue du chargement des pages et rendent les choses plus lentes.
  
Voici quelques exemples d'interactions serveur à serveur:
  
- Web vers les serveurs SQL
    
- Web vers les serveurs d'applications
    
Les échecs de cache sont les autres opérations qui ralentissent les interactions du serveur. Contrairement à SharePoint sur site, il existe une très faible probabilité que vous atteigniez le même serveur pour une page que vous avez visitée précédemment; Cela rend la mise en cache d'objets obsolète.
  
### <a name="network-connection"></a>Connexion réseau 

Avec SharePoint sur site qui n'utilise pas de réseau étendu (WAN), vous pouvez utiliser une connexion à haut débit entre le centre de données et les utilisateurs finaux. En règle générale, les choses sont faciles à gérer du point de vue du réseau.
  
Avec SharePoint Online, il existe quelques facteurs supplémentaires à prendre en compte; par exemple:
  
- Le réseau Microsoft
    
- Internet
    
- Le fournisseur de services Internet
    
Quelle que soit la version de SharePoint (et le réseau) que vous utilisez, les éléments qui entraînent généralement la disponibilité du réseau sont les suivants:
  
- Grande charge utile
    
- Nombreux fichiers
    
- Grande distance physique vers le serveur
    
L'une des fonctionnalités que vous pouvez utiliser dans SharePoint Online est le réseau de distribution de contenu (CDN) Microsoft. Un CDN est fondamentalement une collection distribuée de serveurs déployés sur plusieurs centres de contenu. Avec un CDN, le contenu sur les pages peut être hébergé sur un serveur proche du client même si le client est éloigné du serveur SharePoint d'origine. Microsoft utilisera cette version plus prochaine pour stocker les instances locales des pages qui ne peuvent pas être personnalisées, par exemple la page d'accueil de l'administration SharePoint Online. Pour plus d'informations sur CDN, consultez la rubrique [Content Delivery Networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).
  
La vitesse de connexion de votre fournisseur de services Internet (ISP) ne vous indiquera peut-être pas que vous devez prendre en compte. Un outil de test rapide vous indiquera la vitesse de connexion.
  
### <a name="browser-connection"></a>Connexion de navigateur

Il existe quelques facteurs à prendre en compte pour les navigateurs Web du point de vue des performances.
  
La consultation des pages complexes affectera les performances. La plupart des navigateurs ont seulement un petit cache (environ 90MB), tandis que la page Web moyenne est généralement d'environ 1,6 Mo. L'utilisation de cette valeur n'est pas assez longue.
  
La bande passante peut également être un problème. Par exemple, si un utilisateur regarde des vidéos dans une autre session, cela aura une incidence sur les performances de votre page SharePoint. Bien que vous ne puissiez pas empêcher les utilisateurs de diffuser des médias en continu, vous pouvez contrôler le chargement d'une page pour les utilisateurs.
  
Consultez les articles suivants pour connaître les différentes techniques de personnalisation des pages SharePoint Online et d'autres meilleures pratiques pour obtenir des performances optimales.
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Utiliser l'outil de diagnostics de page pour SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation de réseaux de distribution de contenu](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Utilisation du composant WebPart de recherche de contenu au lieu du composant WebPart requête de contenu pour améliorer les performances dans SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planification de la capacité et test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnostic des problèmes de performances avec SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Utilisation du cache d’objets avec SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Procédure : éviter les limitations ou les blocages dans SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

