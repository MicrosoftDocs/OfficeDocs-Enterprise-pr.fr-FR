---
title: Forum aux questions sur la mise en réseau vidéo d'Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Le référentiel vidéo Office 365 et les services de diffusion en continu rendent les vidéos de stockage et de diffusion en continu au sein de votre organisation simples. Il existe un grand nombre d'informations intéressantes sur la vidéo Office 365; Ce FAQ sur la mise en réseau est conçu pour répondre aux questions les plus fréquentes sur la planification de bande passante, le chiffrement et la façon dont le service exploite les réseaux de distribution de contenu (CDN).
ms.openlocfilehash: f11bd8baff7c2527287f6e1249ad4dae1928bdd2
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30641521"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Forum aux questions sur la mise en réseau vidéo d'Office 365

Le référentiel vidéo Office 365 et les services de diffusion en continu rendent les vidéos de stockage et de diffusion en continu au sein de votre organisation simples. Il existe un grand nombre d' [informations intéressantes sur la vidéo Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); Ce FAQ sur la mise en réseau est conçu pour répondre aux questions les plus fréquentes sur la planification de bande passante, le chiffrement et la façon dont le service exploite les [réseaux de distribution de contenu](content-delivery-networks.md) (CDN).
  
Si vous n'avez pas déjà une connaissance approfondie de ce qui se passe lors du chargement ou de la lecture d'une vidéo, observez la vidéo que nous avons mise en place, [qu'arrive-t-il à un fichier vidéo lorsqu'il est téléchargé vers Office 365 vidéo](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Quelles sont les exigences de bande passante vidéo d'Office 365?

Il existe un grand nombre de [formats vidéo pris en charge](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) pouvant être téléchargés vers Office 365. Chaque fichier vidéo est ensuite encodé dans un format standard avec plusieurs qualités vidéo pour la lecture. La vidéo Office 365 utilise la diffusion de débit adaptative pour sélectionner la meilleure qualité de lecture vidéo en fonction de la bande passante réseau disponible et de la taille du lecteur vidéo. Pour ce faire, le lecteur demande initialement la qualité de la lecture la plus faible. Le service commence alors à envoyer des segments vidéo de 2 secondes vers le lecteur vidéo. Le joueur peut ensuite demander une qualité de lecture supérieure ou inférieure en fonction de la vitesse de remise de chaque segment.
  
La transmission en continu adaptative fait tout cela en arrière-plan pendant que la vidéo est lue avec le minimum de perturbation ou de mise en mémoire tampon. Lors de la lecture vidéo, le lecteur vidéo permet à la visionneuse de remplacer manuellement la qualité de la lecture automatique afin de sélectionner une qualité de lecture vidéo spécifique.
  
Voici un tableau rapide qui décrit la configuration réseau requise pour chaque qualité vidéo. La bande passante minimale par personne nécessaire pour lire une vidéo est de 802Kbps.
  
|||
|:-----|:-----|
|**Qualité de la lecture** <br/> |**Vitesse du réseau** <br/> |
|288p  <br/> |802Kbps  <br/> |
|360p  <br/> |1,2 Mbits/s  <br/> |
|576p  <br/> |2,5 Mbits/s  <br/> |
|720p  <br/> |3,8 Mbits/s  <br/> |

([Retour au début](office-365-video-networking-faq.md))
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>Comment les réseaux de distribution de contenu (CDN) aident-ils la lecture vidéo?

Si plusieurs personnes de la même organisation au sein du même emplacement géographique utilisent la même vidéo, CDN stocke une copie de ces vidéos dans un emplacement plus proche de cette région géographique. Une fois que la vidéo est stockée ou mise en cache à l'emplacement le plus proche, chaque personne diffuse la vidéo à partir de l'emplacement le plus proche et inversement. La vidéo Office 365 utilise les services multiMédias Azure pour gérer les éléments mis en cache dans Azure CDN, ainsi que la durée. Les services multiMédias Azure peuvent utiliser n'importe quel [emplacement de CDN Azure](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) pour mettre en cache des fragments vidéo et des manifestes pendant quelques jours. Si les personnes de votre organisation continuent de regarder les vidéos mises en cache, elles restent dans le cache. Si personne n'accède à la vidéo pendant plusieurs jours, la vidéo sera finalement supprimée du cache. La prochaine fois qu'une personne tente de regarder la vidéo, elle est de nouveau mise en cache à l'emplacement de CDN le plus proche.
  
Toute personne qui tente de regarder la vidéo pendant que le contenu est mis en cache au niveau d'un CDN à proximité de la vidéo se rapproche, et dans la plupart des cas, moins de sauts. Cela améliore la vitesse de lecture vidéo; Toutefois, il ne change pas la configuration réseau requise pour lire la vidéo.
  
> [!NOTE]
> Dans certaines circonstances, comme la limite de capacité atteint, la vidéo peut être supprimée avant que les trois jours n'aient été atteints.
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>Puis-je mettre en cache les vidéos en local pour accélérer la lecture?

Oui. Office 365 ne vous empêche pas d'utiliser un CDN local ou un proxy de mise en cache pour mettre des vidéos ou d'autres contenus Office 365 sur votre réseau local pour un accès plus rapide. Il existe plusieurs façons d'implémenter une solution de mise en cache locale sur votre réseau, la méthode la plus courante consiste à utiliser une solution proxy qui met en cache le contenu localement. Une fois qu'un proxy ou un CDN privé a mis en cache les fragments et les manifestes de la vidéo, les demandes ultérieures pour ces fichiers qui transitent via le proxy ou le CDN privé sont extraites du cache local et ne sont pas extraites d'un emplacement Internet. Tenez compte de la bande passante réseau, de la capacité et de la simultanéité de lecture vidéo lors de la planification d'une solution comme celle-ci.
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Comment les vidéos sont-elles chiffrées et sécurisées?

Office 365 la vidéo sait combien il est important de sécuriser et de protéger vos données. Le centre de gestion de la confidentialité de [Microsoft](https://products.office.com/business/office-365-trust-center-welcome) décrit notre engagement envers la confidentialité et la sécurité de votre contenu. Avec la lecture vidéo, la vitesse est importante pour une expérience optimale; Toutefois, nous ne compromettons pas votre sécurité ou votre confidentialité dans Exchange à des fins de vitesse. Voici comment nous allons tenir compte de la vitesse, de la sécurité et de la confidentialité.
  
Lorsque vous ou une personne de votre organisation Téléchargez une nouvelle vidéo, celle-ci est transcodée, chiffrée avec le chiffrement AES-128 et stockée dans les services multiMédias Azure. Cela signifie que les vidéos sont chiffrées à la fois en transit et au repos.
  
Lorsqu'une personne de votre organisation tente de regarder une nouvelle vidéo, les étapes suivantes sont suivies:
  
1. Demandez à SharePoint Online s'ils sont autorisés à afficher la vidéo.

2. SharePoint Online utilise les autorisations de fichier pour déterminer si la personne peut regarder la vidéo.

3. Si elles sont autorisées, SharePoint Online récupère un jeton d'Azure pour l'envoyer au lecteur vidéo.

4. Le lecteur vidéo utilise ensuite le jeton pour demander la clé de déchiffrement à partir d'Azure.

5. Une fois la clé de déchiffrement disponible, le lecteur vidéo peut diffuser la vidéo.

![Lecture vidéo O365](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Quelles sont les conditions requises pour lire une vidéo Office 365?

Les systèmes d'exploitation et les navigateurs Web pris en charge par la vidéo Office 365 sont les mêmes que les conditions requises pour SharePoint Online dans [Office 365](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). En fonction de la configuration du système d'exploitation et du navigateur Web dont vous disposez, vous déterminez les besoins spécifiques du lecteur vidéo. Voici plus d'informations sur les [exigences de lecture vidéo](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Je ne parviens pas à utiliser la vidéo Office 365, où dois-je commencer?

Résolution des problèmes de connectivité à Office 365 la vidéo implique le dépannage de votre réseau, de vos fournisseurs de services Internet et de votre configuration d'Office 365. Le premier point de départ est le tableau de bord d'État du service. Cela vous permettra de savoir si la vidéo Office 365 rencontre un problème. Si tout semble parfait, voici quelques ressources supplémentaires pour vous aider.
  
- Assurez-vous que vous pouvez vous connecter aux [points de terminaison réseau requis pour la vidéo Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Vérifiez votre connectivité réseau à l'aide de notre [Guide de dépannage réseau Office 365](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Consultez nos [meilleures pratiques pour l'utilisation d'Office 365 sur un réseau lent](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- [Recherchez de l'aide sur la configuration vidéo d'Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Retour au début](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Ressources vidéo Office 365

Voici quelques autres ressources qui vous aideront à déployer et à utiliser la vidéo Office 365:
  
[Trouver de l'aide sur la configuration vidéo d'Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[Se conFormer à la vidéo Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Créer et gérer un canal dans Office 365 vidéo](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Gérer votre portail vidéo Office 365](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Formats vidéo qui fonctionnent dans Office 365 vidéo](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Retour au début](office-365-video-networking-faq.md))
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
