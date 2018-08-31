---
title: Meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
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
description: Serait-il si votre connexion Internet est toujours rapide et jamais bas ? Ce jour seront sans doute. Mais en attendant, il existe des pratique choses que vous pouvez faire pour résoudre un réseau balky et toujours obtenir votre travail quotidien.
ms.openlocfilehash: 52c3bde04aa58f9e24a49d2034e6b6433c44f21c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540581"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent

Serait-il si votre connexion Internet est toujours rapide et jamais bas ? Ce jour seront sans doute. Mais en attendant, il existe des pratique choses que vous pouvez faire pour résoudre un réseau balky et toujours obtenir votre travail quotidien. Bien qu’Office 365 est un service en nuage, il fournit également plusieurs façons pour travailler avec votre contenu hors connexion et facilement conserver vos modifications synchronisées. En outre, il est parfois plus efficace pour travailler avec le contenu hors connexion, car les applications s’exécutent plus rapidement et de l’interface utilisateur est plus vite. Le fait est le : Office 365 vous donne le meilleur des deux domaines. Voici comment tirer parti de cette. 
  
> [!TIP]
> Vous voulez voir comment lente (ou fast) est votre connexion réseau ? Essayez la [vitesse OOKLA de test](https://www.speedtest.net/) ou l' [Application de Test de vitesse de réseau](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 
     
## <a name="why-is-my-network-so-slow"></a>Pourquoi est mon réseau si lent ?

Bien que vous ne disposez pas contrôler les performances réseau lui-même, il est utile de comprendre ce qui se passe les coulisses. Internet est très complexe, mais il existe quelques concepts qui peuvent vous aider à comprendre la situation préférable. Suivant les meilleures pratiques de cet article, vous pouvez aider à contourner des problèmes de performances et réduire la frustration.
  
**Facteurs qui affectent les performances réseau**

![Facteurs de performances réseau](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Bande passante et latence** Les deux mesures plus importantes des performances du réseau sont la bande passante et latence : 
  
- Bande passante est le taux de débit, exprimé en bits par seconde. Plus grand est préférable. Bande passante est similaire à une conduite d’eau. Plus le canal, l’eau plus de » par le biais de « il.
    
- Latence est le temps nécessaire pour le contenu à obtenir à partir d’un serveur ou un service sur votre périphérique et est exprimée en millisecondes. Plus rapide est préférable. Latence peut être dû à un nombre de facteurs, notamment de faible bande passante, une connexion incomplet ou l’heure de transmission.
    
 **Problèmes courants** En plus de bande passante et latence, autres problèmes ont un impact sur les performances du réseau et sont souvent imprévisibles. Performances du réseau peuvent varier en fonction de l’heure du jour ou votre emplacement physique. Le réseau peut devenir obstruée lorsque certains événements se produisent qui pic l’utilisation d’Internet, comme un événement public principal ou catastrophe naturelle. La taille et la complexité de la page en cours de chargement et le nombre et la taille des fichiers en cours de transfert ont une incidence directe sur les performances. Une connexion Wi-Fi peut se dégrader provisoirement : par exemple, vous interrogez une réunion Conférence importante de milliers en demandant à tout le monde tweet en même temps. 
  
 **Pour un réseau satellites** Un réseau satellite est utile lorsqu’un réseau terrestre n’est pas possible, telles que le pays arrière, un destinataire de croisière ou une zone scientifique à distance. Ces réseaux s’appuient sur satellites placés dans une orbite geosynchronous 22 000 miles au-dessus de l’Équateur. Toutefois, une transmission transite réellement environ 90 000 miles et un réseau satellite aura une latence inférieure (500 ms ou plus) à un réseau terrestre (20 à aller-retour de 50 millisecondes). Dans les meilleures conditions, vous pouvez ne pas remarquerez cette latence, mais pour le téléchargement de fichiers volumineux, vidéos et jeux, vous allez probablement. Un autre problème est « pluie fondu » dans les gros temps, telles que thunderstorms et blizzards, peut interrompre temporairement la transmission satellite.
  
## <a name="are-you-sure-its-the-network"></a>Vous êtes qu’il s’agit du réseau ?

Chaque fois que vous rencontrez des problèmes de performances, assurez-vous que votre appareil n’est pas la cause du problème. Il existe deux possibilités qui peuvent être une amélioration notable :
  
- Assurez-vous que votre appareil exécute également et il n’existe aucun programme malveillant sur votre ordinateur.
    
- Si possible, acheter davantage de mémoire. Ajout de mémoire est la plus simple et le plus souvent un moyen efficace pour améliorer les performances sur votre appareil. Il est particulièrement utile lorsque vous travaillez avec des vidéos et des fichiers volumineux.
    
Pour plus d’informations, voir [les performances de Windows et la maintenance](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) et [Windows de résoudre des problèmes de performances système](https://support.microsoft.com/mats/slow_windows_performance/).
   
## <a name="best-practices-for-using-your-browser"></a>Meilleures pratiques pour l’utilisation de votre navigateur

Votre navigateur n’est votre passerelle vers Office 365, afin qu’il peut avoir un impact sur les performances, en particulier avec le temps que nécessaire pour charger une page et la fréquence à laquelle vous arrondissez déclenchement du Office 365 service. 
  
 **En général, les navigateurs**
  
Voici quelques suggestions pour les navigateurs en général :
  
- Désactiver les modules complémentaires du navigateur qui pourraient affecter les performances ou que vous ne devez pas vraiment.
    
- La taille du cache pour vos fichiers internet temporaires.
    
-  Après que vous être connecté à votre compte professionnel ou de l’école, laissez la fenêtre du navigateur ouvert pendant toute la journée. Vous pouvez ouvrir les autres onglets et windows sans vous connecter à nouveau. Si vous devez vous connecter à un autre compte, utilisez la navigation privée. 
    
- Une fois que chaque page est téléchargé et open, conservez les ouvert à l’aide des onglets. Il est facile de naviguer entre les onglets et utilisez la page plus tard dans la journée. Actualisation d’une page que si vous avez besoin des données les plus récentes sur cette page.
    
- Si une page prend trop de temps pour ouvrir, arrêter le téléchargement de la page (appuyez sur ÉCHAP), puis actualisez la page (appuyez sur F5). 
    
-  Dans la mesure du possible, réduire allers-retours vers Office 365. Par exemple, au lieu de la pagination par le biais de listes ou bibliothèques, utilisez recherche pour localiser les fichiers dans une bibliothèque de grande taille et le filtrage dans une liste pour accéder directement aux résultats que vous souhaitez. Ou bien, créer des affichages qui réduisent le temps de chargement de page. Pour plus d’informations, voir [Gérer les grandes listes et bibliothèques dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).
    
- Si les performances vidéo sont médiocre, vous pourrez télécharger la vidéo et de démonstration sur votre appareil. Un lien de téléchargement est peut-être disponible, ou vous pourrez, cliquez avec le bouton droit sur le lien vidéo et sélectionnez **Enregistrer la cible sous**. 
    
 **Navigateur spécifiques**
  
Voici quelques suggestions pour votre navigateur spécifique :
  
- **Internet Explorer** Mise à niveau vers Internet Explorer Version 11 ou version ultérieure pour les améliorations des performances par rapport aux versions précédentes. Pour plus d’informations, consultez [problèmes de réparer Internet Explorer ](https://support.microsoft.com/mats/ie_performance_and_safety).
    
- **FireFox** Pour plus d’informations, voir [Firefox est lent ou cesse de fonctionner](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging).
    
- **Safari** Pour plus d’informations, voir [Apple - Safari](https://www.apple.com/safari/).
    
- **Chrome** Pour plus d’informations, consultez [l’Aide de Chrome](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Meilleures pratiques pour l’utilisation d’Outlook et Outlook Web App

Lecture, écriture et l’organisation de messagerie est une grande partie de la journée de tout le monde. Outlook et Outlook Web App (OWA) offrent une prise en charge en mode hors connexion. À l’aide d’une application de messagerie sur votre téléphone intelligent est également utile. Utilisez les options suivantes qui correspondent le mieux à vos besoins :
  
- Mise à niveau vers Outlook 2013 SP1 ou version ultérieure pour les améliorations des performances par rapport aux versions précédentes. 
    
-  Outlook Web App vous permet de créer des messages en mode hors connexion, les contacts et les événements du calendrier qui sont téléchargés lorsque OWA est la suivante en mesure de se connecter à Office 365. Pour plus d’informations sur la configuration et à l’aide de OWA en mode hors connexion, voir [L’aide de Outlook Web App en mode hors connexion](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).
    
- Outlook vous permet de travailler en mode mis en cache, dans lequel il se connecte automatiquement chaque fois que possible. Vous pouvez configurer Outlook télécharger votre boîte aux lettres entière ou seulement une partie de celui-ci. Pour plus d’informations, voir [Activer le Mode Exchange mis en cache](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) et [travailler hors connexion dans Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633). 
    
- Outlook propose également un mode hors connexion. Pour l’utiliser, vous devez tout d’abord configurer le mode mis en cache afin que les informations de votre compte sont copiées sur votre ordinateur. En mode hors connexion, Outlook va tenter de se connecter à l’aide de l’envoyer et recevoir des paramètres, ou lorsque vous définir manuellement ce qu’il fonctionne en ligne. Pour plus d’informations, voir [travailler hors connexion pour éviter des frais de connexion de données](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [modifiez envoyer et recevoir des paramètres lorsque vous travaillez hors connexion](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)et [commutateur de travailler hors connexion en ligne](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9). 
    
- Si vous disposez d’un téléphone intelligent, vous pouvez l’utiliser trier votre courrier électronique et le calendrier sur le réseau de l’opérateur mobile de votre téléphone. 
    
> [!NOTE]
> Voici quelques conseils à quel moment utiliser Outlook ou OWA. Si l’espace disque n’est pas un problème sur votre appareil, Outlook dispose d’un ensemble complet de fonctionnalités et peut conviennent le mieux. Si l’espace disque est un problème sur votre appareil, envisagez d’utiliser OWA qui possède un sous-ensemble des fonctionnalités, mais également de mieux dans une situation en ligne. Bien sûr, vous pouvez utiliser soit car ils fonctionnent bien ensemble. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Meilleures pratiques pour utiliser OneDrive entreprise

OneDrive entreprise est conçu dès le départ pour fonctionner avec vos fichiers en ligne et hors connexion. Une fois que vous l’avez configuré, la synchronisation des modifications se produit automatiquement et de manière fiable où et quand vous rendre. Si le réseau est lent, vous pouvez travailler avec la version des fichiers en mode hors connexion.
  
OneDrive pour l’application de synchronisation de gestion est disponible avec Office 2013 (Professionnel Plus ou Standard Edition), ou un abonnement à Office 365 qui inclut des applications Office 2013. Si vous ne disposez pas Office 2013, vous pouvez [Télécharger](https://support.microsoft.com/kb/2903984) l’application de synchronisation Business OneDrive gratuitement. Cette application est également plus rapide que l’utilisation des commandes **Ouvrir dans l’Explorateur** ou **Téléchargez** . Pour plus d’informations, voir [configurer votre ordinateur pour synchroniser vos fichiers OneDrive entreprise dans Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Voici quelques conseils supplémentaires pour l’utilisation de OneDrive pour l’application de synchronisation de gestion :
  
- Si vous synchronisez une grande bibliothèque pour la première fois, démarrez la synchronisation pendant les heures, par exemple, nuit. 
    
- Vous pouvez utiliser la fonctionnalité [d’Arrêter la synchronisation d’une bibliothèque à l’application de gestion OneDrive](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) pour interrompre temporairement la synchronisation des mises à jour. Toutefois, utiliser cette fonctionnalité pendant de courtes périodes, telles que de quelques heures à la fois, pour éviter la mise en attente de grande taille numéros de mises à jour et de réduire le risque de conflits de fusion si plusieurs personnes travaillent sur le même document. 
  
## <a name="best-practices-for-using-onenote"></a>Meilleures pratiques pour l’utilisation de OneNote

Chaque site d’équipe SharePoint a un bloc-notes OneNote intégré et vous pouvez facilement créer vos propres. OneNote est idéal pour recueillir des informations pertinentes que vous avez besoin pour obtenir des tâches effectuées tous les jours. Par exemple, de nombreuses équipes utilisent OneNote en tant que point de regroupement pour les réunions hebdomadaires, notes de projet, des idées, des plans et rapports d’état. Vous pouvez parfaitement organiser ces informations hétérogènes à l’aide des onglets, sections et pages.
  
Mais l’avantage de OneNote est que vous pouvez accéder le contenu à partir de n’importe quel appareil, si un ordinateur de bureau, un ordinateur portable, une tablette ou un téléphone intelligent. Et n’avez pas à se soucier de l’enregistrement ou la synchronisation car OneNote le fait pour vous. 
  
Pour plus d’informations, voir [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/).
  
## <a name="best-practices-for-using-lync-online"></a>Meilleures pratiques pour l’utilisation de Lync Online

Conseils pour l’utilisation de Lync Online lorsque votre réseau est lent sont les suivantes :
  
- Utiliser la messagerie instantanée chaque fois que vous pouvez parce qu’il fonctionne correctement sur un réseau lent.
    
- Éviter d’effectuer des appels téléphoniques via un réseau privé virtuel (VPN) ou les connexions d’accès distant service (RAS).
    
- Assurez-vous que votre périphérique audio est approuvé. Pour plus d’informations, voir [téléphones et appareils qualifiés pour Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944).
    
-  Lorsque vous utilisez PowerPoint dans une présentation en ligne, réduire la taille et la complexité des diapositives. Pour plus d’informations, voir [conseils pour améliorer les performances de votre présentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).
    
- La mesure du possible, partager un moniteur, au lieu d’un programme ou un bureau. Pour plus d’informations, voir [partager votre bureau ou un programme dans Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842).
    
- Envoyer les diapositives PowerPoint à l’avance en demande de réunion au lieu de partager, demander la pièce jointe afin que les participants afficher les diapositives sur leur appareil client. Pour plus d’informations, voir [configurer une réunion Lync](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d).
    
-  Performances vidéo sont très dépendant de performances du réseau. Évitez d’utiliser la vidéo si votre réseau est lent. 
    
Pour plus d’informations, consultez [qualité audio ou vidéo dans Lync Online](https://support.microsoft.com/kb/2386655) et [lente écran Mettre à jour dans Lync 2013](https://support.microsoft.com/kb/2958375).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Meilleures pratiques pour l’utilisation de listes SharePoint

Utilisation de données de liste en mode hors connexion « nettoyage », d’analyser ou de données est idéal pour limiter l’impact d’un réseau lent. Vous pouvez lire et écrire la plupart des listes à partir de Microsoft Access 2013 par une liaison leur. Vous pouvez également exporter une liste à un tableau Excel, qui crée une connexion de données à sens unique entre le tableau Excel et la liste.
  
En outre, si la fonctionnalité d’Access Services est activée, vous pouvez travailler avec beaucoup plus de données que le seuil d’affichage de liste, jusqu'à 50 000 éléments par défaut. Access 2013 and Excel 2013 traitent automatiquement les données de la liste de lots de petite taille et puis remontez les données, qui permet de travailler avec davantage de données est supérieur au seuil d’affichage de liste et sans impact négatif sur les performances du service de autres utilisateurs. 
  
Pour plus d’informations, voir la section « informations supplémentaires sur la gestion des grandes listes » dans [Gérer les grandes listes et bibliothèques dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Meilleures pratiques pour la personnalisation de pages web

Lorsque vous personnalisez une page web, vous pouvez par inadvertance provoquer une dégradation des performances avec la page. Plusieurs facteurs peuvent avoir un impact, tels que la complexité et la taille de la page, combien les composants WebPart sont ajoutés, le nombre d’éléments liste ou une bibliothèque est affiché à l’origine et la façon dont vous la page de codes.
  
Pour plus d’informations, voir [performance régler SharePoint Online](https://technet.microsoft.com/library/f97c2f06-0426-443d-8a16-d98abb0da252#TuneSharePoint).
  
## <a name="best-practices-for-using-project-online"></a>Meilleures pratiques pour l’utilisation de Project Online

Les instructions suivantes peuvent aider à améliorer les performances réseau.
  
- Project Online et SharePoint Online nécessitent la synchronisation, ce qui peut prendre beaucoup de temps. Si vos équipes de projet ont des faible chiffre d’affaires, désactivez la synchronisation de sites de projet pour améliorer les performances des Pages de détails de projet et de publier le projet. Limite de synchronisation Active Directory aux groupes de ressources qui doivent utiliser le système et surveiller les éventuels problèmes d’autorisation après la synchronisation des groupes de grande taille. 
    
- Si votre organisation utilise des sites de projet, les créer à la demande plutôt qu’automatiquement. Cela permet d’accélérer la première expérience de publication et évite la création de contenu et les sites inutiles.
    
- Pages de détails de projet (PDP) peut déclencher le recalcul de la totalité du projet et lancer des actions de flux de travail, qui peuvent être opérations gourmandes en performances. Pour éviter le déclenchement de deux processus de mise à jour en même temps sur le même PDP, évitez de mettre à jour les champs de calendrier (date de début, date de fin, date d’état et date du jour) et les champs non planifiées (nom du projet, description et le propriétaire). 
    
- Réduire le nombre de composants WebPart et des champs personnalisés affichés sur chaque PDP. Créez un PDP dédié avec les seuls champs qui nécessitent la mise à jour pour améliorer la charge et de gagner du temps. 
    
- Lorsque vous utilisez OData pour les rapports, limite la quantité de données que vous lors de l’exécution des requêtes à l’aide de filtrage côté serveur.
    
Pour plus d’informations, voir [performance paramétrer Project Online](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>Quelle est la meilleure façon pour signaler les problèmes ?

Microsoft continuellement améliore les performances globales d’Office 365 en surveillant le réseau, à mesure de la bande passante et latence, amélioration de la page charge temps, réduction des e/s disque, redéfinir des pages pour utiliser la stratégie télécharger Minimal, ajout de matériel pour les centres de données et Ajout de plusieurs centres de données. Pour plus d’informations sur les problèmes de création de rapports et de vérification de l’état actuel, voir [Afficher le statut de vos services](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx).
  
## <a name="see-also"></a>Voir aussi

[Planification réseau et optimisation des performances pour Office 365](network-planning-and-performance.md)
  
[Cours Microsoft Virtual Academy : gestion des performances Office 365](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

