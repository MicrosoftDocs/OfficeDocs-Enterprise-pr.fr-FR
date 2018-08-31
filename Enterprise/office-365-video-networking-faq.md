---
title: 'Vidéo Office 365 : Forum aux Questions de mise en réseau'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
description: Le référentiel Office 365 vidéo et transmettre en continu des services facilitent le stockage et des vidéos au sein de votre organisation. Il existe un grand nombre des informations importantes sur Office 365 vidéo ; cette Foire aux questions sur les réseaux est conçu pour répondre aux questions les plus fréquentes autour de la bande passante de la planification, le chiffrement et comment le service exploite les réseaux de distribution de contenu (CDN).
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540395"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Vidéo Office 365 : Forum aux Questions de mise en réseau

Le référentiel Office 365 vidéo et transmettre en continu des services facilitent le stockage et des vidéos au sein de votre organisation. Il y a beaucoup d' [informations sur Office 365 vidéo](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); cette Foire aux questions sur les réseaux est conçu pour répondre aux questions les plus fréquentes autour de la bande passante de la planification, le chiffrement et comment le service exploite les [réseaux de distribution de contenu (CDN)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).
  
Si vous ne déjà posséder une connaissance approfondie de ce qui se produit lorsqu’une vidéo est téléchargée ou de lecture, regardez cette vidéo nous mettre en place, [ce qui se passe dans un fichier vidéo lorsque téléchargé vers Office 365 vidéo](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Quelles sont les exigences de bande passante Office 365 vidéo ?

Il existe un grand nombre [des formats vidéo pris en charge](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) qui peut être téléchargé vers Office 365. Chaque fichier vidéo est puis codée dans un format standard avec plusieurs éléments vidéo différents pour la lecture. Vidéo Office 365 utilise adaptive vitesse de transmission en continu pour sélectionner la meilleure qualité de lecture de la vidéo en fonction de la bande passante réseau disponible et la taille du lecteur vidéo. Pour ce faire, le lecteur demande initialement la qualité de lecture la plus faible. Ensuite, le service commence l’envoi des segments vidéo 2 secondes pour le lecteur vidéo. Le lecteur peut alors demander la qualité de lecture supérieur ou inférieur en fonction de la vitesse à laquelle chaque segment est remis.
  
La diffusion en continu de la vitesse de transmission adaptive toutes les effectue cette action en arrière-plan pendant la lecture de la vidéo avec le moins de perturbations ou la mise en mémoire tampon. Lors de la lecture vidéo, le lecteur vidéo permet de modifier manuellement la qualité de la lecture automatique pour sélectionner une qualité de lecture vidéo spécifique de la visionneuse.
  
Voici une table rapide qui décrit la configuration réseau requise pour chacune des caractéristiques de la lecture vidéo. La bande passante minimale par personne nécessaire pour lire une vidéo est 802 Kbits/s.
  
|||
|:-----|:-----|
|**Qualité de lecture** <br/> |**Vitesse du réseau** <br/> |
|288p  <br/> |802 Kbits/s  <br/> |
|360p  <br/> |1.2 Mbits/s  <br/> |
|576p  <br/> |2.5 Mbits/s  <br/> |
|720 pixels  <br/> |3.8 Mbits/s  <br/> |

([Retour au début](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Comment CDN à lecture vidéo ?

Si plusieurs personnes de la même organisation dans le même emplacement géographique sont en continu l’ou plusieurs vidéos même, CDN stockera une copie de ces vidéos d’un emplacement de plus près à cette région géographique. Avec vidéo stockés ou mis en cache à l’emplacement le plus proche, chaque personne transmet la vidéo à partir de l’emplacement le plus proche de leur au lieu d’un emplacement plus absent (e). Vidéo Office 365 utilise Azure Media Services pour gérer ce qui est mis en cache dans les CDN Azure et la durée. Azure Media Services permet un des [emplacements Azure CDN](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) cache fragments vidéo et les manifestes pour quelques jours. Si les personnes dans votre organisation continuent à visionner les vidéos de mise en cache qu’ils restent dans le cache. Si aucun accès un finira par la vidéo pendant plusieurs jours, la vidéo dépôt supprimées du cache. La prochaine fois que quelqu'un tente de regarder la vidéo qu’il est à nouveau mis en cache à l’emplacement CDN le plus proche.
  
Toute personne qui tente de regarder la vidéo pendant que le contenu est mis en cache à un avantages CDN à proximité de la vidéo en cours de plus près et dans la plupart des cas moins tronçons, absent (e). Cela améliore la vitesse de lecture vidéo ; Toutefois, il ne change pas la réseau requise pour lire la vidéo.
  
> [!NOTE]
> Il existe certains cas, tels que notre capacité maximale est atteinte, dans lesquelles la vidéo peut être supprimée avant de trois jours a été atteinte.
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>Puis-je mettre en cache les vidéos localement pour une lecture plus rapide ?

Oui. Office 365 ne vous empêche d’à l’aide d’un CDN local ou un proxy de mise en cache pour intégrer vidéo ou tout autre contenu Office 365 à votre réseau local pour un accès rapide. Il existe plusieurs façons d’implémenter une solution de mise en cache locale sur votre réseau, la méthode la plus courante consiste à utiliser une solution de proxy qui met en cache le contenu local. Une fois qu’un serveur proxy ou un CDN privée a mis en cache les fragments vidéo et les manifestes, futures demandes pour les fichiers qui routent via le serveur proxy ou CDN privée sont extraites du cache local et pas extraites depuis un emplacement internet. Prendre en compte la bande passante réseau, la capacité et la lecture vidéo concurrence lors de la planification d’une solution similaire à celle-ci.
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Comment les vidéos sont chiffrées et sécurisées ?

Office 365 vidéo sait combien il est important pour conserver vos données sécurisées et privées. [Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-cloud-computing-security) décrit notre engagement à la confidentialité et la sécurité de votre contenu. Avec la lecture vidéo, la vitesse est importante pour une bonne expérience ; Toutefois, nous ne compromettre votre sécurité ou la confidentialité en échange de vitesse. Voici comment nous prendre en charge la vitesse, la sécurité et confidentialité.
  
Lorsque vous ou une personne de votre organisation télécharge une nouvelle vidéo, que la vidéo est transcodage, chiffré avec le chiffrement AES-128 et stockées dans les Services de support Azure. Cela signifie que les vidéos sont chiffrées à la fois en transit et inactives.
  
Lorsqu’une personne de votre organisation tente de regarder une vidéo, ils procédez comme suit :
  
1. Demandez à SharePoint Online s’ils disposent des autorisations pour afficher la vidéo.

2. SharePoint Online utilise les autorisations de fichier pour déterminer si la personne peut regarder la vidéo.

3. S’ils sont autorisés, SharePoint Online récupère un jeton d’Azure pour le lecteur vidéo.

4. Le lecteur vidéo utilise ensuite le jeton pour demander la clé de déchiffrement à Azure.

5. Avec la clé de déchiffrement dans main, le lecteur vidéo peut lire la vidéo.

![O365 Lecture vidéo](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Quelles sont les exigences pour la lecture Office 365 vidéo ?

Vidéo Office 365 pris en charge les systèmes d’exploitation et navigateurs web sont les mêmes que les exigences de SharePoint Online dans [Office 365 requise](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Selon le système d’exploitation et web configuration du navigateur que vous avez déterminera les besoins spécifiques du lecteur vidéo. Voici le plus d’informations sur les [exigences de lecture de la vidéo](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Retour au début](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Impossible d’obtenir Office 365 vidéo fonctionne, où dois-je commencer ?

Résolution des problèmes de connectivité à Office 365 vidéo implique la résolution des problèmes de votre réseau et votre ISP(s) votre configuration d’Office 365. Le premier point de départ est le tableau de bord de l’intégrité de service. Ceci indique d’Office 365 vidéo rencontre un problème ou non. Si tout semble intéressante, voici quelques ressources supplémentaires pour vous aider.
  
- Assurez-vous que vous pouvez vous connecter à des [points de terminaison de réseau requises pour Office 365 vidéo](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

- Vérifiez la connectivité réseau à l’aide de notre [réseau Office 365 guide de dépannage](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Consultez les [meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- Trouvez [l’aide sur la configuration d’Office 365 vidéo](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Retour au début](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Ressources vidéo pour Office 365

Évaluer la rubrique et laisser un commentaire pour nous indiquer si nous avons répondu à vos questions ou si vous n’êtes toujours pour obtenir des réponses. Voici quelques-unes des autres ressources pour vous aider à déployer et utiliser Office 365 vidéo avec succès :
  
[Trouver de l’aide sur la configuration d’Office 365 vidéo](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Conférence vidéo Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Créer et gérer un canal dans Office 365 vidéo](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Gérer votre portail Office 365 vidéo](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Formats vidéo fonctionnant dans Office 365 vidéo](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Retour au début](office-365-video-networking-faq.md))
  
Voici un lien court, que vous pouvez utiliser pour revenir :[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
