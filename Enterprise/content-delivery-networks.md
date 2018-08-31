---
title: Réseaux de distribution de contenu
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Utilisez ces informations pour en savoir plus sur les réseaux de distribution de contenu (CDN) et comment Office 365 les exploite. CDN assurent Office 365 rapide et fiable pour les utilisateurs finaux. Avec CDN, les services en nuage tels qu’Office 365 téléchargement rapidement contenu générique, comme les icônes, au navigateur de vos utilisateurs lorsqu’ils utilisent le service via un client web.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540585"
---
# <a name="content-delivery-networks"></a>Réseaux de distribution de contenu

Utilisez ces informations pour en savoir plus sur les réseaux de distribution de contenu (CDN) et comment Office 365 les exploite. CDN assurent Office 365 rapide et fiable pour les utilisateurs finaux. Avec CDN, les services en nuage tels qu’Office 365 téléchargement rapidement contenu générique, comme les icônes, au navigateur de vos utilisateurs lorsqu’ils utilisent le service via un client web.
  
 **Tête de retour à** [Planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Comment dois-je configurer mon réseau afin que les CDN mieux avec Office 365 ?

Si vous envisagez de [connectivité réseau vers Office 365](network-connectivity.md), il est utile de comprendre comment fonctionne les CDN. Il est également important de comprendre que vous ne pouvez pas filtrer connectivité pour les CDN par adresse IP. Nous fournissons liste best effort d’adresses IP pour les services dans Office 365, tels que Exchange Online. En savoir plus sur nos recommandations pour les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="how-do-cdns-make-services-work-faster"></a>Comment les CDN accélèrent-ils la vitesse de fonctionnement des services ?

Téléchargement des opérations courantes comme icônes indéfiniment peut prendre la bande passante réseau qui peut être mieux utilisé pour le téléchargement de contenu personnel important, telles que le courrier électronique ou des documents. Étant donné que Office 365 utilise une architecture qui inclut CDN, les icônes, les scripts et tout autre contenu générique peut être téléchargé à partir des serveurs rapprocher sur des ordinateurs clients, accélérer les téléchargements. Cela signifie un accès rapide à votre contenu personnel, qui est stocké en toute sécurité dans Office 365 de centres de données.
  
## <a name="what-exactly-is-a-cdn"></a>Qu’est-ce qu’un CDN exactement ?

CDN est utilisés par la plupart des services de cloud computing d’entreprise. Services en nuage tels qu’Office 365 ont des millions de clients télécharger un mélange de contenu de propriétaire (par exemple, les messages électroniques) et générique (par exemple, les icônes) en même temps. Il est plus efficace pour mettre les images, comme les icônes, tout le monde utilise aussi proche de l’ordinateur en tant que possible. Encore, il n’est pas pratique pour chaque service en nuage générer des centres de données CDN qui stockent ce contenu générique dans chaque zone métropolitain, ou même dans chaque concentrateur Internet principal dans le monde, afin que certaines de ces CDN sont partagées.
  
CDN peut être publiques ou privées. CDN privées sont appartenant et exploité par une seule société, et uniquement cette société applications et services peuvent utiliser. CDN public est exécutés par des sociétés qui location d’utilisation pour plusieurs sociétés. Selon où vous vous trouvez, il peut être plus efficace pour Office 365 télécharger des images génériques pour vous depuis un CDN qui appartiennent à Office 365 et s’exécute, un CDN public ou une combinaison des deux. Quel que soit le type du CDN est utilisé, les étapes pour récupérer les données sont les mêmes.
  
1. Votre client demande des données à partir d’Office 365.

2. Office 365 renvoie les données directement à votre client ou indique à votre client à un CDN.

3. Si les données sont déjà mise en cache au niveau du CDN, votre client télécharge les données directement à partir de l’emplacement le plus proche CDN à votre client sur internet.

4. Si les données n’est pas mis en cache au niveau du CDN, le nœud CDN demande les données à partir d’Office 365 et puis cache de données pour une période de temps une fois que votre client télécharge les données.

Les CDN extraire les fichiers et les images à partir du centre de données le plus proche Office 365 et à son tour, votre client extrait les fichiers et les images à partir du CDN le plus proche. Lorsque les utilisateurs accèdent à un service en nuage, tels que la lecture des messages dans Outlook Web App, navigateur de l’utilisateur tente de récupérer les fichiers et les images à partir du centre de données Office 365. Au lieu de passer à l’heure et la bande passante qui consiste à fournir les fichiers, Office 365 redirige le navigateur vers le CDN. Le CDN effectue le centre de données le plus proche pour le navigateur de l’utilisateur et, à l’aide de la redirection, télécharge les images génériques à partir de là. À l’aide de la redirection CDN est rapide et il enregistre les utilisateurs beaucoup de temps de téléchargement.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Existe-t-il une liste de tous les noms de domaines complets qui tirent parti des CDN ?

La liste des noms de domaines complets et comment ils tirer parti des CDN modification au fil du temps, reportez-vous à notre publié [page des points de terminaison Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) pour obtenir de mise à jour sur le plus récent noms de domaines complets qui tirent parti des CDN.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Existe-t-il une liste de tous les CDN qui utilise Office 365 ?

Les CDN utilisés par Office 365 sont toujours susceptible de changer et dans de nombreux cas, il existe plusieurs partenaires CDN configurés dans les événements 1 n’est pas disponible. Les deux CDN les plus courants utilisés sont [Akamai](https://www.akamai.com/us/en/cdn.jsp) et [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Deux de ces solutions CDN ont une portée globale, améliorant ainsi la portée du service vers plusieurs coins du monde. Le contenu qui y est stocké inclut général images, fichiers et scripts Office 365. Par exemple, pour vous connecter à portal.office.com, les images sont extraits à partir du CDN le plus proche pour accélérer les temps de chargement de page. Autres exemples Office 365 ProPlus stockant les fichiers binaires d’installation sur un CDN pour accélérer la quantité de temps que nécessaire pour télécharger la dernière version d’Office. Il existe également certains contenus propriétaires qui est stocké sur CDN tels que les fichiers vidéo pour Office 365 vidéo. Une fois que vous téléchargez des vidéos, les fichiers sont chiffrés et ensuite stockés dans leur format chiffré avec Azure Media Services. Lorsque le lecteur vidéo Office 365 récupère la vidéo est tout d’abord mis en cache du CDN le plus proche avant d’être téléchargés pour accélérer la quantité de temps que nécessaire pour télécharger la vidéo.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 offre un CDN puis-je utiliser mes propres fichiers ?

Oui ! Maintenant votre abonnement à Office 365 comprend un CDN distinct Azure que vous pouvez utiliser pour vos ressources SharePoint Online. Pour plus d’informations sur l’utilisation du CDN 365 Office, voir [utiliser le réseau de distribution de contenu Office 365 avec SharePoint Online](use-office-365-cdn-with-spo.md).
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Puis-je utiliser mes propres CDN et du cache de contenu sur mon réseau local ?

Nous cherchent en permanence de nouvelles méthodes pour prendre en charge les besoins des clients et l’utilisation de la mise en cache des solutions de proxy et d’autres solutions CDN locaux sont en train d’Explorer.
  
## <a name="is-my-data-safe"></a>Mes données sont-elles en sécurité ?

Nous prenons précaution afin de garantir que nous protéger les données qui s’exécute de votre entreprise. Les éléments stockés à nos partenaires de réseaux de distribution de contenu est soit chiffré ; comme avec [Office 365 vidéo](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)ou pas des clients spécifiques ; par exemple les fichiers d’installation Office 365 ProPlus. Accédez au [Centre de gestion de la confidentialité Office 365](https://go.microsoft.com/fwlink/p/?LinkId=397383) pour en savoir plus sur nos efforts détaillés pour protéger vos données et votre confidentialité.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Comment puis-je sécuriser mon réseau avec tous ces services tiers 3e ?

Tirer parti d’un ensemble complet de services partenaires permet à Office 365 à l’échelle et répondre aux besoins de disponibilité ainsi améliorer l’expérience utilisateur lors de l’utilisation d’Office 365. Les services de tiers 3e Qu'office 365 exploite incluent les deux listes de révocation de certificats ; par exemple crl.microsoft.com ou sa.symcb.com et CDN ; par exemple r3.res.outlook.com. Chaque nom de domaine complet de CDN Office 365 utilise est un nom de domaine complet personnalisé pour Office 365, si vous êtes envoyé à un nom de domaine complet à la demande d’Office 365 vous pouvez être assuré que nous contrôler le nom de domaine complet et sous-jacent contenu à cet emplacement.
  
Pour les clients qui vouloir séparer les demandes destinées à un centre de données Microsoft ou Office 365 de demandes qui sont destinés à une partie 3, nous avons écrit des conseils sur les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>J’utilise ExpressRoute Azure pour Office 365, qui modifie les choses ?

[ExpressRoute Azure pour Office 365](azure-expressroute.md) offre une connexion dédiée à l’infrastructure d’Office 365 qui est séparée à partir de l’internet public. Cela signifie que les clients seront toujours doivent se connecter via des connexions non ExpressRoute pour se connecter à CDN et autres infrastructure Microsoft qui n’est pas explicitement inclus dans la liste des services pris en charge par ExpressRoute. Pour plus d’informations sur la façon de router le trafic spécifique telles que les demandes destinées CDN, reportez-vous à [la gestion du trafic réseau Office 365](routing-with-expressroute.md).
  
Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Voir aussi

[Points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
