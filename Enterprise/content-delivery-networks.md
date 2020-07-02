---
title: Réseaux de distribution de contenu
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/22/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Utilisez ces informations pour découvrir comment Office 365 utilise les réseaux de distribution de contenu (CDN) pour améliorer les performances.
ms.openlocfilehash: 21dc32da619a8f5f7521d07213156f2ab86fc876
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997470"
---
# <a name="content-delivery-networks-cdns"></a>Réseaux de distribution de contenu (CDN)

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

CDN permet de conserver rapidement et de façon fiable Office 365 pour les utilisateurs finaux. Les services Cloud tels qu’Office 365 utilisent CDN pour mettre en cache les composants statiques plus près des navigateurs qui les demandent pour accélérer les téléchargements et réduire la latence des utilisateurs finaux. Les informations contenues dans cette rubrique vous aideront à en savoir plus sur les réseaux de distribution de contenu (CDN) et la façon dont ils sont utilisés par Office 365.

## <a name="what-exactly-is-a-cdn"></a>Qu’est-ce qu’un CDN exactement ?

Un CDN est un réseau distribué géographiquement composé de serveurs proxy et de serveurs de fichiers dans des centres de distribution connectés par des réseaux dorsaux à haut débit. Les CDN sont utilisées pour réduire la latence et les temps de chargement pour un ensemble spécifié de fichiers et d’objets dans un site Web ou un service. Un CDN peut avoir plusieurs milliers de points de terminaison pour assurer une maintenance optimale des demandes entrantes à partir de n’importe quel emplacement.

Les CDN sont couramment utilisés pour fournir des téléchargements plus rapides de contenu générique pour un site Web ou un service tel que des fichiers JavaScript, des icônes et des images, et peuvent également fournir un accès privé au contenu utilisateur, tel que des fichiers dans les bibliothèques de documents SharePoint Online, des fichiers multimédias de diffusion en continu et du code personnalisé.

Les CDN sont utilisés par la plupart des services Cloud d’entreprise. Les services Cloud comme Office 365 ont des millions de clients qui téléchargent un mélange de contenu propriétaire (par exemple, des courriers électroniques) et du contenu générique (par exemple, des icônes) en même temps. Il est plus efficace de placer les images utilisées par tout le monde, comme les icônes, aussi près que possible de l’ordinateur de l’utilisateur. Il n’est pas pratique que chaque service Cloud crée des centres de données de CDN qui stockent ce contenu générique dans toutes les zones métropolitaines, ou même dans chaque grand concentrateur Internet du monde entier, de sorte que certaines de ces CDN soient partagées.

## <a name="how-do-cdns-make-services-work-faster"></a>Comment les services CDN fonctionnent-ils plus rapidement ?

Le téléchargement d’objets communs, tels que des images et des icônes de site, peut prendre la bande passante réseau qui peut être mieux utilisée pour le téléchargement de contenu personnel important, comme le courrier électronique ou les documents. Étant donné qu’Office 365 utilise une architecture qui inclut CDN, les icônes, les scripts et d’autres contenus génériques peuvent être téléchargés à partir de serveurs plus près des ordinateurs clients, ce qui rend les téléchargements plus rapides. Cela signifie un accès plus rapide à votre contenu personnel, qui est stocké de manière sécurisée dans les centres de données Office 365.

CDN aide à améliorer les performances du service Cloud de plusieurs façons :

