---
title: Déplacement de données essentielles vers les nouvelles régions de centres de données Office 365
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: 'Nouveau centre de données géographiques ajouter de la capacité et les ressources pour prendre en charge de la demande et l’utilisation de croissance de nos clients en cours de calcul. En outre, les nouveau géographiques datacenter offrent délégation de données dans localisés de données principale du client. Données du client principal sont un terme qui fait référence à un sous-ensemble de données de clients définis dans les termes du contrat de Microsoft Online Services : contenu de boîte aux lettres Exchange Online (corps du message électronique, des entrées de calendrier et le contenu des pièces jointes) et SharePoint Online site contenu et les fichiers stockés dans ce site, et les fichiers téléchargés vers OneDrive entreprise.'
ms.openlocfilehash: 362cb257f2098c1acaf08541f34278ed9b4987d2
ms.sourcegitcommit: 75ad9af1fa8adc73611fc6140546222b001861d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "23839582"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Déplacement de données essentielles vers les nouvelles régions de centres de données Office 365

Nous continuer ouvrir le nouveau centre de données géographiques pour Office 365 pour les services. Ces nouvelles géographiques datacenter ajouter de la capacité et ressources pour prendre en charge de la demande et l’utilisation de croissance de nos clients en cours de calcul. En outre, les nouveau géographiques datacenter offrent délégation de données dans localisés de données principale du client. 

Données du client principal sont un terme qui fait référence à un sous-ensemble des données du client définies dans les [Termes du contrat de Services en ligne Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Contenu de boîte aux lettres Exchange Online (corps du message électronique, des entrées de calendrier et le contenu des pièces jointes)
- Contenu du site SharePoint Online et les fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive entreprise 
  
Les clients existants dont les données client essentielles sont stockées dans une région de centre de données existante ne sont pas concernés par le lancement de la nouvelle région de centre de données. Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données. En tant que client de l'une de ces deux régions, vous bénéficierez de la même qualité de service, ainsi que des mêmes performances et contrôles de sécurité qu'auparavant. Les clients existants qui ont des exigences strictes en matière de résidence de données et qui figurent dans la liste ci-dessous ont la possibilité de déplacer leurs données client essentielles vers la nouvelle région.
  
|****Clients avec une adresse de facturation dans****|****Précédente région de centre de données****|****Nouvelle région de centre de données****|****Région disponible depuis****|
|:-----|:-----|:-----|:-----|
|****Japon****| Asie/Pacifique | Japon | Décembre 2014 |
|****Australie, Nouvelle-Zélande, Fidji****| Asie/Pacifique | Australie | Mars 2015 |
|****Inde****| Asie/Pacifique | Inde | Octobre 2015 |
|****Canada****| Amérique du Nord | Canada | Mai 2016 |
|****Royaume-Uni****| Europe | Royaume-Uni | Septembre 2016 |
|****Corée du Sud****| Asie/Pacifique | Corée du Sud | Avril 2017 |
|****France****| Europe | France | Mars 2018 |
   
> [!NOTE]
> L’option de résidence des données et la disponibilité en matière de déplacement des données client vers la nouvelle région ne correspondent pas à une valeur par défaut pour chaque région créée. À l’avenir, lorsque nous ajouterons de nouvelles régions, nous évaluerons la disponibilité et les conditions de déplacement de données région par région. 
  
Les données client essentielles des nouveaux clients ou des clients Office 365 créés après la mise à disposition de la nouvelle région de centre de données seront automatiquement stockées au repos dans cette nouvelle région.
  
La liste complète de l'ensemble des régions de centre de données, des centres de données et l'emplacement des données client au repos est disponible via les [cartes interactives de centre de données](https://aka.ms/dcmaps). 
  
## <a name="data-residency-option"></a>Option de résidence des données

Nous fournissons une option de résidence des données aux clients Office 365 existants qui font partie des régions de centre de données répertoriées dans le tableau ci-dessus. Grâce à cette option, les clients qui ont des exigences en matière de résidence de données peuvent demander à ce que leurs données client essentielles soient déplacées vers la nouvelle région. Nous recommandons à nos clients de ne prendre aucune mesure, sauf si leur organisation a besoin que les données client essentielles soient stockées au repos dans leur nouvelle région de centre de données respective. S'ils choisissent de déplacer leurs données, les clients limitent les possibilités de Microsoft quant à l'optimisation de l'emplacement des données client essentielles au repos dans la région de centre de données actuelle ou dans la nouvelle. En tant que client de l'une de ces deux régions, vous bénéficierez de la même qualité de service, ainsi que des mêmes performances et contrôles de sécurité qu'auparavant.
  
Pour les clients qui ont besoin de déplacer leurs données essentielles vers la nouvelle région :
  
- Ils devront demander le déplacement de leurs données pendant la période d'inscription définie. Consultez l'article [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir plus de détails concernant la fenêtre d'inscription pour votre région et les étapes à suivre pour s'inscrire au programme. 
    
- Les déplacements de données peuvent prendre jusqu'à 24 mois à compter de la fin de la période de demande.
    
- Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données.
    
- La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé. 
    
- Les déplacements de données sont des opérations de service principales qui ont une incidence minime sur les utilisateurs finals. Les fonctionnalités pouvant être concernées sont répertoriées à la page [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) concernant la disponibilité. Ainsi, les clients n'ont rien à préparer ou à surveiller pendant le déplacement. Si besoin, le client est averti de toute maintenance de service. 
    
## <a name="related-topics"></a>Voir aussi 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/en-us/regions/)
  

