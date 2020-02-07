---
title: Meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
description: Ne serait-ce pas agréable si votre connexion Internet était toujours rapide et jamais inactive ? Ce jour, peut-être. Toutefois, entre-temps, il existe des choses pratiques que vous pouvez effectuer pour contourner un réseau Balky tout en continuant à faire votre travail quotidien.
ms.openlocfilehash: 3e9a3e91c5e1cc775d28742b39ea9c0ed507d2c9
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844955"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent

Ne serait-ce pas agréable si votre connexion Internet était toujours rapide et jamais inactive ? Ce jour, peut-être. Toutefois, entre-temps, il existe des choses pratiques que vous pouvez effectuer pour contourner un réseau Balky tout en continuant à faire votre travail quotidien. Bien qu’Office 365 soit un service basé sur un nuage, il offre également de nombreuses façons de travailler en mode hors connexion et de maintenir la synchronisation de vos modifications. En outre, il est parfois plus efficace de travailler avec du contenu hors connexion, car les applications s’exécutent plus rapidement et l’interface utilisateur est plus réactive. Le point est le suivant : Office 365 vous offre le meilleur des deux mondes. Voici comment en tirer parti. 
  
> [!TIP]
> Vous souhaitez voir à quel point la connexion réseau est lente (ou rapide) ? Essayez l’application de test de vitesse de [OOKLA](https://www.speedtest.net/) ou de test de la [Vitesse du réseau](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 

## <a name="why-is-my-network-so-slow"></a>Pourquoi mon réseau est-il si lent ?

Bien que vous ne soyez pas en mesure de contrôler les performances réseau, il est utile de comprendre ce qui se passe en arrière-plan. Internet est extrêmement complexe, mais il existe quelques concepts qui peuvent vous aider à mieux comprendre la situation. Les meilleures pratiques décrites dans cet article peuvent vous aider à résoudre les problèmes de performances et à réduire la frustration.
  
**Facteurs principaux qui affectent les performances du réseau**

![Facteurs de performances réseau](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Bande passante et latence** Les deux mesures les plus importantes des performances du réseau sont la bande passante et la latence : 
  
- La bande passante est le débit mesuré en bits par seconde. Plus grande est préférable. La bande passante est comparable à un tuyau d’eau. Plus le canal est grand, plus le nombre d’eau que vous pouvez mettre en place est élevé.

- La latence est le temps nécessaire pour obtenir du contenu à partir d’un serveur ou d’un service vers votre appareil et est mesuré en millisecondes. Plus rapide. La latence peut être causée par un certain nombre de facteurs, notamment une faible bande passante, une connexion clairsemée ou une durée de transmission.

 **Problèmes courants** Outre la bande passante et la latence, d’autres problèmes ont un impact sur les performances du réseau et sont souvent imprévisibles. Les performances du réseau peuvent fluctuer en fonction de l’heure de la journée ou de votre emplacement physique. Le réseau peut être encombré lorsque certains événements se produisent et font grimper l’utilisation d’Internet, comme une catastrophe naturelle ou un événement public important. La taille et la complexité de la page en cours de chargement, ainsi que le nombre et la taille des fichiers en cours de transfert ont un impact direct sur les performances. Une connexion WiFi peut se dégrader temporairement : par exemple, vous interrogez une grande réunion de conférence de milliers en demandant tout le monde au Tweet en même temps. 
  
 **Considérations relatives à un réseau satellite** Un réseau satellite est utile lorsqu’un réseau terrestre n’est pas réalisable, comme le pays d’arrière-plan, un navire de croisière ou une zone scientifique distante. Ces réseaux s’appuient sur des satellites positionnés sur une orbite géosynchrone 22 000 milles au-dessus de l’Équateur. Toutefois, une transmission voyage en fait environ 90 000 kilomètres, et par conséquent, un réseau satellite a une latence plus lente (500 ms ou plus) qu’un réseau terrestre (20 à MS). Dans les meilleures conditions, vous pouvez ne pas remarquer cette latence, mais pour télécharger des fichiers volumineux, des vidéos de diffusion en continu et des jeux, vous en aurez probablement besoin. Un autre problème est le « fondu de pluie » dans lequel une météo importante, telle que Thunderstorms et blizzards, peut interrompre temporairement la transmission par satellite.
  
## <a name="are-you-sure-its-the-network"></a>Êtes-vous sûr qu’il s’agit du réseau ?

Chaque fois que vous rencontrez des problèmes de performances, vérifiez d’abord que votre appareil n’est pas à l’origine du problème. Vous pouvez effectuer une amélioration importante dans les deux cas suivants :
  
- Assurez-vous que votre appareil fonctionne correctement et qu’il n’y a aucun programme malveillant sur votre ordinateur.

- Si possible, achetez davantage de mémoire. L’ajout de la mémoire est la méthode la plus simple et la plus efficace pour améliorer les performances de votre appareil. Elle est particulièrement utile lorsque vous travaillez avec des fichiers et des vidéos volumineux.

Pour plus d’informations, reportez-vous à [performances et maintenance Windows](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) et [conseils pour améliorer les performances du PC dans Windows 10](https://support.microsoft.com/en-za/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Meilleures pratiques pour l’utilisation de votre navigateur

Votre navigateur est votre passerelle vers Office 365, ce qui peut avoir un impact sur les performances, notamment le temps nécessaire au chargement d’une page et la fréquence d’aller-retour vers le service Office 365.
  
 **Navigateurs en général**
  
Voici quelques suggestions pour les navigateurs en général :
  
- Désactivez les modules complémentaires du navigateur susceptibles d’avoir un impact sur les performances ou dont vous n’avez pas vraiment besoin.

- Augmentez la taille du cache pour vos fichiers Internet temporaires.

- Une fois que vous êtes connecté à votre compte professionnel ou scolaire, laissez la fenêtre du navigateur ouverte tout au long de la journée. Vous pouvez ouvrir d’autres onglets et fenêtres sans vous reconnecter. Si vous avez besoin de vous connecter à un autre compte, utilisez la navigation privée. 

- Une fois que chaque page est téléchargée et ouverte, laissez-la ouverte en utilisant des onglets. Il est facile de naviguer entre les onglets et d’utiliser la page plus tard au cours de la journée. Actualisez une page uniquement si vous avez besoin des données les plus récentes sur cette page.

- Si l’ouverture d’une page prend trop de temps, arrêtez le téléchargement de la page (appuyez sur ÉCHAP), puis actualisez la page (appuyez sur F5). 

-  Dans la mesure du possible, réduisez les allers-retours vers Office 365. Par exemple, plutôt que d’utiliser la pagination dans des listes ou des bibliothèques, utilisez la recherche pour rechercher des fichiers dans une grande bibliothèque et filtrer dans une liste pour obtenir directement les résultats que vous souhaitez. Ou, créez des affichages réduisant le temps de chargement de la page. Pour plus d’informations, consultez la rubrique [gestion des grandes listes et bibliothèques dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Si les performances vidéo sont médiocres, vous pouvez télécharger la vidéo et la regarder sur votre appareil. Un lien de téléchargement peut être disponible, ou vous pouvez cliquer avec le bouton droit sur le lien vidéo, puis sélectionner **enregistrer la cible sous**.

 **Propres au navigateur**
  
Voici quelques suggestions pour votre navigateur :
  
- **Internet Explorer** Effectuez une mise à niveau vers Internet Explorer version 11 ou version ultérieure pour des améliorations de performances substantielles par rapport aux versions précédentes. Pour plus d’informations, reportez-vous au [Guide de résolution des problèmes pour Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).

- **Firefox** Pour plus d’informations, consultez la rubrique [Firefox lente ou cesse de fonctionner](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).

- **Safari** Pour plus d’informations, consultez la rubrique [Apple-Safari](https://www.apple.com/safari/).

- **Chrome** Pour plus d’informations, consultez la rubrique [aide chrome](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Meilleures pratiques pour l’utilisation d’Outlook et d’Outlook Web App

La lecture, l’écriture et l’organisation du courrier électronique sont un élément de la journée. Outlook et Outlook Web App (OWA) offrent une prise en charge hors connexion. L’utilisation d’une application de messagerie sur votre téléphone intelligent constitue une autre alternative utile. Utilisez les options suivantes qui répondent le mieux à vos besoins :
  
- Effectuez une mise à niveau vers la dernière version d’Outlook pour améliorer considérablement les performances par rapport aux versions précédentes. 

-  Outlook Web App vous permet de créer des messages hors connexion, des contacts et des événements de calendrier qui sont téléchargés lorsque OWA est maintenant en mesure de se connecter à Office 365. Pour plus d’informations sur la configuration et l’utilisation d’OWA en mode hors connexion, consultez la rubrique [utilisation d’Outlook Web App en mode hors connexion](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook vous permet de travailler en mode mis en cache, dans lequel il se connecte automatiquement chaque fois que cela est possible. Vous pouvez demander à Outlook de télécharger l’ensemble de votre boîte aux lettres, ou seulement une partie de celle-ci. Pour plus d’informations, consultez la rubrique [activer le mode Exchange mis en cache](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) et [travailler hors connexion dans Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook offre également un mode hors connexion. Pour ce faire, vous devez d’abord configurer le mode mis en cache afin que les informations de votre compte soient copiées sur votre ordinateur. En mode hors connexion, Outlook tente de se connecter à l’aide des paramètres d’envoi et de réception, ou lorsque vous le configurez manuellement pour qu’il fonctionne en ligne. Pour plus d’informations, consultez la rubrique [travailler hors connexion pour éviter les frais de connexion de données](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [modifier les paramètres d’envoi et de réception lorsque vous travaillez en mode hors connexion](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)et [passer du mode hors connexion à en ligne](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Si vous disposez d’un téléphone intelligent, vous pouvez l’utiliser pour trier votre courrier électronique et votre calendrier sur le réseau de votre opérateur téléphonique.

> [!NOTE]
> Voici quelques conseils sur l’utilisation d’Outlook ou d’OWA. Si l’espace disque n’est pas un problème sur votre appareil, Outlook dispose d’un ensemble complet de fonctionnalités et peut s’avérer plus efficace pour vous. Si l’espace disque est un problème sur votre appareil, envisagez d’utiliser OWA qui dispose d’un sous-ensemble de fonctionnalités, mais il fonctionnera également mieux dans une situation en ligne. Bien entendu, vous pouvez utiliser l’un ou l’autre car ils fonctionnent bien ensemble.
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Meilleures pratiques pour l’utilisation de OneDrive entreprise

OneDrive entreprise est entièrement conçu pour fonctionner avec vos fichiers en ligne et hors connexion. Une fois que vous l’avez configurée, la synchronisation des modifications se produit automatiquement et de manière fiable chaque fois que vous les créez. Si le réseau est lent, vous pouvez travailler avec la version hors connexion des fichiers.
  
L’application de synchronisation OneDrive entreprise est fournie avec un abonnement SharePoint Online et Office 365 Business, ou vous pouvez [Télécharger](https://support.microsoft.com/kb/2903984) gratuitement l’application de synchronisation onedrive entreprise. Cette application est également plus rapide que l’utilisation des commandes **ouvrir dans l’Explorateur** ou **Télécharger** . Pour plus d’informations, consultez [la rubrique Configurer votre ordinateur pour synchroniser vos fichiers OneDrive entreprise dans Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Voici quelques conseils supplémentaires pour l’utilisation de l’application de synchronisation OneDrive entreprise :
  
- Si vous synchronisez une grande bibliothèque pour la première fois, lancez la synchronisation pendant les heures creuses, par exemple, pendant la nuit.

- Vous pouvez utiliser la fonctionnalité [arrêter la synchronisation d’une bibliothèque avec l’application OneDrive entreprise](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) pour arrêter temporairement la synchronisation des mises à jour. Toutefois, utilisez cette fonctionnalité pendant de courtes périodes, par exemple quelques heures à la fois, pour éviter de mettre en file d’attente un grand nombre de mises à jour et réduire le risque de conflits de fusion si plusieurs personnes travaillent sur le même document.
  
## <a name="best-practices-for-using-onenote"></a>Meilleures pratiques pour l’utilisation de OneNote

Chaque site d’équipe SharePoint dispose d’un bloc-notes OneNote intégré et vous pouvez facilement créer vos propres sites. OneNote est un excellent moyen de recueillir des informations opportunes dont vous avez besoin quotidiennement pour effectuer des tâches. Par exemple, de nombreuses équipes utilisent OneNote comme point de collecte pour des réunions hebdomadaires, des notes de projet, des idées, des plans et des rapports d’État. Vous pouvez organiser ces informations disparates à l’aide de pages, de sections et d’onglets.
  
La beauté de OneNote est que vous pouvez accéder au contenu à partir de pratiquement n’importe quel appareil, qu’il s’agisse d’un ordinateur de bureau, d’un ordinateur portable, d’une tablette ou d’un téléphone intelligent. Et vous n’avez pas à vous soucier de l’enregistrement ou de la synchronisation, car OneNote le fait pour vous.
  
Pour plus d’informations, consultez la rubrique [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Meilleures pratiques pour l’utilisation de Skype entreprise et de Lync Online

Les instructions suivantes sont des instructions générales sur l’utilisation de Skype entreprise ou de Lync Online lorsque votre réseau est lent :

- Utilisez la messagerie instantanée dès que vous pouvez faire en sorte qu’elle fonctionne correctement sur un réseau lent.

- Évitez d’appeler des appels téléphoniques via un réseau privé virtuel (VPN) ou un service d’accès à distance (RAS).

- Assurez-vous que votre périphérique audio est approuvé. Pour plus d’informations, reportez-vous à la rubrique [téléphones et appareils qualifiés pour Microsoft Lync](https://docs.microsoft.com/skypeforbusiness/lync-cert/ip-phones).

- Lorsque vous utilisez PowerPoint dans une présentation en ligne, réduisez la taille et la complexité des diapositives. Pour plus d’informations, reportez-vous [à conseils pour améliorer les performances de votre présentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Les performances vidéo sont très tributaires des performances du réseau. Évitez d’utiliser la vidéo si votre réseau est lent.

Pour plus d’informations, reportez-vous à la rubrique [qualité audio ou vidéo insuffisante dans Lync Online](https://support.microsoft.com/kb/2386655)ou [résolution des problèmes de connexion dans Skype entreprise](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Meilleures pratiques pour l’utilisation des listes SharePoint

Utiliser des données de liste hors connexion pour « nettoyer », analyser ou rapporter des données est un excellent moyen de réduire l’impact d’un réseau lent. Vous pouvez lire et écrire la plupart des listes à partir de Microsoft Access 2019 et Microsoft Access 2016 en les liant. Vous pouvez également exporter une liste vers un tableau Excel, ce qui crée une connexion de données unidirectionnelle entre le tableau Excel et la liste. Découvrez comment [travailler hors connexion avec des tables liées à des listes SharePoint](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).
  
Pour plus d’informations, reportez-vous à la section « en savoir plus sur la gestion des grandes listes » dans [gestion des grandes listes et bibliothèques dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Meilleures pratiques pour la personnalisation des pages Web

Lorsque vous personnalisez une page Web, vous risquez de nuire involontairement aux performances de la page. Un certain nombre de facteurs peuvent avoir un impact, comme la complexité et la taille de la page, le nombre de composants WebPart ajoutés, le nombre d’éléments de liste ou de bibliothèque initialement affichés, ainsi que le mode de codage de la page.
  
Pour plus d’informations, consultez la rubrique [optimiser les performances de SharePoint Online](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).
  
## <a name="best-practices-for-using-project-online"></a>Meilleures pratiques pour l’utilisation de Project Online

Les instructions suivantes peuvent vous aider à améliorer les performances du réseau.
  
- Project Online et SharePoint Online nécessitent une synchronisation, ce qui peut prendre beaucoup de temps. Si les équipes de votre projet ont un bon chiffre d’affaires, désactivez la synchronisation des sites Project pour améliorer les performances des pages de détails de projet et de publication. Limitez la synchronisation Active Directory aux groupes de ressources qui ont réellement besoin d’utiliser le système et surveillez les problèmes d’autorisation potentiels après la synchronisation des grands groupes.

- Si votre organisation utilise des sites de projet, créez-les à la demande plutôt qu’automatiquement. Cela accélère la première expérience de publication et évite la création de sites et de contenu inutiles.

- Les pages de détails de projet (PDP) peuvent déclencher un recalcul de l’ensemble du projet et lancer des actions de flux de travail, qui peuvent être toutes deux des opérations gourmandes en performances. Pour éviter de déclencher simultanément deux processus de mise à jour sur le même PDP, évitez de mettre à jour les champs de calendrier (date de début, date de fin, date d’État et date actuelle) et les champs non planifiés (nom de projet, description et propriétaire).

- Réduisez le nombre de composants WebPart et de champs personnalisés affichés sur chaque PDP. Créez une PDP dédiée avec les seuls champs qui nécessitent une mise à jour pour améliorer la charge et gagner du temps.

- Lorsque vous utilisez OData pour la création de rapports, limitez la quantité de données que vous interrogez lors de l’exécution à l’aide du filtrage côté serveur.

Pour plus d’informations, consultez la rubrique [régler les performances de Project Online](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>Quelle est la meilleure façon de signaler les problèmes ?

Microsoft améliore en permanence les performances globales d’Office 365 en surveillant le réseau, en mesurant la bande passante et la latence, en améliorant le temps de chargement des pages, en réduisant les e/s disque, en reconcevant les pages pour utiliser une stratégie de téléchargement minimale, en ajoutant du matériel aux centres de données et en ajoutant des centres de données. Pour plus d’informations sur la vérification de vos problèmes d’État et de création de rapports, consultez [la rubrique How to check Office 365 service Health](https://docs.microsoft.com/office365/enterprise/view-service-health).
  
## <a name="see-also"></a>Voir aussi

[Planification réseau et optimisation des performances pour Office 365](network-planning-and-performance.md)
  
[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
 