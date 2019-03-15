---
title: Réseaux de distribution de contenu
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
description: Utilisez ces informations pour en savoir plus sur les réseaux de distribution de contenu (CDN) et sur la façon dont Office 365 les utilise.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636095"
---
# <a name="content-delivery-networks"></a>Réseaux de distribution de contenu

Les informations contenues dans cette rubrique vous aideront à en savoir plus sur les réseaux de distribution de contenu (CDN) et la façon dont ils sont utilisés par Office 365.

CDN permet de conserver rapidement et de façon fiable Office 365 pour les utilisateurs finaux. Les services Cloud comme Office 365 utilisent CDN pour mettre en cache les composants statiques plus près des navigateurs qui les demandent pour accélérer les téléchargements et réduire la latence. Public CDN permet de télécharger plus rapidement du contenu générique tel que des fichiers JavaScript, des icônes et des images, tandis que les CDN privés peuvent fournir un accès rapide et sécurisé aux contenus des utilisateurs, tels que les vidéos et les bibliothèques de documents SharePoint Online.
  
 **Headr à** [Planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune).
  
## <a name="what-exactly-is-a-cdn"></a>Qu'est-ce qu'un CDN exactement?

Les CDN sont utilisés par la plupart des services Cloud d'entreprise. Les services Cloud comme Office 365 ont des millions de clients qui téléchargent un mélange de contenu propriétaire (par exemple, des courriers électroniques) et du contenu générique (par exemple, des icônes) en même temps. Il est plus efficace de placer les images utilisées par tout le monde, comme les icônes, aussi près que possible de l'ordinateur de l'utilisateur. Pourtant, il n'est pas pratique que chaque service Cloud crée des centres de données de CDN qui stockent ce contenu générique dans toutes les zones métropolitaines, ou même dans chaque grand concentrateur Internet du monde entier, de sorte que certaines de ces CDN soient partagées.
  
CDN peut être privé ou public. Les CDN privées sont détenues et gérées par une seule société, et seuls les applications et services de cette société peuvent l'utiliser. Les CDN publiques sont exécutées par des entreprises qui louent une utilisation à plusieurs sociétés. En fonction de l'emplacement où vous vous trouvez, il peut être plus efficace pour Office 365 de télécharger des images génériques à partir d'un CDN qu'Office 365 possède et s'exécute, d'un CDN public ou d'une combinaison des deux. Quel que soit le type de CDN utilisé, les étapes de récupération des données sont les mêmes.
  
1. Votre client demande des données à partir d'Office 365.

2. Office 365 renvoie les données directement à votre client ou dirige votre client vers un CDN.

3. Si les données sont déjà mises en cache au niveau du CDN, votre client télécharge les données directement de l'emplacement de CDN le plus proche vers votre client sur Internet.

4. Si les données ne sont pas mises en cache au niveau du CDN, le nœud CDN demande les données à partir d'Office 365, puis les données du cache pendant un certain temps après que votre client a téléchargé les données.

Le CDN extrait les fichiers et les images du centre de contenu Office 365 le plus proche et, à son tour, votre client extrait les fichiers et les images du CDN le plus proche. Lorsque les utilisateurs accèdent à un service Cloud, comme la lecture du courrier électronique dans Outlook Web App, le navigateur de l'utilisateur tente de récupérer les fichiers et les images à partir du centre de contenu Office 365. Au lieu de passer le temps et la bande passante des fichiers, Office 365 redirige le navigateur vers le CDN. Le CDN indique le centre de données le plus proche dans le navigateur de l'utilisateur et, à l'aide de la redirection, télécharge les images génériques à partir de là. L'utilisation de cette redirection de CDN est rapide et permet aux utilisateurs d'économiser beaucoup de temps de téléchargement.

## <a name="how-do-cdns-make-services-work-faster"></a>Comment les services CDN fonctionnent-ils plus rapidement?

Le téléchargement d'éléments courants, tels que des icônes de plus en plus, peut prendre une bande passante réseau qui peut être mieux utilisée pour le téléchargement de contenu personnel important, comme des courriers électroniques ou des documents. Étant donné qu'Office 365 utilise une architecture qui inclut CDN, les icônes, les scripts et d'autres contenus génériques peuvent être téléchargés à partir de serveurs plus près des ordinateurs clients, ce qui rend les téléchargements plus rapides. Cela signifie un accès plus rapide à votre contenu personnel, qui est stocké de manière sécurisée dans les centres de données Office 365.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Comment dois-je configurer mon réseau de sorte qu'CDN fonctionne de manière optimale avec Office 365?

Si vous planifiez la [connectivité réseau vers Office 365](network-connectivity.md), il est utile de comprendre le fonctionnement général de CDN et le mode de gestion du trafic réseau CDN.