- CDN la charge de travail du réseau et du téléchargement de fichiers à distance du service Cloud, ce qui permet de libérer des ressources de service Cloud afin de servir le contenu de l’utilisateur et d’autres services en réduisant le besoin de traiter les demandes d’éléments statiques.
- Les CDN sont conçus pour fournir un accès aux fichiers à faible latence en mettant en œuvre des réseaux de fichiers et des réseaux à hautes performances, et en exploitant des protocoles réseau mis à jour tels que [http/2](https://en.wikipedia.org/wiki/HTTP/2) avec une compression et un multiplexage de requêtes hautement efficaces.
- Les réseaux CDN utilisent un grand nombre de points de terminaison répartis globalement pour mettre le contenu à la disposition des utilisateurs le plus près possible.

## <a name="the-office-365-cdn"></a>Le CDN Office 365

Le réseau de distribution de contenu (CDN) Office 365 intégré permet aux administrateurs d’Office 365 de fournir de meilleures performances pour les pages SharePoint Online de leur organisation en mettant en cache les composants statiques plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. Le CDN Office 365 utilise le [protocole http/2](https://en.wikipedia.org/wiki/HTTP/2) pour améliorer la compression et les vitesses de téléchargement.

> [!NOTE]
> Le CDN Office 365 est uniquement disponible pour les clients dans le Cloud de **production** (dans le monde entier). Les clients des nuages des États-Unis, de Chine et d’Allemagne ne prennent actuellement pas en charge le CDN Office 365.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger sur le réseau de distribution de contenu Office 365, vous pouvez ajouter des origines **publiques**, **privées** ou les deux.

![Diagramme conceptuel de CDN Office 365](media/O365-CDN/o365-cdn-flow-transparent.svg "Diagramme conceptuel de CDN Office 365")

Le contenu des origines **publiques** du réseau de distribution de contenu Office 365 est anonymement accessible à toute personne qui dispose des URL d’accès aux ressources hébergées. Comme l’accès au contenu des origines publiques est anonyme, vous ne devez l’utiliser que pour mettre en cache du contenu générique non sensible, comme des scripts, des icônes, des images et des fichiers javascript. Le réseau de distribution de contenu Office 365 est utilisé par défaut pour télécharger des ressources génériques, telles que les applications clientes Office 365, à partir d’une origine publique.

Les origines **privées** dans le CDN Office 365 fournissent un accès privé au contenu utilisateur comme les bibliothèques de documents, les sites et les images propriétaires SharePoint Online. L’accès au contenu des origines privées est sécurisé à l’aide de jetons générés dynamiquement, de sorte qu’il n’est accessible qu’aux utilisateurs autorisés à accéder à la bibliothèque de documents ou à l’emplacement de stockage d’origine. Les origines privées du réseau de distribution de contenu Office 365 ne peuvent être utilisées que pour du contenu SharePoint Online, et vous ne pouvez accéder aux ressources que par redirection à partir de votre client SharePoint Online.

Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour plus d’informations sur l’utilisation du CDN Office 365, voir [use the office 365 Content Delivery Network with SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo).

Pour regarder une série de courtes vidéos qui fournissent des informations conceptuelles et des informations sur l’utilisation du CDN Office 365, visitez la [chaîne YouTube SharePoint Developer Patterns and Practices](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Autres CDN Microsoft

Bien qu’il ne fasse pas partie du CDN Office 365, vous pouvez utiliser ces CDN dans votre client Office 365 pour accéder aux bibliothèques de développement SharePoint, à du code personnalisé et à d’autres fins qui ne rentrent pas dans le cadre du CDN d’Office 365.

### <a name="azure-cdn"></a>CDN Azure

Vous pouvez utiliser le **CDN Azure** pour déployer votre propre instance CDN pour héberger des composants WebPart personnalisés, des bibliothèques et d’autres ressources de ressource, ce qui vous permet d’appliquer des touches d’accès à votre stockage CDN et de mieux contrôler votre configuration de CDN. L’utilisation du CDN Azure n’est pas gratuite et nécessite un abonnement Azure.

Pour plus d’informations sur la configuration d’une instance CDN Azure, consultez la rubrique [QuickStart : intégrer un compte de stockage Azure avec Azure CDN](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn).

Pour obtenir un exemple de la façon dont le CDN Azure peut être utilisé pour héberger les composants WebPart SharePoint, voir [déployer votre composant WebPart côté client SharePoint sur Azure CDN](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Pour plus d’informations sur le module Azure CDN Azure, voir [Manage Azure CDN with PowerShell](https://docs.microsoft.com/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>CDN Microsoft Ajax

Le **CDN Ajax** de Microsoft est un CDN en lecture seule qui offre de nombreuses bibliothèques de développement courantes, notamment jQuery (et toutes ses autres bibliothèques), ASP.NET AJAX, Bootstrap, Knockout.js et d’autres encore.
  
Pour inclure ces scripts dans votre projet, il suffit de remplacer les références à ces bibliothèques disponibles publiquement par des références à l’adresse CDN au lieu de les inclure dans votre projet lui-même. Par exemple, utilisez le code suivant pour créer un lien vers jQuery :

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Pour plus d’informations sur l’utilisation du CDN Microsoft Ajax, consultez la rubrique [Microsoft Ajax CDN](https://docs.microsoft.com/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Comment Office 365 utilise-t-il le contenu d’un CDN ?

Quel que soit le CDN que vous configurez pour votre client 365 Office, le processus de récupération des données de base est le même.

1. Votre client (une application cliente Office ou un navigateur) demande des données à partir d’Office 365.

2. Office 365 renvoie directement les données à votre client ou, si les données font partie d’un ensemble de contenu hébergé par le CDN, redirige votre client vers l’URL du CDN.

    a. Si les données sont déjà mises en cache dans une origine _publique_ , votre client télécharge les données directement de l’emplacement de CDN le plus proche vers votre client.

    b. Si les données sont déjà mises en cache dans une origine _privée_ , le service CDN vérifie les autorisations de votre compte d’utilisateur Office 365 sur l’origine. Si vous disposez d’autorisations, SharePoint Online génère dynamiquement une URL personnalisée composée du chemin d’accès à la ressource dans le CDN et de deux jetons d’accès, et renvoie l’URL personnalisée à votre client. Votre client télécharge ensuite les données directement de l’emplacement de CDN le plus proche vers votre client à l’aide de l’URL personnalisée.

3. Si les données ne sont pas mises en cache au niveau du CDN, le nœud CDN demande les données à partir d’Office 365, puis met les données en cache pendant un certain temps après que votre client a téléchargé les données.

Le CDN indique le centre de données le plus proche dans le navigateur de l’utilisateur et, à l’aide de la redirection, télécharge les données demandées à partir de là. La redirection du CDN est rapide et permet aux utilisateurs d’enregistrer beaucoup de temps de téléchargement.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Comment dois-je configurer mon réseau de sorte qu’CDN fonctionne de manière optimale avec Office 365 ?

La limitation de la latence entre les clients sur votre réseau et les points de terminaison CDN est la principale considération pour garantir des performances optimales. Vous pouvez utiliser les meilleures pratiques décrites dans [Managing Office 365 Endpoints](managing-office-365-endpoints.md) pour vous assurer que votre configuration réseau permet aux navigateurs clients d’accéder directement au CDN plutôt que de router le trafic CDN via des proxys centraux afin d’éviter une latence inutile.

Vous pouvez également lire les [principes de connectivité réseau office 365](https://aka.ms/o365networkingprinciples) pour comprendre les concepts inhérents à l’optimisation des performances réseau d’Office 365.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Existe-t-il une liste de tous les CDN utilisés par Office 365 ?

Le CDN utilisé par Office 365 est toujours susceptible d’être modifié et, dans de nombreux cas, plusieurs partenaires CDN configurés dans l’événement 1 ne sont pas disponibles. Les CDN principaux utilisés par Office 365 sont les suivants :

|CDN  |Company  |Utilisation  |Liens  |
|---------|---------|---------|---------|
|CDN Office 365     |Download         |Ressources génériques dans les origines publiques, contenu utilisateur SharePoint dans les origines privées         |[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)         |
|CDN Azure     |Microsoft         |Code personnalisé, solutions SharePoint Framework         |[CDN Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)         |
|CDN Microsoft Ajax (lecture seule)     |Microsoft         |Bibliothèques communes pour Ajax, jQuery, ASP.NET, bootstrap, Knockout.js etc.         |[CDN Microsoft Ajax](https://docs.microsoft.com/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Quels gains de performances fournissent un CDN ?

Il existe de nombreux facteurs impliqués dans la mesure de différences spécifiques de performances entre les données téléchargées directement à partir d’Office 365 et les données téléchargées à partir d’un CDN spécifique, telles que votre emplacement par rapport à votre client et au point de terminaison CDN le plus proche, le nombre de biens sur une page qui sont pris en charge par le CDN, ainsi que les modifications transitoires de la Toutefois, un simple test A/B peut vous aider à afficher la différence en temps de téléchargement pour un fichier spécifique.

Les captures d’écran suivantes illustrent la différence de vitesse de téléchargement entre l’emplacement de fichiers natif dans Office 365 et le même fichier hébergé sur le [réseau de distribution de contenu Microsoft Ajax](https://docs.microsoft.com/aspnet/ajax/cdn/overview). Ces captures d’écran sont extraites de l’onglet **réseau** dans les outils de développement Internet Explorer 11. Ces captures d’écran montrent la latence sur la bibliothèque jQuery. Pour afficher cet écran, dans Internet Explorer, appuyez sur **F12** et sélectionnez l’onglet **réseau** qui est symbolisé par une icône Wi-Fi.
  
![Capture d’écran du réseau F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Cette capture d’écran montre la bibliothèque téléchargée vers la Galerie de pages maîtres sur le site SharePoint Online proprement dit. Le temps nécessaire au chargement de la bibliothèque est de 1,51 secondes.
  
![Capture d’écran du temps de chargement de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La deuxième capture d’écran montre le même fichier fourni par le CDN de Microsoft. Cette fois, la latence est d’environ 496 millisecondes. Il s’agit d’une amélioration importante qui montre qu’une seconde entière est éclatée du temps total de téléchargement de l’objet.
  
![Capture d’écran du temps de chargement de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Mes données sont-elles sûres ?

Nous sommes très vigilants pour protéger les données qui exécutent votre entreprise. Les données stockées dans le CDN Office 365 sont chiffrées à la fois en transit et sur REST, et l’accès aux données dans le CDN Office 365 SharePoint est sécurisé par les autorisations utilisateur Office 365 et l’autorisation de jeton. Les demandes de données dans le CDN Office 365 SharePoint doivent être renvoyées (redirigées) à partir de votre client Office 365 ou un jeton d’autorisation ne sera pas généré.

Pour vous assurer que vos données restent sécurisées, nous vous recommandons de ne jamais stocker de contenu utilisateur ou d’autres données sensibles dans un CDN public. Étant donné que l’accès aux données dans un CDN public est anonyme, public CDN doit uniquement être utilisé pour héberger du contenu générique tel que des fichiers de script Web, des icônes, des images et d’autres ressources non sensibles.

> [!NOTE]
> les fournisseurs de CDN tiers peuvent avoir des normes de confidentialité et de conformité qui diffèrent des engagements décrits par le centre de gestion de la confidentialité Office 365. Les données mises en cache via le service CDN peuvent ne pas être conformes aux conditions de traitement des données Microsoft (DPT) et se trouver en dehors des limites de conformité du centre de gestion de la confidentialité Office 365.

Pour obtenir des informations détaillées sur la confidentialité et la protection des données pour les fournisseurs de CDN Office 365, consultez les rubriques suivantes :  

- En savoir plus sur la protection des données et la confidentialité Office 365 à partir du centre de gestion de la [confidentialité Microsoft](https://www.microsoft.com/trustcenter)
- En savoir plus sur la protection des données et de confidentialité d’Akamai sur le centre de gestion de la [confidentialité des Akamai](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- En savoir plus sur la protection des données et la confidentialité Azure dans le centre de gestion de la [confidentialité Azure](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Comment puis-je sécuriser mon réseau avec tous ces services tiers ?

L’utilisation d’un ensemble complet de services partenaires permet à Office 365 de mettre à l’échelle et de répondre aux exigences de disponibilité, ainsi que d’améliorer l’expérience utilisateur lors de l’utilisation d’Office 365. Les services tiers Office 365 tirent parti des listes de révocation de certificats ; tel que crl.microsoft.com ou sa.symcb.com, et CDN ; tel que r3.res.outlook.com. Chaque nom de domaine complet de CDN généré par Office 365 est un nom de domaine complet personnalisé pour Office 365. Si vous êtes envoyé à un nom de domaine complet (FQDN) à la demande d’Office 365, vous pouvez être assuré que le fournisseur de CDN contrôle le nom de domaine complet et le contenu sous-jacent à cet emplacement.
  
Pour les clients qui souhaitent différencier les demandes destinées à un centre de connaissances Microsoft ou Office 365 des demandes destinées à un tiers, nous avons écrit des instructions sur la [gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Existe-t-il une liste de tous les noms de domaine complets qui tirent parti de CDN ?

La liste des noms de domaine complets et la façon dont ils exploitent les modifications apportées à CDN. Consultez nos pages [URL et plages d’adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) pour obtenir les derniers noms de domaine complets qui exploitent CDN.

Vous pouvez également utiliser l' [adresse IP et le service Web d’URL office 365](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service) pour demander les URL et plages d’adresses ip Office 365 actuelles au format CSV ou JSON.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Puis-je utiliser mon propre CDN et mettre en cache du contenu sur mon réseau local ?

Nous recherchons continuellement de nouvelles façons de répondre aux besoins de nos clients et nous explorons actuellement l’utilisation de solutions proxy de mise en cache et d’autres solutions de CDN sur site.

Bien qu’il ne fasse pas partie du CDN Office 365, vous pouvez également utiliser le **CDN Azure** pour héberger des composants WebPart personnalisés, des bibliothèques et d’autres ressources de ressources, ce qui vous permet d’appliquer des touches d’accès à votre stockage CDN et de mieux contrôler la configuration de votre CDN. L’utilisation du CDN Azure n’est pas gratuite et nécessite un abonnement Azure. Pour plus d’informations sur la configuration d’une instance CDN Azure, consultez la rubrique [QuickStart : intégrer un compte de stockage Azure avec Azure CDN](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>J’utilise Azure ExpressRoute pour Office 365, cela modifie-t-il les choses ?

[Azure ExpressRoute pour office 365](azure-expressroute.md) fournit une connexion dédiée à l’infrastructure Office 365 qui est distincte de l’Internet public. Cela signifie que les clients devront toujours se connecter sur des connexions non-ExpressRoute pour se connecter à CDN et à d’autres infrastructures Microsoft qui ne sont pas incluses explicitement dans la liste des services pris en charge par ExpressRoute. Pour plus d’informations sur le routage de trafic spécifique tel que les demandes destinées à CDN, consultez la rubrique [gestion du trafic réseau Office 365](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Puis-je utiliser CDN avec SharePoint Server en local ?

L’utilisation de CDN n’a de sens que dans un contexte SharePoint Online et doit être évitée avec SharePoint Server. Cela est dû au fait que tous les avantages liés à l’emplacement géographique ne sont pas vrais si le serveur est situé localement ou géographiquement fermé. En outre, s’il existe une connexion réseau aux serveurs où elle est hébergée, le site peut être utilisé sans connexion Internet et par conséquent ne peut pas récupérer les fichiers CDN. Dans le cas contraire, vous devez utiliser un CDN s’il en existe une disponible et stable pour la bibliothèque et les fichiers dont vous avez besoin pour votre site.
  
Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Voir aussi

[Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples)

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)

[Gestion des points de terminaison Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)

[URL et plages d’adresses IP Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)

[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trustcenter)

[Optimisation des performances Office 365](tune-office-365-performance.md)
