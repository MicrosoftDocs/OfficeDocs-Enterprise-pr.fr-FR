---
title: Déplacement de données essentielles vers les nouvelles régions de centres de données Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: "Nouveau centre de régions centres ajouter de la capacité et des ressources de calcul pour prendre en charge notre demande de client et sa croissance d’utilisation en cours. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles. Le terme « données client essentielles » fait référence à un sous-ensemble de données client définies dans les conditions d'utilisation de Microsoft Online Services : Exchange Onlinecontenu de la boîte aux lettres (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes), SharePoint Onlinecontenu du site et fichiers stockés dans ce site, ainsi que fichiers téléchargés vers OneDrive Entreprise."
ms.openlocfilehash: 0efe43b61351d89452abb9a114b37f8df9d79ec2
ms.sourcegitcommit: 160a2564c90a4d64d19f072e0de9fe1b3cd0c917
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "42417049"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Déplacement de données essentielles vers les nouvelles régions de centres de données Office 365

Nous continuons à ouvrir de nouvelles régions de centres de données pour les services Office 365 pour les entreprises. Ces nouvelles régions de centre de données permettent d'accroître la capacité et le nombre de ressources de calcul pour prendre en charge la demande continue des clients et l'augmentation de l'utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles. 

Les données client principales sont un terme qui fait référence à un sous-ensemble de données client, notamment : 
- Contenu de boîte aux lettres Exchange Online (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes)
- Contenu de site SharePoint Online et fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive entreprise
- Messages de conversation Teams, y compris les messages privés, les messages de canal et les images utilisées dans les conversations
  
Les clients existants dont les données client essentielles sont stockées dans une région de centre de données existante ne sont pas concernés par le lancement de la nouvelle région de centre de données. Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données. En tant que client de l'une de ces deux régions, vous bénéficierez de la même qualité de service, ainsi que des mêmes performances et contrôles de sécurité qu'auparavant. Nous proposons aux clients existants figurant dans le tableau ci-dessous une option permettant de demander une migration précoce des données client principales de leur organisation au repos sur leur nouvelle région de centre de données.
  
|**Clients avec pays d’abonnement client dans**|**Précédente région de centre de données**|**Nouvelle région de centre de**|**Région disponible depuis**|
|:-----|:-----|:-----|:-----|
|**Japon**| Asie/Pacifique | Japon | Décembre 2014 |
|**Australie, Nouvelle-Zélande, Fidji**| Asie/Pacifique | Australie | Mars 2015 |
|**Inde**| Asie/Pacifique | Inde | Octobre 2015 |
|**Canada**| Amérique du Nord | Canada | Mai 2016 |
|**Royaume-Uni**| Europe | Royaume-Uni | Septembre 2016 |
|**Corée du Sud**| Asie/Pacifique | Corée du Sud | Avril 2017 |
|**France**| Europe | France | Mars 2018 |
|**Émirats arabes unis**| Europe | Émirats arabes unis | Juin 2019 |
|**Afrique du Sud**| Europe | Afrique du Sud | Juillet 2019 |
|**Suisse, Liechtenstein**| Europe | Suisse | Décembre 2019 |
|**Allemagne**| Europe | Allemagne | Décembre 2019 |
  
Les données client essentielles des nouveaux clients ou des clients Office 365 créés après la mise à disposition de la nouvelle région de centre de données seront automatiquement stockées au repos dans cette nouvelle région.


>[!Note]
>Nous avons lancé la région de centre de l’Allemagne en décembre 2019. Les nouveaux clients Office 365 disposant d’une adresse d’abonnement allemande associée à leur client auront leurs données client principales stockées sur REST en Allemagne. Nous prévoyons de proposer une migration de l’Europe vers l’Allemagne pour les clients allemands à l’avenir. Aujourd’hui, les clients Microsoft Cloud Germany/Deutschland peuvent demander une migration vers les services Office 365 dans les nouvelles régions de centre de connaissances allemand. Pour plus d’informations, reportez-vous à la rubrique [Comment choisir de migrer de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans les nouvelles régions de centre](https://aka.ms/office365germanymoveoptin) de données allemand.
>
  
La liste complète de l'ensemble des régions de centre de données, des centres de données et l'emplacement des données client au repos est disponible via les [cartes interactives de centre de données](https://office.com/datamaps). 
  
## <a name="data-residency-option"></a>Option de résidence des données

Nous fournissons une option de résidence des données aux clients Office 365 existants qui font partie des régions de centre de données répertoriées dans le tableau ci-dessus. Avec cette option, les clients ayant des exigences en matière de résidence des données peuvent demander la migration précoce des données client principales de leur organisation au repos sur leur nouvelle région de centre de données.  Microsoft fournira une date d’échéance pour tous les clients éligibles qui demandent une migration précoce lors de la fenêtre d’enregistrement.  Consultez l'article [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir plus de détails concernant la fenêtre d'inscription pour votre région et les étapes à suivre pour s'inscrire au programme.  Les déplacements de données peuvent prendre jusqu'à 24 mois à compter de la fin de la période de demande.

Le fait de ne pas faire en sorte que Microsoft puisse déplacer vos données client principales au repos sur votre nouveau Geo de centre de données dans le temps dans le cadre de la gestion et de l’optimisation des services.Vos données client principales peuvent uniquement être déplacées vers votre nouvelle région de centre de données, pas vers une autre région géographique.Nous avertirons les administrateurs du client via le centre de messages lorsque ce déplacement de gestion de service est terminé et à mettre à jour l’emplacement des données dans le centre d’administration.
   
Aucune fonction, fonctionnalité ou certification de conformité unique n'est fournie avec la nouvelle région de centre de données.
    
La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé. 
    
Les déplacements de données sont des opérations de service principales qui ont une incidence minime sur les utilisateurs finals. Les fonctionnalités pouvant être concernées sont répertoriées à la page [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [contrat de niveau de service Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) concernant la disponibilité. Ainsi, les clients n'ont rien à préparer ou à surveiller pendant le déplacement. Si besoin, le client est averti de toute maintenance de service. 

Les données sont déplacées vers la nouvelle région de centre de données.
    
## <a name="related-topics"></a>Voir aussi 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