Lorsque vous activez un CDN pour votre client 365 Office, vous commencez par définir des stratégies qui régissent les sources de contenu (les **origines** dans le contexte d'CDN), les classifications de données ou les types de fichiers que vous souhaitez distribuer via le CDN. Les utilisateurs qui accèdent au contenu spécifié sont redirigés vers l'emplacement le plus proche du fichier dans le CDN. Par conséquent, vous devez utiliser les meilleures pratiques décrites dans [Managing Office 365 Endpoints](managing-office-365-endpoints.md) pour vous assurer que votre configuration réseau permet aux navigateurs clients d'accéder au CDN directement plutôt que de router le trafic CDN via des proxys centraux afin d'éviter présentation de la latence inutile.

## <a name="is-my-data-safe"></a>Mes données sont-elles sûres?

Nous sommes très vigilants pour garantir la protection des données qui exécutent votre entreprise. Les données propres au client stockées dans CDN sont chiffrées à la fois en transit et au repos.

> [!NOTE]
> Les fournisseurs de CDN peuvent avoir des normes de confidentialité et de conformité qui diffèrent des engagements décrits par le centre de gestion de la confidentialité Office 365. Les données mises en cache via le service CDN peuvent ne pas être conformes aux conditions de traitement des données Microsoft (DPT) et se trouver en dehors des limites de conformité du centre de gestion de la confidentialité Office 365.

Pour obtenir des informations détaillées sur la confidentialité et la protection des données pour les fournisseurs de CDN Office 365, consultez les rubriques suivantes:  

+ En savoir plus sur la protection des données et la confidentialité Office 365 à partir du centre de gestion de la [confidentialité Microsoft](https://www.microsoft.com/trustcenter)
+ En savoir plus sur la protection des données et la confidentialité Azure dans le centre de gestion de la [confidentialité Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ En savoir plus sur la protection des données et de confidentialité d'Akamai sur le centre de gestion de la [confidentialité des Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Comment puis-je sécuriser mon réseau avec tous ces services tiers?

L'utilisation d'un ensemble complet de services partenaires permet à Office 365 de mettre à l'échelle et de répondre aux exigences de disponibilité, ainsi que d'améliorer l'expérience utilisateur lors de l'utilisation d'Office 365. Les services tiers Office 365 tirent parti des listes de révocation de certificats; tel que crl.microsoft.com ou sa.symcb.com, et CDN; tel que R3.res.Outlook.com. Chaque nom de domaine complet CDN Office 365 utilise un nom de domaine complet personnalisé pour Office 365. Si vous êtes envoyé à un nom de domaine complet (FQDN) à la demande d'Office 365, vous pouvez être assuré que le fournisseur de CDN contrôle le nom de domaine complet et le contenu sous-jacent à cet emplacement.
  
Pour les clients qui souhaitent toujours séparer les demandes destinées à un centre de connaissances Microsoft ou Office 365 des demandes destinées à un tiers, nous avons écrit des instructions sur la [gestion des points de terminaison d'office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Existe-t-il une liste de tous les CDN utilisés par Office 365?

Le CDN utilisé par Office 365 est toujours susceptible d'être modifié et, dans de nombreux cas, plusieurs partenaires CDN configurés dans l'événement 1 ne sont pas disponibles. Les principaux CDN en cours d'utilisation sont les suivants:

+ [Office 365 (spécifiquement pour le contenu SharePoint Online)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Download](https://www.akamai.com/us/en/cdn.jsp)

Ces solutions de CDN ont une portée mondiale qui renforce la portée du service à un plus grand nombre de coins du monde. Le contenu qui y est stocké comprend des scripts, des fichiers et des images généraux d'Office 365. Par exemple, lorsque vous vous connectez à portal.office.com, les images sont extraites du CDN le plus proche afin d'accélérer le temps de chargement de la page. D'autres exemples incluent Office 365 proPlus stockant les bits d'installation sur un CDN pour accélérer le temps nécessaire au téléchargement de la dernière version d'Office.

Il existe également du contenu propriétaire stocké sur CDN, tel que les fichiers vidéo pour la vidéo Office 365. Une fois que vous avez téléchargé les vidéos, les fichiers sont chiffrés, puis stockés dans leur format chiffré avec Azure Media Services. Lorsque le lecteur vidéo Office 365 extrait la vidéo, il est d'abord mis en cache sur le CDN le plus proche avant d'être téléchargé pour accélérer le temps nécessaire au téléchargement de la vidéo.

Pour plus d'informations sur l'utilisation du CDN Office 365, voir [use the office 365 Content Delivery Network with SharePoint Online](use-office-365-cdn-with-spo.md).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Existe-t-il une liste de tous les noms de domaine complets qui tirent parti de CDN?

La liste des noms de domaine complets et la façon dont ils exploitent les modifications apportées à CDN dans le temps, reportez-vous à la page Publications [et plages d'adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) pour obtenir les derniers noms de domaine complets qui tirent parti de CDN.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Puis-je utiliser mon propre CDN et mettre en cache du contenu sur mon réseau local?

Nous recherchons continuellement de nouvelles façons de répondre aux besoins de nos clients et nous explorons actuellement l'utilisation de solutions proxy de mise en cache et d'autres solutions de CDN sur site.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>J'utilise Azure ExpressRoute pour Office 365, cela modifie-t-il les choses?

[Azure ExpressRoute pour office 365](azure-expressroute.md) fournit une connexion dédiée à l'infrastructure Office 365 qui est distincte de l'Internet public. Cela signifie que les clients devront toujours se connecter sur des connexions non-ExpressRoute pour se connecter à CDN et à d'autres infrastructures Microsoft qui ne sont pas incluses explicitement dans la liste des services pris en charge par ExpressRoute. Pour plus d'informations sur le routage de trafic spécifique tel que les demandes destinées à CDN, consultez la rubrique [gestion du trafic réseau Office 365](routing-with-expressroute.md).
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[URL et plages d’adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trustcenter)